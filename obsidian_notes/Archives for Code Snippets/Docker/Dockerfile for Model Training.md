---
tags:
  - code
  - code_snippet
  - aws/sagemaker
  - model/training
  - docker
keywords: 
topics: 
language: bash
date of note: 2024-03-27
---

## Code Snippet Summary

>[!important] 
>For the Python science stack, we will 
>- start from a *standard Ubuntu installation* and 
>- run the normal tools to *install the dependencies*. 
>- Finally, we *add the code* that implements our specific algorithm to the container and *set up the right environment* to run under.
>- Along the way, we *clean up extra space*. This makes the container smaller and faster to start.

- [[Dockerfile Instructions]]

## Background Knowledge
### Location of Dockerfile

- In the `container` directory are all the components you need to package the sample algorithm for Amazon SageMager:

```
.
|-- Dockerfile
|-- build_and_push.sh
`-- model
    |-- nginx.conf
    |-- predictor.py
    |-- serve
    |-- train
    `-- wsgi.py
```

- Let's discuss each of these in turn:
	* **`Dockerfile`** describes how to build your Docker container image. More details below.
	* **`build_and_push.sh`** is a script that uses the Dockerfile to build your container images and then pushes it to ECR. We'll invoke the commands directly later in this notebook, but you can just copy and run the script for your own algorithms.
	* **`model`** is the directory which contains the files that will be installed in the container.
	* **`local_test`** is a directory that shows how to test your new container on any computer that can run **Docker**, including an **Amazon SageMaker** *notebook instance*. Using this method, you can quickly iterate using small datasets to eliminate any structural bugs before you use the container with Amazon SageMaker. We'll walk through local testing later in this notebook.

The files that we'll put in the container are:
* __`nginx.conf`__ is the configuration file for the nginx front-end. Generally, you should be able to take this file as-is.
* __`predictor.py`__ is the program that actually implements the **Flask web server** and the predictions for this app. You'll want to *customize the actual prediction parts* to your application. Since this algorithm is simple, we do all the processing here in this file, but you may choose to have separate files for implementing your custom logic.
* __`serve`__ is the program started *when the container is started for **hosting***. It simply launches the gunicorn server which runs multiple instances of the Flask app defined in `predictor.py`. You should be able to take this file as-is.
* __`train`__ is the program that is invoked *when the container is run for **training***. You will modify this program to implement your training algorithm.
* __`wsgi.py`__ is a small wrapper used to invoke the Flask app. You should be able to take this file as-is.

In summary, the two files you will probably want to change for your application are `train` and `predictor.py`.

### The Dockerfile

- The **Dockerfile** *describes the image that we want to build*. You can think of it as describing the *complete operating system installation* of the system that you want to run. A Docker container running is quite a bit lighter than a full operating system, however, because it takes advantage of Linux on the host machine for the basic operations.

- [[Dockerfile Instructions]]
- [[Dockerfile as Instruction to Build Docker Image]]

### Building and registering the container

- The following shell code shows how to build the container image using `docker build` and push the container image to ECR using `docker push`. This code is also available as the shell script `container/build-and-push.sh`, which you can run as `build-and-push.sh decision_trees_sample` to build the image `decision_trees_sample`.

- [[Amazon ECR or Elastic Container Registry Create and Push Image]]


## Code

>[!important] Highlight
>This *Dockerfile* sets up an environment with PyTorch, CUDA, cuDNN, and various Python libraries commonly used for NLP tasks. It prepares the container to run Python applications, specifically those located in the `/opt/program` directory, which are copied from the host's `model` directory.
>- `model` directory contains the `train` script. See [[SageMaker BYO Container - Pytorch Lightning Training]] on how to write a `train` script for BYO containers


  
```bash
FROM pytorch/pytorch:1.13.1-cuda11.6-cudnn8-runtime
    
RUN apt-get -y update && apt-get install -y --no-install-recommends \
         wget \
         g++ \
         python3 \
         python3-dev \
         build-essential libssl-dev libffi-dev \
         libxml2-dev libxslt1-dev zlib1g-dev \
         python3-pip \
         git \
         nginx \
         libgcc-5-dev \
         ca-certificates \
         python3-setuptools \
    && rm -rf /var/lib/apt/lists/*

# Here we get all python packages.
# There's substantial overlap between scipy and numpy that we eliminate by
# linking them together. Likewise, pip leaves the install caches populated which uses
# a significant amount of space. These optimizations save a fair amount of space in the
# image, which reduces start up time.
RUN ln -s "/usr/bin/python3.10" /usr/bin/python
RUN python3.10 -m pip install pip --upgrade
RUN pip install --upgrade pip
        
RUN pip3 install boto3 \
                 gevent \
                 gunicorn \
                 fsspec \
                 beautifulsoup4 \
                 pandas \
                 scikit-learn \ 
                 matplotlib \
                 lxml \
                 flask \ 
                 spacy \
                 sagemaker \
                 fasttext \
                 tqdm \
                 torchmetrics \
                 lightning  \
                 transformers \
                 tensorboard

ENV PYTHONUNBUFFERED=TRUE
ENV PYTHONDONTWRITEBYTECODE=TRUE
ENV LC_ALL=C.UTF-8 
ENV LANG=C.UTF-8
ENV PATH="/opt/ml:/opt/program:${PATH}"

# RUN python -m spacy download en_core_web_sm
# RUN python -m spacy download xx_sent_ud_sm
# RUN python -m spacy download xx_ent_wiki_sm


COPY model /opt/program
WORKDIR /opt/program

ENTRYPOINT ["python3"]
```


