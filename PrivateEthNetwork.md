1. Preparation:

 # git clone https://github.com/ethereum/go-ethereum.git
 # cd  go-ethereum
 # git checkout v1.7.2
 # sudo apt-get install -y build-essential
 # sudo -E add-apt-repository ppa:gophers/archive
 # sudo apt-get update
 # sudo apt-get install golang-1.7
 Add 
   export GOROOT=/usr/lib/go-1.7
   export PATH=$GOROOT/bin:$PATH
 to ./bashrc
 # source ~/.bashrc
 # make geth
 # make all

 Add geth binary path for example
   export PATH=/home/upsquared/go-ethereum/build/bin:$PATH
 to ./bashrc
 # source ~/.bashrc

2.
# mkdir node1 node2 node3 node4
# geth --datadir node1/ account new
  Address: {9be7181ec8625a10d85be1b71297c311502ce0e5}
# geth --datadir node2/ account new
  Address: {9bf98906b2817876f02a738b9d8da55bd24aaf5c}
# geth --datadir node3/ account new
  Address: {e388a32676bd0cdd72b17751a9fa905ebc96e04b}
# geth --datadir node4/ account new
  Address: {32f74737e3b333b9733f00cc030db1cd4cea9db4}
# echo '9be7181ec8625a10d85be1b71297c311502ce0e5' >> accounts.txt
# echo '9bf98906b2817876f02a738b9d8da55bd24aaf5c' >> accounts.txt
# echo 'e388a32676bd0cdd72b17751a9fa905ebc96e04b' >> accounts.txt
# echo '32f74737e3b333b9733f00cc030db1cd4cea9db4' >> accounts.txt
# echo 'intel123' > node1/password.txt
# echo 'intel123' > node2/password.txt
# echo 'intel123' > node3/password.txt
# echo 'intel123' > node4/password.txt
# puppeth
Please specify a network name to administer (no spaces, please)
> devnet
What would you like to do? (default = stats)
 1. Show network stats
 2. Configure new genesis
 3. Track new remote server
 4. Deploy network components
> 2

Which consensus engine to use? (default = clique)
 1. Ethash - proof-of-work
 2. Clique - proof-of-authority
> 2

How many seconds should blocks take? (default = 15)
> 5 // for example

Which accounts are allowed to seal? (mandatory at least one)
> 0x9be7181ec8625a10d85be1b71297c311502ce0e5 //First three nodes are sealers
> 0x9bf98906b2817876f02a738b9d8da55bd24aaf5c
> 0xe388a32676bd0cdd72b17751a9fa905ebc96e04b

Which accounts should be pre-funded? (advisable at least one)
> 0x9be7181ec8625a10d85be1b71297c311502ce0e5 // All pre-defined accounts with fund !
> 0x9bf98906b2817876f02a738b9d8da55bd24aaf5c
> 0xe388a32676bd0cdd72b17751a9fa905ebc96e04b
> 0x32f74737e3b333b9733f00cc030db1cd4cea9db4

Specify your chain/network ID if you want an explicit one (default = random)
> 1515 // for example. Do not use anything from 1 to 10

Anything fun to embed into the genesis block? (max 32 bytes)
>

What would you like to do? (default = stats)
 1. Show network stats
 2. Manage existing genesis
 3. Track new remote server
 4. Deploy network components
> 2

1. Modify existing fork rules
 2. Export genesis configuration
> 2

Which file to save the genesis into? (default = devnet.json)
> genesis.json
INFO [01-23|15:16:17] Exported existing genesis block

What would you like to do? (default = stats)
 1. Show network stats
 2. Manage existing genesis
 3. Track new remote server
 4. Deploy network components
> ^C // ctrl+C to quit puppeth

Update the genesis.json
 - Cleane the empty addresses that puppeth includes when creating the file
 - Change the gasLimit


# geth --datadir node1/ init genesis.json
# geth --datadir node2/ init genesis.json
# geth --datadir node3/ init genesis.json
# geth --datadir node4/ init genesis.json

# bootnode -genkey boot.key
# bootnode -nodekey boot.key -verbosity 9 -addr :30310

