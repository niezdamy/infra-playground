# Handy docker commands:

## Build

Build image from Dockerfile in the current dir and tag image

```bash
docker build -t myimage:1.0 .
```

List and delete images

```bash
docker image ls
docker image rm alpine:3.4
```

Pull and push images, retag

```bash
docker pull myimage:1.0
docker tag myimage:1.0 myrepo/myimage:2.0
docker push myrepo/myimage:2.0
```

Run a container from the Alpine version 3.9 image, name the running container “web” and expose port 5000 externally, mapped to port 80 inside the container

```bash
docker container run --name web -p 5000:80 alpine:3.9
```

Stop a running container through SIGTERM

```bash
docker container stop web
```

Stop a running container through SIGKILL

```bash
docker container kill web
```

Delete all running and stopped containers

```bash
docker container rm -f $(docker ps -aq)
```

Print the last 100 lines of a container’s logs

```bash
docker container logs --tail 100

```

List the running containers (add --all to include stopped containers)

```bash
docker container ls -all
```

List the networks

```bash
docker network ls
```

How to SSH into a running container

```
docker ps
docker exec -it <container name> /bin/bash
```

Get IP Address

```bash
docker inspect $(dl) | grep -wm1 IPAddress | cut -d '"' -f 4

docker inspect $(dl) | jq -r '.[0].NetworkSettings.IPAddress'

```

Docker stats for all containers

```bash
docker stats $(docker ps --format '{{.Names}}')
```

Gete port mapping

```bash
docker inspect -f '{{range $p, $conf := .NetworkSettings.Ports}} {{$p}} -> {{(index $conf 0).HostPort}} {{end}}' <containername>

```

Clean Up

```bash
docker system prune --all --force
```

## Dockerfile instructions:

- [.dockerignore](https://docs.docker.com/engine/reference/builder/#dockerignore-file)
- [FROM](https://docs.docker.com/engine/reference/builder/#from) Sets the Base Image for subsequent instructions.
- [MAINTAINER (deprecated - use LABEL instead)](https://docs.docker.com/engine/reference/builder/#maintainer-deprecated) Set the Author field of the generated images.
- [RUN](https://docs.docker.com/engine/reference/builder/#run) execute any commands in a new layer on top of the current image and commit the results.
- [CMD](https://docs.docker.com/engine/reference/builder/#cmd) provide defaults for an executing container.
- [EXPOSE](https://docs.docker.com/engine/reference/builder/#expose) informs Docker that the container listens on the specified network ports at runtime. NOTE: does not actually make ports accessible.
- [ENV](https://docs.docker.com/engine/reference/builder/#env) sets environment variable.
- [ADD](https://docs.docker.com/engine/reference/builder/#add) copies new files, directories or remote file to container. Invalidates caches. Avoid `ADD` and use `COPY` instead, cause of default behavior (add decompress archives)
- [COPY](https://docs.docker.com/engine/reference/builder/#copy) copies new files or directories to container. By default this copies as root regardless of the USER/WORKDIR settings. Use `--chown=<user>:<group>` to give ownership to another user/group. (Same for `ADD`.)
- [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#entrypoint) configures a container that will run as an executable.
- [VOLUME](https://docs.docker.com/engine/reference/builder/#volume) creates a mount point for externally mounted volumes or other containers.
- [USER](https://docs.docker.com/engine/reference/builder/#user) sets the user name for following RUN / CMD / ENTRYPOINT commands.
- [WORKDIR](https://docs.docker.com/engine/reference/builder/#workdir) sets the working directory.
- [ARG](https://docs.docker.com/engine/reference/builder/#arg) defines a build-time variable.
- [ONBUILD](https://docs.docker.com/engine/reference/builder/#onbuild) adds a trigger instruction when the image is used as the base for another build.
- [STOPSIGNAL](https://docs.docker.com/engine/reference/builder/#stopsignal) sets the system call signal that will be sent to the container to exit.
- [LABEL](https://docs.docker.com/config/labels-custom-metadata/) apply key/value metadata to your images, containers, or daemons.
- [SHELL](https://docs.docker.com/engine/reference/builder/#shell) override default shell is used by docker to run commands.
- [HEALTHCHECK](https://docs.docker.com/engine/reference/builder/#healthcheck) tells docker how to test a container to check that it is still working.

```

```