- Check command from Dockerfile in [reference](https://docs.docker.com/reference/dockerfile/)'
- `FROM`: Create a new build stage from a **base image**.
- `RUN`: Execute *build* commands. [reference](https://docs.docker.com/reference/dockerfile/#run)
	- The `RUN`, `CMD`, and `ENTRYPOINT` instructions all have two possible forms:
		- `INSTRUCTION ["executable","param1","param2"]` (exec form)
		- `INSTRUCTION command param1 param2` (shell form)
- `ENV`: Set *environment variables*.
- `COPY`: *Copy* files and directories. [reference](https://docs.docker.com/reference/dockerfile/#copy)
	- The `COPY` instruction copies new files or directories from `<src>` and adds them to the filesystem of the container at the path `<dest>`.
- `WORKDIR`: Change **working directory**. It sets the working directory for instructions that follow it in the Dockerfile.  [reference](https://docs.docker.com/reference/dockerfile/#workdir)
- `ENTRYPOINT`: Specify **default executable**. [reference](https://docs.docker.com/reference/dockerfile/#entrypoint)
	- `ENTRYPOINT ["executable", "param1", "param2"]` or  `ENTRYPOINT command, param1 param2`
	- An `ENTRYPOINT` allows you to configure a container that will run as an executable.
	- *Command line arguments* to `docker run <image>` will be appended after all elements in an exec form `ENTRYPOINT`, and will override all elements specified using `CMD`.
	- This allows *arguments to be passed to the entry point*, i.e., `docker run <image> -d` will pass the `-d` argument to the entry point. You can override the `ENTRYPOINT` instruction using the `docker run --entrypoint` flag.
	- You can use the exec form of `ENTRYPOINT` to set fairly stable **default commands** and **arguments** and then use either form of `CMD` to set additional defaults that are more likely to be changed.
	  
- The instruction is not case-sensitive. However, convention is for them to be **UPPERCASE** to distinguish them from arguments more easily.
  
- `ENV PYTHONUNBUFFERED=TRUE`: it is to make sure `print` output saved in Cloudwatch logs.
	- Stack Overflow: [What is the use of PYTHONUNBUFFERED in docker file?](https://stackoverflow.com/questions/59812009/what-is-the-use-of-pythonunbuffered-in-docker-file)
	- AWS re:Post: [How to get logs or print statements from SageMaker PyTorch deployed endpoint?](https://repost.aws/questions/QU74MThjkyRVCtySw-DEozrQ/how-to-get-logs-or-print-statements-from-sagemaker-pytorch-deployed-endpoint)

### Build Image from Base Image

```bash
FROM pytorch/pytorch:1.13.1-cuda11.6-cudnn8-runtime
```

- It starts with the `pytorch/pytorch:1.13.1-cuda11.6-cudnn8-runtime` base image, which provides a pre-configured environment with PyTorch, CUDA, and cuDNN.
- See more pre-bulit images in [Docker Hub](https://hub.docker.com/).


### Set up Working Directory and Entry Point to the Container

```bash
COPY bsm /opt/program
WORKDIR /opt/program

ENTRYPOINT ["python3"]
```

- It copies the contents of the `bsm` directory from the host to the `/opt/program` directory in the container.
- It sets the working directory to `/opt/program`.
- It specifies the default command to run when the container starts, which is `python3`.




-----------
##  Recommended Notes

- [[Dockerfile Instructions]]
- 


- Overview of BYO training: [[SageMaker BYO Container Entry point]]
	- Prepare `train` script in [[SageMaker BYO Container - Pytorch Lightning Training]]
	- Prepare `predictor.py` script in [[SageMaker BYO Container - Pytorch Lightning Hosting and Prediction]]
- [[Amazon SageMaker Example Building Your Own Container 1 Docker]]
- [Dockerfile reference](https://docs.docker.com/reference/dockerfile/)
- [Docker Hub](https://hub.docker.com/)
	- [Docker Hub - Pytorch](https://hub.docker.com/r/pytorch/pytorch/tags). We can find base image from pytorch library here.
	- [Docker Hub - Huggingface/transformers-pytorch-gpu](https://hub.docker.com/r/huggingface/transformers-pytorch-gpu)
	- [Docker Hub - Langchain](https://hub.docker.com/r/langchain/langchain)
