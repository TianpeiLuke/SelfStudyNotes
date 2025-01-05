---
tags:
  - concept
  - software_engineering/operational_excellence
  - software_development/container
  - docker/images
keywords:
  - container_image
  - docker_image_registry
  - docker_image
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
- [[Microservice Definition]]
- [[Infrastructure as Code for Continuous Delivery]]

>[!important] Definition
>**Container Image** is a *lightweight*, *stand-alone*, *executable* software package allowing code to run quickly and reliably *across environments*.

^3b1eef

- [[Continuous Integration or CI in DevOps and MLOps]]
- [[Continuous Delivery or CD in DevOps and MLOps]]


>[!important] Definition 
>**Docker container images** are *lightweight, executable packages* that include everything you need in it.
> 
>- All of your *application code*, 
>- *software*, 
>- *dependencies*, 
>- and *configuration variables*.
> 
>They are considered *read-only artifacts*.
>- Once an image is built, it *cannot be changed* unless you build a new image.
>- Docker Images can be stored in **Image Registry** from which an image can be *pulled and run* on a machine or host

^0a8ba3


![[docker_image.png]]

### Build Docker Images via Dockerfile

![[Dockerfile as Instruction to Build Docker Image#^5a2827]]

![[dockerfile_build_images.png]]

![[Dockerfile as Instruction to Build Docker Image#^159d45]]

- [[Dockerfile as Instruction to Build Docker Image]]
- [Dockerfile reference](https://docs.docker.com/engine/reference/builder/)

![[docker_image_layers.png]]

### Union File System

>[!important] Definition 
> Docker uses what is called a **union file system** for the efficient storage of these layers, or what you can think of as the *building blocks* for container.
> 
>
>A union file system allows you to *overlay multiple layers* so that they appear as a *unified view* to the container.
> 
>- If a file that exists in a *lower layer* needs to be modified, it would be *copied* to the **modifying layer**, not modifying the copy from the lower layer.
>	- Note that Docker images are *read-only*. So in order to make changes, Docker mounts a **writeable layer** on the *top* of the lower **read-only layers**.
> 
>- This *writeable layer* allows any processes or applications running inside the container a place to *modify* or *create files*.
>- The read-only version of the file would remain *unchanged*, but is now *hidden underneath* the copy in the writeable layer.
>  
>This is called the **copy-on-write strategy**.

>[!info]
>By using the **copy-on-write strategy**,  all of the *read-only layers* of the image remain unchanged, which means that they can be *shared* by *multiple different running container instances*.
>- So the image is shared, but each container gets its **own writeable top layer**.
>- This writeable top layer stays *relatively small* by only bringing data into the writeable layer when needed.




![[docker_union_file_system.png]]

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

- Coursera
	- [Containerized Applications on AWS](https://www.coursera.org/learn/containerized-applications-on-aws/home/welcome)