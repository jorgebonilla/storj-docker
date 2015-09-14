FROM ubuntu:latest
MAINTAINER jorge.luis.bonilla@gmail.com

ENV DEBIAN_FRONTEND noninteractive
#Modify this line with your SJCX address
ENV SJCX_ADDRESS=1NytpEjVPRhJxzdbdxZZGFm5sbiZFgVW3Y

# 1 - Install dataserv-client v1.1.0

RUN apt-get update && \
apt-get install -y python3-pip &&\
pip3 install dataserv-client

#2 - Clean up

RUN apt-get clean &&\
apt-get purge

#3 - Update Dataserv-client
RUN pip3 install dataserv-client --upgrade #2.1.3

#4 - Create dataserv mountpoint
RUN mkdir /var/storj

#5 Register payout address - Change this address to your own before running
RUN dataserv-client --url=http://switch.driveshare.org config --set_payout_address=$SJCX_ADDRESS
