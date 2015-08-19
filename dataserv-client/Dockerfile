FROM ubuntu:latest
MAINTAINER jorge.luis.bonilla@gmail.com

ENV DEBIAN_FRONTEND noninteractive

# 1 - Install dataserv-client v1.1.0

RUN apt-get update && \
apt-get install -y python3-pip &&\
pip3 install dataserv-client==1.1.0

RUN apt-get clean &&\
apt-get purge

