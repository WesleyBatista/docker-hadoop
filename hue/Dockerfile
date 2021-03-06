# copy from https://github.com/cloudera/hue/blob/891c5e0/tools/docker/hue-base/Dockerfile
FROM ubuntu:trusty
MAINTAINER Wesley Batista "https://github.com/wesleybatista"

RUN apt-get update -y

RUN apt-get install -y software-properties-common
RUN add-apt-repository -y ppa:webupd8team/java
RUN apt-get update -y

RUN echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | sudo /usr/bin/debconf-set-selections
RUN apt-get install -y oracle-java8-installer

RUN apt-get update -y
RUN apt-get install --fix-missing -q -y \
  git \
  ant \
  gcc \
  g++ \
  libkrb5-dev \
  libmysqlclient-dev \
  libssl-dev \
  libsasl2-dev \
  libsasl2-modules-gssapi-mit \
  libsqlite3-dev \
  libtidy-0.99-0 \
  libxml2-dev \
  libxslt-dev \
  libffi-dev \
  make \
  maven \
  libldap2-dev \
  python-dev \
  python-setuptools \
  libgmp3-dev \
  libz-dev

RUN mkdir -p /opt/hue
WORKDIR /opt/hue

RUN git clone https://github.com/cloudera/hue.git ./
RUN git checkout release-3.12.0
RUN make apps

EXPOSE 8888

CMD ["build/env/bin/hue", "runserver_plus", "0.0.0.0:8888"]