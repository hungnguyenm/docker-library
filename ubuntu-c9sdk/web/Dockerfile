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
        tmux \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*

# Change `nodejs` to `node`
RUN update-alternatives --install /usr/bin/node node /usr/bin/nodejs 10

# Install Cloud9 SDK
RUN git clone git://github.com/c9/core.git c9sdk \
 && c9sdk/scripts/install-sdk.sh

ENTRYPOINT node c9sdk/server.js --listen 0.0.0.0 -w /root/workspace/ -a :