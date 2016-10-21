# ResinOS and Docker-compose

This is a demonstration project of using a [resinOS device](https://resinos.io/) as a remote host to [docker-compose](https://docs.docker.com/compose/overview/).
It just sets up a simple python webserver that uses a redis store to keep track of how many times the webpage has been 
visited.

## Usage

1. Setup your resinOS device. (https://resinos.io/docs/raspberrypi3/gettingstarted/)
* Download one of the resinOS device images, in this example we use the raspberry pi 3.
* **[Optional]** Configure the image for wifi connection, to do this you will first have to [install `rdt`](https://resinos.io/docs/raspberrypi3/gettingstarted/#install-resin-device-toolbox).
* Power up the device and `ping resin.local` to make sure its connected to the network.

2. Install docker + docker compose on your laptop.
* https://docs.docker.com/compose/install/

3. clone this repo:

4. Deploy your services:
From the project directory run the following.
```
DOCKER_API_VERSION=1.22 DOCKER_HOST=tcp://resin.local:2375 docker-compose up
```

4. visit resin.local:5000 in your webbrowser

## Warnings and Limitations.

* You need to make sure that the base images used in your services **match the architecture** of the device you are 
running the containers on. In this example, we target a raspberry pi 3, so we need our base images to be `armhf`, the
regular/official `amd64` images on dockerhub won't work.
