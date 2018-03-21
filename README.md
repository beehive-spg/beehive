# beehive

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

<img src="https://i.imgur.com/VnKmMI0.png" width="20%">

This repository acts as a connector of all necessary beehive components by using submodules for an
easier overview. 

## Installation
First of all clone the repository with:
```
git clone https://github.com/beehive-spg/beehive.git
```

After that the submodules have to be downloaded. This can be done by issuing the following commands:
```
git submodule update --init --recursive
```

The repository includes a ```docker-compose.yml``` file, which starts up all containers needed
for Beehive to work properly. The Frontend, Backend, Routing and Generator images will all be pulled
from docker-hub, only the database image has to be built manually.

### Database Docker Image
To build the database image the following commands will have to be executed:
```
# go to db directory
cd database

# build beehive-database image
docker build --build-arg username=<USERNAME> --build-arg password=<DOWNLOAD_KEY> -t beehive-database
```

Replace ```<USERNAME>``` and ```<DOWNLOAD_KEY>``` with your [Datomic](https://my.datomic.com/login) email address and download key.

### Generator Environment Variables
For the Generator to work properly an environment file is needed. It should be named ```.env_generator``` 
and located in the main directory.

```
GOOGLE_API_KEY=<GOOGLE_MAPS_GEOCODING_API_KEY>
```
Replace ```<GOOGLE_MAPS_GEOCODING_API_KEY>``` with your own API key.

### Start the Application

After building the database image locally the docker-compose file can be started with:

```
docker-compose up
```

## Docker-Hub Links
- [Frontend](https://hub.docker.com/r/astwys/beehive-frontend/)
- [Backend](https://hub.docker.com/r/astwys/beehive-backend/)
- [Routing Engine](https://hub.docker.com/r/langhaarzombie/beehive-routing/)
- [Distribution](https://hub.docker.com/r/dschonas/beehive-distribution/)
- [Generator](https://hub.docker.com/r/dschonas/beehive-generator/)

## Component Repository Links
For details on how to interact with the individual components see the following links:
- [Frontend](https://github.com/beehive-spg/beehive-frontend)
- [Backend](https://github.com/beehive-spg/beehive-backend)
- [Routing Engine](https://github.com/beehive-spg/beehive-routing)
- [Distribution](https://github.com/beehive-spg/beehive-drone-distribution)
- [Generator](https://github.com/beehive-spg/beehive-order-generator)
- [Database](https://github.com/beehive-spg/beehive-database)
