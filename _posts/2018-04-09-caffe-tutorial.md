---
layout: posts
title: "CAFFE - Framework for Deep Learning"
date: '2018-04-09 14:18:00'

---


Installation Steps :
(to be followed religiously) 

sudo apt-get install vim-gnome
sudo apt-get install libprotobuf-dev libleveldb-dev libsnappy-dev libopencv-dev libhdf5-serial-dev protobuf-compiler

sudo apt-get install --no-install-recommends libboost-all-dev

sudo apt-get install libatlas-base-dev 

sudo apt-get install libgflags-dev libgoogle-glog-dev liblmdb-dev

sudo apt-get install python-pip
or, Python 3.5 development files
sudo apt-get install -y python3-dev
sudo apt-get install -y python3-numpy python3-scipy
git clone https://github.com/BVLC/caffe
download the github repository
in python directory, execute the following
for req in $(cat requirements.txt); do pip install $req; done
cp Makefile.config.example
if only CPU is to be used - Uncomment CPU_ONLY 
change CUDA directory to /usr/bin/cuda-8.0 for UBUNTU 16.04
change Python directory according to 3.5 if you want to use Python 3
+INCLUDE_DIRS := $(PYTHON_INCLUDE) /usr/local/include /usr/include/hdf5/serial/
+LIBRARY_DIRS := $(PYTHON_LIB) /usr/local/lib /usr/lib /usr/lib/x86_64-linux-gnu/hdf5/serial/

make clean
make all
make test
make runtest
