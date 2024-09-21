# docker_liquidsoap

[![License](https://img.shields.io/github/license/ZetZed/docker_liquidsoap)](https://github.com/ZetZed/docker_liquidsoap/blob/master/LICENSE)

Dockerfile for running [Liquidsoap](https://www.liquidsoap.info/) in a container. \
Just mount your Liquidsoap script, music directory and you are good to go!

Works well with containerized [icecast2](https://icecast.org/): [ZetZed/docker_icecast2](https://github.com/ZetZed/docker_icecast2)

### Installation
- Build the image yourself
  -  `docker build -t ZetZed/liquidsoap github.com/ZetZed/docker_liquidsoap`
  -  Add build arg `LIQUIDSOAP_VERSION` to specify the version of Liquidsoap to use in the image, check available versions [here](https://opam.ocaml.org/packages/liquidsoap/). \
    Example: `docker build -t ZetZed/liquidsoap:1.4.4 --build-arg LIQUIDSOAP_VERSION=1.4.4 github.com/ZetZed/docker_liquidsoap`

### Configuration
- Mount your Liquidsoap script file to `/etc/liquidsoap/script.liq`
- Mount your music directory to `/music`
- In your Liquidsoap script change path to your music directory to `/music`

#### docker run
```
docker run --name liquidsoap -d --restart=always \
--volume /path/to/your/script.liq:/etc/liquidsoap/script.liq \
--volume /path/to/your/music:/music \
ZetZed/liquidsoap
```
#### docker-compose.yml
```
liquidsoap:
  image: ZetZed/liquidsoap
  container_name: liquidsoap
  restart: always
  volumes:
    - /path/to/your/script.liq:/etc/liquidsoap/script.liq
    - /path/to/your/music:/music
```
