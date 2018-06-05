  I'm using ASUS DUAL-GTX1060-O6G card, here is the step to install CUDA8.0.
  
    # sudo apt-get install cuda
    # sudo apt-get remove nvidia-384
    # sudo apt-get install nvidia-375 nvidia-modprobe

    It's important to download the "runfile (local)" file
    Refs:
      https://developer.nvidia.com/cuda-80-download-archive
      https://devtalk.nvidia.com/default/topic/992023/install-cuda-on-debian/
      http://developer.download.nvidia.com/compute/cuda/8.0/secure/prod/docs/sidebar/CUDA_Installation_Guide_Linux.pdf?myGRzqRKRbnPn0LR3z8RElP0bmD6IkEM__jepil4PGJs6P5kosr3GWVm-GekH2ULD9_TucDbBOHTVBr7xIQFi8X4vvLtdU_no4cn6b5Cn1JKga-19olq_3toLyiqQNJVJ5cCFI2NDFUs0VDohLJyn8_tBW9DvHJhd_MsL9DCrRn0qVztD8oaTUM2
   
    # sudo service lightdm stop
    # sudo sh cuda_8.0.44_linux-run
    # sudo ./cuda_8.0.44_linux.run 
    Please make sure that
      -   PATH includes /usr/local/cuda-8.0/bin
      -   LD_LIBRARY_PATH includes /usr/local/cuda-8.0/lib64,
 
    # reboot

    Then install CUDNN.80 since I need use the card as deeplearning training card.
    # https://developer.nvidia.com/rdp/assets/cudnn_install-txt-5prod-8
    # wget -c wget http://developer.download.nvidia.com/compute/redist/cudnn/v6.0/cudnn-8.0-linux-x64-v6.0.tgz
    # tar -xzvf cudnn-8.0-linux-x64-v5.1.tgz
    # sudo cp cuda/include/cudnn.h /usr/local/cuda/include
    # sudo cp cuda/lib64/libcudnn* /usr/local/cuda/lib64
    # sudo chmod a+r /usr/local/cuda/include/cudnn.h /usr/local/cuda/lib64/libcudnn*
    # cd /usr/lib/x86_64-linux-gnu/
    # sudo ln -s libcuda.so.1 libcuda.so
    # sudo ldconfig

    Solve the conflict beteen Intel Graphic Card and Nvidia Card. 
    Refs:
      https://devtalk.nvidia.com/default/topic/991849/-solved-run-cuda-on-dedicated-nvidia-gpu-while-connecting-monitors-to-intel-hd-graphics-is-this-possible-

    Install ENV
    Refs:
      https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/001432712108300322c61f256c74803b43bfd65c6f8d0d0000
    # source venv/bin/activate
