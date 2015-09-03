FROM ubuntu:latest
MAINTAINER jorge.luis.bonilla@gmail.com

ENV DEBIAN_FRONTEND noninteractive

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
RUN dataserv-client config --set_payout_address=1NytpEjVPRhJxzdbdxZZGFm5sbiZFgVW3Y

#6 register your node
RUN  dataserv-client --url=http://status.driveshare.org:5000 register

#7 create shards - Change the max_size before running
VOLUME /media/storj:/var/storj
RUN dataserv-client --url=http://status.driveshare.org:5000 --store_path=/var/storj --max_size=1TB build

#8 let the network know you are online
RUN dataserv-client ping
