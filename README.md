
1. Setup your resinOS device. (https://resinos.io/docs/raspberrypi3/gettingstarted/)
* Download
* configure
* ping resin.local

2. Install docker + docker compose on your laptop.
* https://docs.docker.com/compose/install/

3. Deploy your services:
```
DOCKER_API_VERSION=1.22 DOCKER_HOST=tcp://resin.local:2375 docker-compose up
```

4. visit resin.local:5000 in your webbrowser