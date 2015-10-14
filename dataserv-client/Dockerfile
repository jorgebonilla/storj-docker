FROM ubuntu:latest
MAINTAINER jorge.luis.bonilla@gmail.com

ENV DEBIAN_FRONTEND noninteractive
#Modify this line with your SJCX address
ENV SJCX_ADDRESS=1NytpEjVPRhJxzdbdxZZGFm5sbiZFgVW3Y

# 1 - Install dataserv-client v1.1.0
RUN apt-get update && \
apt-get install -y python-pip python-dev &&\
pip install dataserv-client

#2 - Amazon s3fs
RUN apt-get install -y build-essential git libfuse-dev libcurl4-openssl-dev libxml2-dev mime-support automake libtool pkg-config libssl-dev
RUN git clone https://github.com/s3fs-fuse/s3fs-fuse
RUN cd s3fs-fuse/ && ./autogen.sh && ./configure --prefix=/usr --with-openssl && make && make install
RUN echo "AKIAJQMK6DDJGLE6WSUQ:vPciLW6zmRmuJB+U8/2Z2IrO72cjt28oQ6/iJAJR" > ~/.passwd-s3fs
RUN mkdir /tmp/cache && chmod 777 /tmp/cache
RUN mkdir /var/storj && s3fs -o use_cache=/tmp/cache storj.jorgebonilla /var/storj

#3 - Clean up
RUN apt-get clean &&\
apt-get purge

#5 Register payout address - Change this address to your own before running
RUN dataserv-client --url=http://switch.driveshare.org config --set_payout_address=$SJCX_ADDRESS

CMD dataserv-client --store_path=/var/storj --max_size=100MB farm
