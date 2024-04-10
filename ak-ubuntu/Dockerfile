FROM ubuntu:20.04

LABEL maintainer "Appknox <engineering@appknox.com>"

ENV GOSU_VERSION 1.14
ENV LANG en_US.UTF-8

RUN apt-get update -y \
  && DEBIAN_FRONTEND=noninteractive apt-get install --no-install-recommends -y \
    build-essential \
    ca-certificates  \
    gnupg2 \
    dirmngr \
    curl \
    git \
    zip \
    software-properties-common \
    fonts-noto-cjk \
    language-pack-en \
    iputils-ping \
    tmux \
    dnsutils \
    unzip \
  && curl -sL https://deb.nodesource.com/setup_14.x -o nodesource_setup.sh \
  && bash nodesource_setup.sh \
  # && add-apt-repository ppa:nginx/stable -y \
  && curl -s https://www.postgresql.org/media/keys/ACCC4CF8.asc | apt-key add - \
  && sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt/ $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list' \
  && apt-get update -y \
  && gpg --batch --keyserver hkps://keys.openpgp.org --recv-keys B42F6819007F00F88E364FD4036A9C25BF357DD4 \
  && curl -o /usr/local/bin/gosu -SL "https://github.com/tianon/gosu/releases/download/$GOSU_VERSION/gosu-$(dpkg --print-architecture)" \
  && curl -o /usr/local/bin/gosu.asc -SL "https://github.com/tianon/gosu/releases/download/$GOSU_VERSION/gosu-$(dpkg --print-architecture).asc" \
  && gpg --batch --verify /usr/local/bin/gosu.asc /usr/local/bin/gosu \
  && rm /usr/local/bin/gosu.asc \
  && chmod +x /usr/local/bin/gosu \
  && rm -rf /var/lib/apt/lists/*