# geth --mine -networkid 1515 --datadir node1/ --unlock 0 --password node1/password.txt --syncmode 'full' --port 30311 --rpc --rpccorsdomain "*" --rpcaddr 10.239.67.178 --rpcport 8545 --rpcapi 'personal,db,eth,net,web3,txpool,miner' --bootnodes 'enode://cd9054839921ff2bf736e83e3c4b43eb84fcdab9d57ff4fd9c7cbe6efd1470702396f7a083a590ed9bff2429d5e4a1843541de0d7b54e90f98d72b8133d3e1a7@10.239.67.178:30310' console
# geth --mine -networkid 1515 --datadir node2/ --unlock 0 --password node2/password.txt --syncmode 'full' --port 30312 --rpc --rpccorsdomain "*" --rpcaddr 10.239.67.178 --rpcport 8546 --rpcapi 'personal,db,eth,net,web3,txpool,miner' --bootnodes 'enode://cd9054839921ff2bf736e83e3c4b43eb84fcdab9d57ff4fd9c7cbe6efd1470702396f7a083a590ed9bff2429d5e4a1843541de0d7b54e90f98d72b8133d3e1a7@10.239.67.178:30310' console
# geth --mine -networkid 1515 --datadir node3/ --unlock 0 --password node3/password.txt --syncmode 'full' --port 30313 --rpc --rpccorsdomain "*" --rpcaddr 10.239.67.178 --rpcport 8547 --rpcapi 'personal,db,eth,net,web3,txpool,miner' --bootnodes 'enode://cd9054839921ff2bf736e83e3c4b43eb84fcdab9d57ff4fd9c7cbe6efd1470702396f7a083a590ed9bff2429d5e4a1843541de0d7b54e90f98d72b8133d3e1a7@10.239.67.178:30310' console
# geth --mine -networkid 1515 --datadir node4/ --unlock 0 --password node4/password.txt --syncmode 'full' --port 30314 --rpc --rpccorsdomain "*" --rpcaddr 10.239.67.178 --rpcport 8548 --rpcapi 'personal,db,eth,net,web3,txpool,miner' --bootnodes 'enode://cd9054839921ff2bf736e83e3c4b43eb84fcdab9d57ff4fd9c7cbe6efd1470702396f7a083a590ed9bff2429d5e4a1843541de0d7b54e90f98d72b8133d3e1a7@10.239.67.178:30310' console

# net.peerCount

6. Connect MetaMask Ethereum Wallet
Set the proxy to the chrome browser, https://metamask.io/
Then click the MetaMask on the right top of the browser tool bar

Create MetaMask account
My: sugar game quality theme food tortoise twice surprise popular liquid design matrix
My address: 0xac05BE8800cfb366661cCEEC2400fedD091981bb

Create "New Custom RPC" to http://10.239.67.178:8548

7. Transfer Ether
# geth --datadir node4/ attach ipc:node4/geth.ipc
# personal.unlockAccount(eth.accounts[0],"intel123")
# eth.sendTransaction({from:eth.accounts[0], to:"0xac05BE8800cfb366661cCEEC2400fedD091981bb", value:web3.toWei(1, "ether")})

8. View Account Balance In MetaMask
You should see the eth in the MetaMask

9. Remex Solidity Editor
Open the http://remix.ethereum.org  <== make sure not https

pragma solidity ^0.4.11;
contract Hello  {
      // a string variable
      string public greeting;

    // the function with the same name as the class is a constructor
     function Hello(string _greeting) {
         greeting = _greeting;
     }
 
     // change the greeting message
     function setGreeting(string _greeting) {
         greeting = _greeting;
     }
 
     // get the greeting message
     function greet() constant returns (string _greeting) {
        _greeting = greeting;
     }
 }


Compile
Run -> Environment -> Web3 Provider -> 10.239.67.178:8548 

# geth --datadir node4/ attach ipc:node4/geth.ipc
# personal.unlockAccount(eth.accounts[0],"intel123")

Finally Create the contract from http://remix.ethereum.org

Make sure the file is Hello.sol and matches with contract name in the right window
Now you can set some value to the setGreeting method
and click on it to invoke the smart contract. Once again, 
make sure that you have your account unlocked, because, 
to invoke a smart contract we use ethereum transactions and we need the signature of the initiator. O
nce done with the setGreeting method, you can invoke other methods too.

11.Ethereum Block Explorer
# git clone https://github.com/carsenk/explorer
# npm install
change the localhost to 10.239.67.178 in package.json 
change the localhost to 10.239.67.178 in app/app.js
# npm start

OR
# git clone https://github.com/etherparty/explorer
# npm install
change the localhost to 10.239.67.178 in package.json 
change the localhost to 10.239.67.178 in app/app.js
# npm start

12. Reference
https://webcache.googleusercontent.com/search?q=cache:ofb_VWXtlk4J:https://hackernoon.com/setup-your-own-private-proof-of-authority-ethereum-network-with-geth-9a0a3750cda8+&cd=5&hl=zh-CN&ct=clnk&gl=us
