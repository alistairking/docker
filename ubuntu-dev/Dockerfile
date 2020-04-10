FROM ubuntu:bionic

RUN apt-get update && \
  apt-get -y install curl lsb-release sudo && \
  curl https://pkg.caida.org/os/ubuntu/bootstrap.sh | bash

RUN apt-get -y update && apt-get install -y \
  apt-utils \
  build-essential \
  sudo \
  git \
  autoconf \
  libtool

RUN useradd -m docker && echo "docker:docker" | chpasswd && adduser docker sudo
RUN sed -i.bkp -e \
      's/%sudo\s\+ALL=(ALL\(:ALL\)\?)\s\+ALL/%sudo ALL=NOPASSWD:ALL/g' \
      /etc/sudoers

USER docker
