# storj-docker
Storj Dataserv Client

Usage
===

1. Pull the Docker image:
```docker pull jorgebonilla/storj-dataserv-client```
2. Run docker image:
```docker run -it -v <Storj Directory>:/var/storj jorgebonilla/storj-dataserv-client bash```

3. register your address:
```
root@8834f7426e1a:/# dataserv-client --address=<bitcoin address> register
Address <bitcoin address> now registered on http://104.236.104.117.
```
4. Build the storj datastore:
```
root@8834f7426e1a:/# dataserv-client --store_path=/var/storj --max_size=13421772800 --address=<bitcoin address> build

```
***This might take a while***

Build Image from Source
===
```
git clone https://github.com/jorgebonilla/storj-docker.git
cd storj-docker/dataserv-client
docker build .
```
