---
layout: posts
title: "CAFFE - Framework for Deep Learning"
date: '2018-04-09 14:18:00'

---

CAFFE is a fast open source Deep Learning Framework created by UC Berkeley keeping in mind the easy application and innovation in the field of Deep Learning. 

It is a C++ based framework with a python frontend. It supports various Deep Learning architectures like CNN, RNN, LSTM, etc. 

## Installation Steps :

### Pre-requisites before installation
* CUDA (if you want a GPU support for training the models)
* OpenCV
* BLAS (Basic Linear Algebra Subprograms) - operations like matrix multiplication, matrix addition, both implementation for CPU(cBLAS) and GPU(cuBLAS). Provided by MKL(INTEL), ATLAS, openBLAS, etc. 
* Python/pip - 3.5/2.7 both are compatible
* Glogs/gflags - provide logging and command line utilities which can be useful for debugging
* leveldb, lmdb - for image database (these are the database io for your program)
* protobuf - a way to define data structure (all files in caffe taht define the model structure are written in protobuf)
* cuDNN - for GPU acceleration. The version of cuDNN should be chosen according to the compatibility with CUDA.

### Installing the above packages (UBUNTU)
1. `sudo apt-get install vim-gnome`  This installs gvim text editor (if not already present in your system). This can be replaced by any text editor of your choice.
2. `sudo apt-get install libprotobuf-dev libleveldb-dev libsnappy-dev libopencv-dev libhdf5-serial-dev protobuf-compiler`  Installs various dependency packages
3. `sudo apt-get install --no-install-recommends libboost-all-dev`
4. `sudo apt-get install libatlas-base-dev `
5. `sudo apt-get install libgflags-dev libgoogle-glog-dev liblmdb-dev`
6. Install pip (For Python 2.7 or 3.5)  `sudo apt-get install python-pip`  or, Python 3.5 development files
`sudo apt-get install -y python3-dev`
7. Install numpy and scipy libraries
`sudo apt-get install -y python3-numpy python3-scipy`
8. For caffe compilation, follow these steps :
   - `git clone https://github.com/BVLC/caffe` 
   download the github repository 
   - `cd </cloned repository/python/>` and execute the following:    
      - `for req in $(cat requirements.txt); do pip install $req; done`
      - You can modify the `requirements.txt` file as per your extra requirements
    - `cd <cloned-repository> `
    - `cp Makefile.config.example Makefile.config`
      - if only CPU is to be used - Uncomment CPU_ONLY 
      - change CUDA directory to /usr/bin/cuda-8.0 for UBUNTU 16.04 (this only points to the current CUDA version to be used)
      - change Python directory according to 3.5 if you want to use Python 3
      - Add/modify these lines :
         ```
         +INCLUDE_DIRS := $(PYTHON_INCLUDE) /usr/local/include /usr/include/hdf5/serial/
         +LIBRARY_DIRS := $(PYTHON_LIB) /usr/local/lib /usr/lib /usr/lib/x86_64-linux-gnu/hdf5/serial/
         ```
    - For Compilation, run the following set of commands:    
      ```
      make clean    
      make all     
      make test  
      make runtest
      ```
    - To run on multiple GPU's, compile with `USE_NCCL = 1` (in Makefile.config).
      For this, install the NCCL git repository.
       1. `git clone http://github.com/NVIDIA/nccl.git`
       2. `cd nccl`
       3. `sudo make install –j4`
       4. `sudo ldconfig`
       5. Compile

### Some points to be noted
1. CAFFE needs GCC and G++ version to be more than 5 or 5.2. Doesn’t compile with 4.8 version. 
To update the GCC version in case needed : https://askubuntu.com/questions/26498/choose-gcc-and-g-version
