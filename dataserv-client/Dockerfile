FROM ubuntu:latest
MAINTAINER jorge.luis.bonilla@gmail.com

ENV DEBIAN_FRONTEND noninteractive
#Modify this line with your SJCX address
ENV SJCX_ADDRESS=<ENTER_YOUR_SJCX_ADDRESS>

# 1 - Install dataserv-client v1.1.0

RUN apt-get update && \
apt-get install -y python3-pip &&\
pip3 install dataserv-client==1.1.0

#2 - Clean up

RUN apt-get clean &&\
apt-get purge

#3 - Update Dataserv-client
RUN pip3 install dataserv-client --upgrade #2.0.3

#4 - Create dataserv mountpoint
RUN mkdir /var/storj

#5 Register payout address - Change this address to your own before running
RUN dataserv-client config --set_payout_address=$SJCX_ADDRESS

#6 register your node
RUN  dataserv-client --url=http://status.driveshare.org:5000 register

