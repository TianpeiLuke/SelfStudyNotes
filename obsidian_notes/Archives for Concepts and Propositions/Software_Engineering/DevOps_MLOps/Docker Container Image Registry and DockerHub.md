---
tags:
  - concept
  - software_engineering/operational_excellence
  - software_development/container
  - docker/concepts
keywords:
  - container_registry
  - docker_image_registry
  - image_registry
topics:
  - software_development/container_microservice
name: Docker Container Image Registry and DockerHub
date of note: 2024-12-29
---

## Concept Definition

>[!important]
>**Name**: Docker Container Image Registry and DockerHub

![[Container as Microservice#^0d486a]]

- [[Container as Microservice]]
- [[Microservice Definition]]
- [[Infrastructure as Code for Continuous Delivery]]

### Container Registry

>[!important] Definition
>**Container Registry** is a repository for 
>- *storing*, 
>- *sharing* 
>- and *deploying container images*, 
>
>often integrated into *CI/CD pipelines*. 
>
>Examples: Docker Hub, AWS ECR.

^3b1eef

- [[Continuous Integration or CI in DevOps and MLOps]]
- [[Continuous Delivery or CD in DevOps and MLOps]]

>[!important] Definition
>An **image registry** is a repository where you can store *container images*. 
>- You can store the images either *publicly* or *privately*. 
>- From the repository, images can be *pulled* and *deployed*, or used by other *developers*.

- [[DevOps]]
- [[Docker Container Images]]

>[!important] Definition
>**Image registries** can be public or private. 
> 
> - **Public registries** are useful for providing images that can be used as *base images* for software development. 
> 	- e.g. [[Amazon SageMaker Python SDK 3 Frameworks]]
> 	- [Docker Hub](https://hub.docker.com/)
> 
> - **Private registries** are useful in situations where you don’t want to expose container images to the public, which is often the case with proprietary software.


![[docker_container_images_registry.png]]

![[Docker Container#^3dfe41]]

- [[Docker Container]]

### Docker Hub

>[!important] Definition
>**Docker Hub** is a popular repository for *container images*. 
>- It offers a variety of sources for container images that you can use, including images from container community developers, open-source projects, and software vendors. 

- For more information about Docker Hub, see [Docker Hub](https://www.docker.com/products/docker-hub/).



## Explanation



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

