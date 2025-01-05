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
language: Docker
date of note: 2025-01-04
---

## Code Snippet Summary

>[!important]


## Code

>[!info]
> - `FROM`: **Defines the base image**. All the instructions that follow are run in a container launched from the base image.
>     
> - `WORKDIR`: Sets the **working directory** for the subsequence instructions.
>     
> - `ENV`: Sets **environment variables**.
>     
> - `COPY`: **Copies** files and directories into the *container image*.
>     
> - `RUN`: **Runs commands** in the new container. This instruction commits *a new layer* on top of the present layer.
>     
> - `CMD`: Sets the **default command to run** when the container is **launched**.
>     
> - `EXPOSE`: Is used to **document** the containers that the port exposes.

- [[Docker Container Images#Union File System]]






-----------
##  Recommended Notes

- [[Docker Container]]
- [[Docker Container Images]]
- [[Docker Container Image Registry]]

- [[Amazon SageMaker Python SDK 2 Deploy a Pre-Trained Model]]
- [[Amazon SageMaker Python SDK 3 Frameworks]]
- [[Amazon SageMaker Python SDK 4.1 BYO Processing Container]]
- [[Amazon SageMaker Example Building Your Own Container 0 Overview]]
- [[Amazon SageMaker Example Building Your Own Container 1 Docker]]


- For more information about Dockerfile instructions, see [Dockerfile reference](https://docs.docker.com/engine/reference/builder/)



