---
title: Docker
---

# Docker

[Credit to Eric Roth. This is just my
version](https://github.com/lifeeric/docker-cheat-sheet)

## Commands to List Things

### List all the running containers:

```
Docker ps
```

### List all the docker containers (stopped and running):

```
docker ps -a
```

### List all the images:

```
docker images
```

### List available commands:

```
docker
```

### List networks

```
docker network ls
```

### List processes running in a container

```
docker top [container_ID|container_name]
```

## Commands to Show Info/Status

### Get your installed docker's version

```
docker version
```

### Get info (num containers, images, versions of things).

```
docker info
```

### Get the logs for a container:

```
docker logs [container_ID|container_name]
```

### Info about a container:

```
docker inspect [container_ID|container_name]
```

### Get the stats of a container:

```
docker stats [container_ID|container_name]
```

### Inspect networks

```
docker network inspect network_name
```

### Inspect volumes 

```
docker volume ls
```

## Commands to Remove/Stop Things

### Stop a container:

```
docker stop [container_ID|container_name]
```

### Stop all running containers:

```
docker stop $(docker ps -aq)
```

### Remove container (must be stopped first)

```
docker rm [container_ID|container_name]
```

### Remove a running container

```
docker rm -f [container_ID|container_name]
```

### Remove an image

```
docker rmi [image_name|image_ID]
```

### Remove all images

```
docker rmi $(docker images -a -q)
```

### Remove networks

```
docker network rm network_name [container_name|container_id]
```

### Cleanup unused volumes

```
docker volume prune
```

## Commands to Start/Run Things

### Create and run a container (in interactive mode)

```
docker run -it [image_name|image_ID]
```

### Create and run a container (in the background)

```
docker run -d [image_name|image_ID]
```

### Create, run a container, and name it

```
docker run [-d|-it] --name "some_name" [image_name|image_ID]
```

### Create, run a container, and select ports

```
docker run [-d|-it] -p host_port:container_port [image_name|image_ID]
```

### Create, run, and limit memory usage:

```
docker run [-d|-it] -m integer_and_unit [image_name|image_ID]
```

The units are b, k, m, or g


### Create a network

```
docker network create network_name
```
or
```
docker network create --driver bridge network_name
```

### Build image from Dockerfile

```
docker image build -t reponame .
```
Looks for the Dockerfile in the current directory


### Run a container in a network

```
docker run [-it|-d] --net=network_name [image_name|image_ID]
```

## Changing Things when They're Running

### Attach to running container

docker attach container_name

### Get into interactive mode

```
docker exec -it conatiner_name [bash|sh]
```

### Connect a running container to a network

```
docker network connect network_name [container_name|container_id]
```

### Disconnect a running container from a network

```
docker network disconnect network_name [container_name|container_id]
```

### Retag existing image

```
docker image tag image_name new_name
```

### Add a tag to a new image:

```
docker image tag image_name image_name:tag_name
```

## Dockerfile

Has to be name Dockerfile (case sensitive)

Parts:

- FROM - the os used
- ENV - Environment variables
- RUN - run commands, scripts, etc.
- EXPOSE - expose/declare? what ports the image uses
- CMD - Final command, convention where you run the main app
- WORKDIR - sets the working directory
- COPY - copy from host to container

## Misc 

### Download an image:

```
docker pull image_name
```

### Upload to docker hub

```
docker image push image_name
```
if denied:
```
docker login
```



