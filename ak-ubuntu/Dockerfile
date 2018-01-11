FROM ubuntu:16.04

LABEL maintainer "Appknox <engineering@appknox.com>"

ENV GOSU_VERSION 1.10

RUN apt-get update || apt-get update \
  && DEBIAN_FRONTEND=noninteractive apt-get install -y \
    build-essential \
    curl \
    git \
    software-properties-common \
    python-software-properties \
  && curl -sL https://deb.nodesource.com/setup_9.x -o nodesource_setup.sh \
  && bash nodesource_setup.sh \
  && add-apt-repository ppa:nginx/development -y \
  && add-apt-repository ppa:deadsnakes/ppa \
  && apt-get update \
  && gpg --keyserver ha.pool.sks-keyservers.net --recv-keys B42F6819007F00F88E364FD4036A9C25BF357DD4 \
  && curl -o /usr/local/bin/gosu -SL "https://github.com/tianon/gosu/releases/download/$GOSU_VERSION/gosu-$(dpkg --print-architecture)" \
  && curl -o /usr/local/bin/gosu.asc -SL "https://github.com/tianon/gosu/releases/download/$GOSU_VERSION/gosu-$(dpkg --print-architecture).asc" \
  && gpg --verify /usr/local/bin/gosu.asc \
  && rm /usr/local/bin/gosu.asc \
  && chmod +x /usr/local/bin/gosu