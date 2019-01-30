# Forked from https://github.com/ZcashFR/zcash-docker
* update to latest stable Zcash version v2.0.2
* Zcash data volume

### build
```
docker build -t jro7/zcash .
```

# create volume first
```
docker volume create zcash-data
```
# start zcash container and mount data volume
```
docker run -d \
    --name zcash \
    --mount source=zcash-data,target=/home/zcash \
    jro7/zcash
```

# update zcash version
1. pull latest zcash image `docker pull jro7/zcash` OR build latest version yourself
1. stop running zcash container `docker stop zcash`
1. remove zcash container `docker rm zcash`
1. start again using above "start"


# remove everything
1. stop running zcash container `docker stop zcash`
1. remove zcash container `docker rm zcash`
1. remove zcash-data container `docker volume rm zcash-data`
1. remove zcash image `docker rmi jro7/zcash`

# docker docs on volume
https://docs.docker.com/storage/volumes/
---
# --- TODO --- OLD DOCS

# Docker Zcash Full Node v2.0.2

Official Zcash full node build from zcash source. Docker image based on debian stretch-slim.

## Getting Started



### Prerequisites

Install Docker on your computer.

### Installing

To install zcash full node pull the latest image from Docker Hub

```
docker pull zcashfr/zcash
```
Create zcash container
```
docker run -d --name zcash zcashfr/zcash
```
Docker entrypoint is configure to run launch-zcashd.sh, this script download Zcash keys and after start zcashd service. At first start please wait until keys download is complete (~800MB) before using zcash-cli executable. 

### Usage
You can use all commands of official Zcash client, please refer to [Zcash wiki](https://github.com/zcash/zcash/wiki).

Example of using zcash-cli to get information.
```
docker exec zcash zcash-cli getinfo
```

## Built With

* [Docker](https://www.docker.com/) - Docker client
* [Zcash](https://github.com/zcash/zcash) - Zcash full node

## Contributing

Submit your Issues or Pull request on Github project


## Authors

* **Fabrice Marchal** - *Initial work* - [Le_Bleu](https://github.com/LeBleu89)


## License

This project is licensed under the GPL 3.0 License - see the [LICENSE.md](LICENSE.md) file for details

