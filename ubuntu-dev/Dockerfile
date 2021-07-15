FROM ubuntu:bionic

RUN apt-get update && \
  apt-get -y install curl lsb-release sudo

RUN apt-get -y update && apt-get install -y \
  apt-utils \
  build-essential \
  sudo \
  git \
  autoconf \
  libtool \
  vim \
  devscripts \
  libev-dev

RUN cd /tmp && \
  curl -sLO https://golang.org/dl/go1.16.3.linux-amd64.tar.gz && \
  rm -rf /usr/local/go && tar -C /usr/local -xzf go1.16.3.linux-amd64.tar.gz

RUN useradd -m alistair && echo "alistair:alistair" | chpasswd && adduser alistair sudo
RUN sed -i.bkp -e \
      's/%sudo\s\+ALL=(ALL\(:ALL\)\?)\s\+ALL/%sudo ALL=NOPASSWD:ALL/g' \
      /etc/sudoers

COPY bashrc /home/alistair/.bashrc
COPY bash_profile /home/alistair/.bash_profile
COPY gitconfig /home/alistair/.gitconfig
COPY install-deps /home/alistair/bin/install-deps

RUN mkdir /work && chown -R alistair:alistair /work

USER alistair
