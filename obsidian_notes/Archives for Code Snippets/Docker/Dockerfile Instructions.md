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
language: Dockerfile Instructions
date of note: 2025-01-04
---

## Code Snippet Summary

>[!important]
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


## Code

### Dockerfile

```bash
FROM pytorch/pytorch:1.13.1-cuda11.6-cudnn8-runtime

RUN pip install --upgrade pip


WORKDIR /opt/program
ENV PATH="/opt/ml:/opt/program:${PATH}"
COPY model /opt/program



ENTRYPOINT ["python3"] 
```

- `FROM` : set the prebuilt pytorch Docker image as the **base image**
- `RUN`: run the bash linux command to install or upgrade `pip`

Then we set `opt/program` as the **work directory** with 
```
WORKDIR /opt/program
```

- After that, we add the work directory into to **environment variable**  `PATH` via  ```

```
ENV PATH="/opt/program:${PATH}"
```

- And we *copy*  the *local directory* `model` to the directory `opt/program` in the *container*

```
COPY model /opt/program
```

- [[Dockerfile for Model Training]]





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


- [Docker CLI Reference](https://docs.docker.com/reference/cli/docker/)
- see [Dockerfile reference](https://docs.docker.com/engine/reference/builder/) for more information about Dockerfile instructions, 
- see the full reference for the [docker base command](https://docs.docker.com/engine/reference/commandline/docker/).



