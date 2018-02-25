Fork of [yujiod/docker-mineos](https://github.com/yujiod/docker-mineos). Docker image available on the [Docker Hub](https://hub.docker.com/r/lewazo/mineos/).
## Changes made in this fork
* Add support for persistent config file through docker volumes.
* Add support for changing timezones through the TZ env variable.

# minecraft-mineos

Dockerfile for creating Mine OS server image with Java 8.

[Mine OS - easy minecraft hosting solution](http://minecraft.codeemo.com/)

## Usage

    docker run -d lewazo/docker-mineos
    docker run -d -p 8443:8443 -p 25565:25565 lewazo/docker-mineos

The WebUI on 8443 port with self signed SSL. When binding to 8443, open below URL.

https://<hostname>:8443/

Login username is `minecraft`. Password is auto genereated. Please check password in logs.

    docker logs <container_id>

You can also specify a password when running the container. The environment variable is `PASSWORD`.

    docker run -d -e PASSWORD=cr33p3r lewazo/docker-mineos

## Console access

SSH is no longer supported.
Please use exec on docker.

    docker exec -it <container_id> bash

### Mount minecraft data volume

The mount point is `/var/games/minecraft`.

    docker run -d -v /var/games/minecraft lewazo/docker-mineos

### Multiple minecraft server port binding

    docker run -d -e PASSWORD=cr33p3r -v /var/games/minecraft -p 8443:443 \
    -p 25565:25565 -p 25566:25566 -p 25567:25567 -p 25568:25568 -p 25569:25569 -p 25570:25570 \
    lewazo/docker-mineos
