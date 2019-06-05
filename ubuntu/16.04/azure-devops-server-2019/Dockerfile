FROM ubuntu:16.04
LABEL MAINTAINER="BBT Software AG <devadmin@bbtsoftware.ch>"

# To make it easier for build and release pipelines to run apt-get,
# configure apt to not require confirmation (assume the -y argument by default)
ENV DEBIAN_FRONTEND=noninteractive
RUN echo "APT::Get::Assume-Yes \"true\";" > /etc/apt/apt.conf.d/90assumeyes

RUN mkdir /azp && \
    groupadd -r azp --gid=999 && \
    useradd -r -g azp --uid=999 --home-dir=/azp --shell=/bin/bash azp && \
    chown azp:azp /azp && \
    apt-get update && \
    apt-get install -y --no-install-recommends \
        ca-certificates \
        curl \
        jq \
        git \
        iputils-ping \
        libcurl3 \
        libicu55 \
        libunwind8 \
        netcat \ 
        zip \
        unzip

WORKDIR /azp

COPY docker-entrypoint.sh /usr/local/bin/

ENTRYPOINT ["docker-entrypoint.sh"]

USER azp