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

After that the submodules have to be downloaded and checked out to the newest commit. This can be done by issuing the following commands:
```
git submodule update --init --recursive

get submodule update --recursive --remote
```

The repository includes a ```docker-compose.yml``` file, which is starts up all containers needed
for Beehive to work properly. The Frontend, Backend, Routing and Generator images will all be pulled
from docker-hub, only the database image will have to be built manually.

### Database Docker Image
To build the Database image the following commands will have to be executed:

```
# go to db directory
cd database

# build beehive-database image
docker build --build-arg username=<USERNAME> --build-arg password=<PASSWORD> -t beehive-database
```

Replace ```<USERNAME>``` and ```<PASSWORD>``` with your [Datomic](https://my.datomic.com/login) account credentials.

### Frontend Environment Variables
For the Frontend to work properly an environment file is needed. It should be named
```.env_fronted``` and located in the main directory.

The file content should look like this:
```
// default mapbox public api token
REACT_APP_MAPBOX_ACCESS_TOKEN=pk.eyJ1IjoiYXN0d3lzIiwiYSI6ImNqNTBzbHMzYTJkMTkycXFqOHV2bDFwc28ifQ.BAEjuFoOh6TfXlYKwRfRrg
REACT_APP_GOOGLE_API_KEY=<GOOGLE_MAPS_GEOCODING_API_KEY>
```

Replace ```<GOOGLE_MAPS_GEOCODING_API_KEY>``` with your own API key.
The Mapbox access token can be left as is, as it's the default public token, which is available to
everyone.

### Generator Environment Variables
The Generator also needs an environment file. Name it ```.env_generator``` and put the following
content into it:

```
GOOGLE_API_KEY=<GOOGLE_MAPS_GEOCODING_API_KEY>
```
Replace ```<GOOGLE_MAPS_GEOCODING_API_KEY>``` with your own API key.

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
