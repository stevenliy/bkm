1. Install InfluxDB

		# wget https://dl.influxdata.com/influxdb/releases/influxdb_1.5.2_amd64.deb
		# sudo dpkg -i influxdb_1.5.2_amd64.deb
		# sudo service influxdb start

2. Install Telegraf

		# wget https://storage.googleapis.com/golang/go1.8.3.linux-amd64.tar.gz
		# tar -xf go1.8.3.linux-amd64.tar.gz
		# export GOPATH="/home/stli/opt/gopkg" 
		# export GOROOT="/home/stli/opt/go"
		# go get -d github.com/influxdata/telegraf
		# cd $GOPATH/src/github.com/influxdata/telegraf
		# make
		# ./telegraf --help
		# ./telegraf --input-filter amqp_consumer --output-filter influxdb config > telegraf.conf
		# rabbitmqctl add_vhost influxdb
		# sudo rabbitmqctl set_permissions -p influxdb guest ".*" ".*" ".*"
		# ./telegraf --config telegraf.conf --input-filter amqp_consumer --output-filter influxdb

		# sudo rabbitmq-plugins enable rabbitmq_management

		Publish the below message to queue "telegrah" through http://10.239.67.39:15672/
			weather,location=us-midwest temperature=82 1465839830100400200

3. Check data in influx database

		# influx
		> show databases
			name: databases
			name
			----
			_internal
			telegraf
		> use telegraf
			Using database telegraf
		> select * from weather
			The message "weather,location=us-midwest temperature=82 1465839830100400200" will be there

4. Install Chronograf

		# wget https://dl.influxdata.com/chronograf/releases/chronograf_1.4.4.1_amd64.deb
		# sudo dpkg -i chronograf_1.4.4.1_amd64.deb
		http://10.239.67.39:8888

5. Install Kapacitor

		# wget https://dl.influxdata.com/kapacitor/releases/kapacitor_1.4.1_amd64.deb
		# sudo dpkg -i kapacitor_1.4.1_amd64.deb

		Kapacitor has a mirror of the InfluxDB API for writes (hostname:8086/write) .
		In the [[outputs.influxdb]] section of your telegraf.conf set urls = ['http://kapacitor-host:8086']

