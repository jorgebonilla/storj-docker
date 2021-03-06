# storj-docker
Storj Dataserv Client

Note: Make sure your Docker hosts time is in sync. Bad things can happen with a off-synced time.
````
ntpdate <your favorite ntp server>
```

Usage
===

1 Build Image from Source
```
git clone https://github.com/jorgebonilla/storj-docker.git
cd storj-docker/dataserv-client
````
Before running the build command, make sure you add the right SJCX address to the Dockerfile.
```
docker build -t jorgebonilla/dataserv-client:2.1.3  .
```
The Dockerfile will execute the following commands for you:
```
dataserv-client --url=http://switch.driveshare.org config --set_payout_address=$SJCX_ADDRESS
```
2 Run the Docker Container:
```
docker run -it -v </your/storage/location>:/var/storj jorgebonilla/dataserv-client:2.1.3 bash
dataserv-client version 
```

3 Let the poll run, it will automatically build the datastore:

From within the docker container:
 ```
dataserv-client --url=http://switch.driveshare.org --max_size=<maxSize> --store_path=/var/storj farm
 ```
 From docker host:
 ```
docker run -v </your/storage/location>:/var/storj -d jorgebonilla/dataserv-client:2.1.3 dataserv-client --url=http://switch.driveshare.org --max_size=<maxSize> --store_path=/var/storj farm
 ```
 
For more info refer to the [storj project] (https://github.com/Storj/dataserv-client "Storj Project")

If this was helpfull to you in anyway, please feel free to drop a tip @ [1GkYUGuqgXaV2dpdkZAC97ytYaKRFKdVqT](bitcoin:1GkYUGuqgXaV2dpdkZAC97ytYaKRFKdVqT "Bitcoin Address")
