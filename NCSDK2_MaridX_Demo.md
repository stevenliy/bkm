
    # git clone https://github.com/BVLC/caffe.git
    !!! if you want to run ssd net need install this one https://github.com/weiliu89/caffe/tree/ssd as well
    # cd caffe/
    # git checkout 1.0
    # sudo apt-get install libprotobuf-dev libleveldb-dev libsnappy-dev libopencv-dev libhdf5-serial-dev protobuf-compiler
    # sudo apt-get install --no-install-recommends libboost-all-dev
    # cp Makefile.config.example Makefile.config.example
    # sudo apt-get install libgoogle-glog-dev
    # sudo apt-get install libopenblas-dev
    # sudo apt-get install liblmdb-dev
    # sudo apt-get libhdf5-serial-dev
    # sudo apt-get install libhdf5-serial-dev
    # sudo apt install libatlas-base-dev
    # vim Makefile.config
       CPU_ONLY := 1
       USE_OPENCV := 0
       INCLUDE_DIRS := $(PYTHON_INCLUDE) /usr/local/include /usr/include/hdf5/serial
       LIBRARY_DIRS := $(PYTHON_LIB) /usr/local/lib /usr/lib /usr/lib/x86_64-linux-gnu/hdf5/serial

    USE python3, change the Makefile.config more
       PYTHON_LIBRARIES := boost_python-py35 python3.5m
       PYTHON_INCLUDE := /usr/include/python3.5m \
                     /usr/lib/python3.5/dist-packages/numpy/core/include
				 
    # cd /usr/lib64/
      Check libdrm.so* is there
    # cd -
    # make all
    # make pycaffe
    # sudo apt-get install python3-pip
    # pip3 install numpy
    # pip3 install networkx
    
    Install OpenCV version 3.4.1.
    # git clone https://github.com/opencv/opencv_contrib.git
    # cd opencv_contrib
    # git checkout ced5aa760688dd2ec867ebf7bd4f0c2341d2fde5
    # cd ../
    # git clone https://github.com/opencv/opencv.git
    # cd opencv
    # git checkout 2fb4812f6dfb9eac536c4975af18eb94da003366
    # mkdir build && cd build
    # cmake -DWITH_VA_INTEL=ON -DWITH_OPENGL=ON -DINSTALL_PYTHON_EXAMPLES=ON -DBUILD_NEW_PYTHON_SUPPORT=ON -DOPENCV_EXTRA_MODULES_PATH=../../opencv_contrib/modules -DWITH_CUDA=OFF ..
    # make -j10
    # sudo make install

    # git clone https://github.com/movidius/ncsdk.git -b ncsdk2
    # cd ncsdk
    # git checkout 00120fd0febd3ed514721284c71a6e6d0e20cbd7
    # pip3 install -r requirements.txt

    # git clone https://github.com/movidius/ncappzoo.git -b ncsdk2
    # git checkout 00120fd0febd3ed514721284c71a6e6d0e20cbd7
    # sudo apt-get install graphviz
    # sudo apt-get install graphviz-dev
    # sudo apt-get install python3-tk
    # cd apps
    Execute the samples
