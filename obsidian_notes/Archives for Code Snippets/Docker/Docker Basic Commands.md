---
tags:
  - code
  - code_snippet
  - docker
  - docker/dockerfile
  - docker/images
  - software_development/container
keywords:
  - dockerfile
topics:
  - software_development/container_microservice
language: Docker Basic Commands
date of note: 2025-01-04
---

## Code Snippet Summary

>[!important]
>- `docker build`: **Builds** an image from a *Dockerfile*. 
>	- In the demonstration, we pass `-t` to *tag the image* that’s created.
>- `docker run`: **Creates** and **starts** a container. 
>	- In the demonstration, we use `-p` to *expose ports*, 
>	- `-e` to *set environment variables*, 
>	- and `-v` to *bind mount volumes*.
>- `docker exec`: **Runs** a command in a **running container**.
>- `docker stop`: **Stops** a container.
>- `docker rm`: **Removes** a container. 
>	- Use `-f` to *force* the remove.

- [[Dockerfile Instructions]]
- [[Amazon ECR or Elastic Container Registry Create and Push Image]]
- [[Docker Remove Unused Images and Containers]]


## Code

### Build Docker Image via Dockerfile


```bash
docker build -t first-image .
```

- `docker build`: : **Builds an image** from a **Dockerfile**. 
	- In the demonstration, we pass `-t` to *tag* the image that’s created.


### Check the container image


```bash
docker image ls
```

- `docker image ls`: list all of docker images

### Run Docker Image

```bash
docker run -p 8080:8080 first-image
```

- `docker run`: **Creates** and **starts** a container. 
	- In the demonstration, we use `-p` to **expose ports**,  
		- The `-p` parameter **publishes** the *port* 8080 *inside* the container on *port* 8080 of the *host*.
	- `-e` to **set environment variables**, 
	- and `-v` to **bind mount volumes**.

```bash
docker run -e MESSAGE_COLOR=\#0000ff -p 8080:8080 first-image
```

- passing a new environment variable `MESSAGE_COLOR`

```bash
docker run -v ~/input.txt:/app/input.txt -p 8080:8080 first-image
```

- I want to make my host file system available inside of the container.
- To do this, I'll use a bind mount. I want to use `input.txt` on my host to *replace* the `app/input.txt` *in the container*.
- The `-v` parameter takes *two arguments*.
	- The first is the location on the *host*,
	- the second is the location in the *container*.
- This can be a *directory* or a *file*.


### Detach Docker Container 

```bash
docker run -d -p 8080:8080 first-image
```


### View the running Docker Container

```bash
docker ps
```

- `docker ps`:  list of the **running container** in the process list.
- View the running Docker containers.

### View logs 

```bash
docker logs webapp
```

- `docker logs`: view logs that are being captured from the container


### Check what inside the Container Environment

```bash
docker exec -it 52 sh
```

- `docker exec`: **Runs** a command in a **running container**.
	- We only need a prefix that will uniquely identify the container. In this case it is `52` as the *container id* is `52*`
	- `-i` means that  `stdin` always *attached*,
	- `-t`  will provision a *pseudo* `tty`, or *terminal*.
	- The last parameter is the command I want run **inside the container**. In this case, it is the command `sh`

### Stop Running Container

```bash
docker stop 52
```


### Remove Container

```bash
docker rm 52
```




-----------
##  Recommended Notes

- [[Docker Container]]
- [[Docker Container Images]]
- [[Docker Container Image Registry and DockerHub]]

- [[Amazon SageMaker Python SDK 2 Deploy a Pre-Trained Model]]
- [[Amazon SageMaker Python SDK 3 Frameworks]]
- [[Amazon SageMaker Python SDK 4.1 BYO Processing Container]]
- [[Amazon SageMaker Example Building Your Own Container 0 Overview]]
- [[Amazon SageMaker Example Building Your Own Container 1 Docker]]

- Coursera
	-  [**Exercise 1: Creating the First Container**](https://aws-tc-largeobjects.s3.us-west-2.amazonaws.com/DEV-AWS-MO-ContainersRedux/exercise-1-firstcontainer.html)
	- In this exercise, you create an AWS Cloud9 instance and modify some of the environment settings. You also install the prerequisites and source code that are needed to launch new container instances inside your AWS Cloud9 environment.

- [Docker CLI Reference](https://docs.docker.com/reference/cli/docker/)
- see [Dockerfile reference](https://docs.docker.com/engine/reference/builder/) for more information about Dockerfile instructions, 
- see the full reference for the [docker base command](https://docs.docker.com/engine/reference/commandline/docker/).



