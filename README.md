# ResinOS and Docker-compose

This is a demonstration project of using a [resinOS device](https://resinos.io/) as a remote host to [docker-compose](https://docs.docker.com/compose/overview/).
It just sets up a simple python webserver that uses a redis store to keep track of how many times the webpage has been 
visited.

## Usage

### Setup your resinOS device.
Head over to the getting started page of resinOS (https://resinos.io/docs/raspberrypi3/gettingstarted/)
1. Download one of the resinOS device images, in this example we use the raspberry pi 3.
2. **[Optional]** Configure the image for wifi connection, to do this you will first have to [install `rdt`](https://resinos.io/docs/raspberrypi3/gettingstarted/#install-resin-device-toolbox).
3. Power up the device and `ping resin.local` to make sure its connected to the network.

### Get Docker and Docker-compose Installed
Install docker + docker compose on your laptop, following this guide: https://docs.docker.com/compose/install/

### Spin up the services
1. First clone this repo:
```
git clone https://github.com/resin-io-playground/resinos-compose.git
```

2. Deploy your services:
From the project directory run the following.
```
DOCKER_API_VERSION=1.22 DOCKER_HOST=tcp://resin.local:2375 docker-compose up
```

#### Profit $$$
Point the browser on your laptop to resin.local:5000

## Warnings and Limitations.

* You need to make sure that the base images used in your services **match the architecture** of the device you are 
running the containers on. In this example, we target a raspberry pi 3, so we need our base images to be `armhf`, the
regular/official `amd64` images on dockerhub won't work.
