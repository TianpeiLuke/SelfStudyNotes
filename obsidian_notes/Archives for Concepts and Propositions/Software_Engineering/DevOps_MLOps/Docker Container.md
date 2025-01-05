---
tags:
  - concept
  - software_development/container
  - docker/concepts
keywords:
  - docker_container
topics:
  - software_development/container_microservice
name: Docker Container
date of note: 2025-01-02
---

## Concept Definition

>[!important]
>**Name**: Docker Container


![[Amazon SageMaker Example Building Your Own Container 1 Docker#^e3ea3f]]

### Docker Client, Docker Daemon, and Image Registry

>[!important] Definition
>**Docker** has three main components:
>- The **Docker client**: the client that *sends the requests* to server.
>	- The Docker client provides developers a way to interact with Docker through a **command line interface**, or **CLI**. 
>	- This is how you issue commands to Docker to 
>		- *build* your containers, `docker build`
>		- *run* your containers, `docker run`
>		- or *stop* your containers. `docker stop`
>- The **Docker daemon**: the *server* that running on the machine that *carries out the request*
>	- The Docker daemon is installed on a *host machine*.
>	- The Docker daemon creates and manages the *Docker images* on your behalf.
>	- The purpose of Docker daemon is to perform the request from client.
>- and the **Image Registry**.
>	- The image registry is the place to store **Docker images**.
>	- It can *push* or *pull* Docker images.
>	- A registry makes it possible for the the *Docker daemon* to *retrieve and run* the requested *Docker images*.
>
>The **Docker client** and **Docker daemon** use a *client-server model*.

^3dfe41

- [[Container as Microservice]]
- [[Docker Container Daemon]]

![[docker_container_images_registry.png]]

![[docker_flow_diagram.png]]

### Docker Image

![[Docker Container Images#^3b1eef]]


![[Docker Container Images#^0a8ba3]]

- [[Docker Container Images]]
- [[Docker Container Image Registry]]
- [[Container Orchestration]]



## Explanation



## AWS ML Docker Containers

- [[Amazon SageMaker Python SDK 2 Deploy a Pre-Trained Model]]
- [[Amazon SageMaker Python SDK 3 Frameworks]]
- [[Amazon SageMaker Python SDK 4.1 BYO Processing Container]]
- [[Amazon SageMaker Example Building Your Own Container 0 Overview]]
- [[Amazon SageMaker Example Building Your Own Container 1 Docker]]

- [[Pipeline for MODS Deep Learning training]]
- [[Pipeline for MODS training]]




-----------
##  Recommended Notes and References


- Coursera
	- [Containerized Applications on AWS](https://www.coursera.org/learn/containerized-applications-on-aws/home/welcome)
- Documentation
	- [Docker Homepage](https://www.docker.com/)
	- [Docker Documentation](https://docs.docker.com/)
	- For more information about Docker, see the [Docker documentation](https://docs.docker.com/).