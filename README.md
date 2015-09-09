# storj-docker
Storj Dataserv Client

Usage
===

1 Build Image from Source
```
git clone https://github.com/jorgebonilla/storj-docker.git
cd storj-docker/dataserv-client
````
Before running the build command, make sure you add the right SJCX address to the Dockerfile.
```
docker build -t jorgebonilla/storj-dataserv-client:2.0.3  .
```
The Dockerfile will execute the following commands for you:
```
dataserv-client config --set_payout_address=$SJCX_ADDRESS
dataserv-client --url=http://status.driveshare.org:5000 register
```
3 Run the Docker Container:
```
docker run -it -v </your/storage/location>:/var/storj jorgebonilla/dataserv-client:2.0.3 bash
dataserv-client version 
```
4 Build the storj datastore:
```
root@8834f7426e1a:/# dataserv-client --url=http://status.driveshare.org:5000 --store_path=/var/storj --max_size=1TB build
***This might take a while***
root@8834f7426e1a:/# dataserv-client ping
```
5 Let the poll run:

From within the docker container:
 ```
dataserv-client poll
 ```
 From docker host:
 ```
 docker run -d jorgebonilla/storj-dataserv-client:2.0.3 dataserv-client poll
 ```
 
