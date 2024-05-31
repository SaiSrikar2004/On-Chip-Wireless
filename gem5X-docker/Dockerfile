FROM ubuntu:20.04
SHELL ["/bin/bash" , "-c" ]
ENV DEBIAN_FRONTEND noninteractive
RUN echo "deb http://us.archive.ubuntu.com/ubuntu/ xenial main" \
>> /etc/apt/sources.list \
&& echo \
" deb http://us.archive.ubuntu.com/ubuntu/ xenial universe" \
>> /etc/apt/sources.list \
&& apt update -y\
&& apt install wget -y
RUN mkdir /opt/miniconda3
RUN  wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O /opt/miniconda3/miniconda.sh
RUN bash /opt/miniconda3/miniconda.sh -b -u -p /opt/miniconda3
COPY linux-64_scons-3.0.0-py27_0.tar.bz2 /opt
RUN source /opt/miniconda3/bin/activate\
&& conda config --set restore_free_channel true \
&& conda init \ 
&& conda create --name py275 -c free python=2.7.5 -y\
&& conda activate py275 \
&& conda install /opt/linux-64_scons-3.0.0-py27_0.tar.bz2 -y


RUN apt-get -y install build-essential gcc-arm-linux-gnueabihf \
RUN apt-get install gcc-aarch64-linux-gnu \
device-tree-compiler make git m4 zlib1g \
zlib1g-dev libprotobuf-dev protobuf-compiler libprotoc-dev \
libgoogle-perftools-dev python-dev  libboost-all-dev \
RUN apt-get install diod -y
RUN apt-get install qemu qemu-user qemu-system qemu-user-static -y
COPY swig-3.0.8.tar.gz /opt
RUN tar -xzf /opt/swig-3.0.8.tar.gz  
RUN cd /swig-3.0.8 && ./configure --without-pcre && make && make install
