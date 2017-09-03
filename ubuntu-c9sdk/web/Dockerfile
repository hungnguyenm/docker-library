FROM ubuntu:xenial

LABEL maintainer="Hung Nguyen<minhhung.ng@gmail.com>"

WORKDIR /root

# Install required packages
RUN apt-get update && apt-get install -y \
	build-essential \
	curl \
	git \
	nodejs \
	python \
	software-properties-common \
	tmux

# Change `nodejs` to `node`
RUN update-alternatives --install /usr/bin/node node /usr/bin/nodejs 10

# Install Oracle Java 8
RUN echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | debconf-set-selections \
 && add-apt-repository -y ppa:webupd8team/java \
 && apt-get update \
 && apt-get install -y oracle-java8-installer \
 && rm -rf /var/lib/apt/lists/* \
 && rm -rf /var/cache/oracle-jdk8-installer

ENV JAVA_HOME /usr/lib/jvm/java-8-oracle

# Install Cloud9 SDK
RUN git clone git://github.com/c9/core.git c9sdk \
 && c9sdk/scripts/install-sdk.sh

ENV USERNAME admin
ENV PASSWORD admin

ENTRYPOINT node c9sdk/server.js --listen 0.0.0.0 --auth $USERNAME:$PASSWORD -w /root/workspace/