---
tags:
  - concept
  - software_engineering/operational_excellence
  - software_development/container
  - docker/images
  - docker/dockerfile
keywords:
  - container_image
  - dockerfile
topics:
  - software_development/container_microservice
name: Docker Container Images
date of note: 2024-12-29
---

## Concept Definition

>[!important]
>**Name**: Docker Container Images

![[Container as Microservice#^0d486a]]

- [[Container as Microservice]]

![[Docker Container Images#^3b1eef]]

- [[Docker Container Images]]


![[docker_image.png]]

### Build Docker Images via Dockerfile

>[!important] Definition
>A **Dockerfile** is a text document that contains *instructions* on how to *build* your *container image*. 
>- A Dockerfile includes instructions for what *base layer* to use (for example, whether you want to use a minimal version of Linux or use an image that has preinstalled software, such as a database engine). 
>- Other instructions include 
>	- *running commands* in the container, 
>	- or *copying* your application *data*, *dependencies*, and *configurations* into the container.

^5a2827


>[!important] Definition
>A **Dockerfile** is a *plain-text template* that you create with *instructions* that informs Docker *how* your Docker image is *built*, step by step.
>- Once you have this Dockerfile in place, you run the docker build command with the *Docker client* and the *Docker daemon* builds the *Docker image*.

^9e5967

![[dockerfile_build_images.png]]

>[!important] Definition
>
>Each *instruction* in  **Dockerfile**  that runs creates what is called a **layer**.
>- A **Docker image** is composed of *multiple layers* that are *stacked* on top of each other, and each layer can then be used *across multiple images*.
>- For two Dockerfiles, if the first two *instructions* were the *same*, then both Docker images would be able to *share* the first two layers.
>- This makes the Docker container *lightweight* since it has *less duplications*.

^159d45



![[docker_image_layers.png]]


## Explanation

>[!info]
>You can *pass* **configuration data** into the containers *at runtime*, through **environment variables** or through **volumes**.


## AWS ML Containers

- [[Amazon SageMaker Python SDK 2 Deploy a Pre-Trained Model]]
- [[Amazon SageMaker Python SDK 3 Frameworks]]
- [[Amazon SageMaker Python SDK 4.1 BYO Processing Container]]
- [[Amazon SageMaker Example Building Your Own Container 0 Overview]]
- [[Amazon SageMaker Example Building Your Own Container 1 Docker]]

- [[Pipeline for MODS Deep Learning training]]
- [[Pipeline for MODS training]]



-----------
##  Recommended Notes and References


- [Dockerfile reference](https://docs.docker.com/engine/reference/builder/)
- For more information, see [Best Practices for writing Dockerfiles](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/).
- Coursera
	- [Containerized Applications on AWS](https://www.coursera.org/learn/containerized-applications-on-aws/home/welcome)