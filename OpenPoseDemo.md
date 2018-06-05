
    # git clone https://github.com/CMU-Perceptual-Computing-Lab/openpose.git
    # cd openpose
    # mkdir build
    # cd build
    # cmake -DOpenCV_INCLUDE_DIRS=/home/stli/deeplearning/opencv_3.4/opencv-3.4.0/build/install/include \
      -DOpenCV_LIBS_DIR=/home/stli/deeplearning/opencv_3.4/opencv-3.4.0/build/install/lib \
      -DCaffe_INCLUDE_DIRS=/opt/movidius/caffe/build/install/include \
      -DCaffe_LIBS=/opt/movidius/caffe/build/install/lib/libcaffe.so -DBUILD_CAFFE=OFF ..
    # make -j`nproc`


    # git clone https://github.com/ildoonet/tf-pose-estimation
    # cd tf-openpose/src
    ...
    # python run_webcam.py --model=mobilenet_thin --resolution=432x368 --camera=0

    Refs:
      https://ncsforum.movidius.com/discussion/224/nan-result-error-after-huge-network-was-used
      https://antkillerfarm.github.io/dl/2018/01/30/Deep_Learning_35.html
