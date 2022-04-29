FROM ubuntu:20.04
MAINTAINER nomura <i.sysnomura@gmail.com>

# for timezone 
ENV DEBIAN_FRONTEND=noninteractive

#install ros
RUN apt update

#install utilities
RUN apt install -y sudo \
    cmake \
    git \
    wget \
    nano \
    libzmq3-dev \
    python3-pip \
    tmux

#install python lib
RUN pip3 install pyzmq

# add sudo user
RUN groupadd -g 1000 developer && \
    useradd  -g      developer -G sudo -m -s /bin/bash nomura && \
    echo 'nomura:robo2006' | chpasswd

RUN echo 'Defaults visiblepw'             >> /etc/sudoers
RUN echo 'nomura ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

USER nomura

#displey(x11) setup
RUN echo "export DISPLAY=\"host.docker.internal:0.0\""  >> ~/.bashrc
