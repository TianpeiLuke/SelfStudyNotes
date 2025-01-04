---
tags:
  - excerpt
  - documentation
  - code_package
  - aws/sagemaker
  - container
  - bring_your_own
aliases: 
keywords: 
topics:
  - BYO container
language: python
date of note: 2024-03-28
name: Building Your Own Container
version: 
year: 2022
---
# Part 1: Packaging and Uploading your Algorithm for use with Amazon SageMaker

## An overview of Docker

>[!info] **Docker**
>*Docker* provides a simple way to package arbitrary code into an ***image*** that is totally *self-contained*. Once you have an image, you can use *Docker* to run a ***container*** based on that image. Running a container is just like running a program on the machine except that *the container creates a fully self-contained environment for the program to run*. Containers are *isolated* from each other and from the host environment, so the way you set up your program is the way it runs, no matter where you run it.

^e3ea3f


>[!quote]
> - Docker is more powerful than **environment managers** like conda or virtualenv because (a) it is *completely language independent* and (b) it *comprises your whole operating environment*, including startup commands, environment variable, etc.
> 
> - In some ways, a Docker container is like a **virtual machine**, but it is much lighter weight.
> 
> - Docker uses a simple file called a `Dockerfile` to specify *how the image is assembled*. We’ll see an example of that below. You can *build your Docker images* based on Docker images built by yourself or others, which can simplify things quite a bit.
> 
> - **Amazon SageMaker** uses *Docker* to allow users to train and deploy arbitrary algorithms.

- [[Docker Container]]

## How Amazon SageMaker runs your Docker container

- Because you can run the same image in *training* or *hosting*, Amazon SageMaker runs your container with the argument `train` or `serve`. How your container processes this argument depends on the container:
  
	- In the example here, we don’t define an `ENTRYPOINT` in the Dockerfile so Docker will *run the command `train` at training time* and *`serve` at serving time*. In this example, we define these as executable Python scripts, but they could be any program that we want to start in that environment.
	  
	- If you *specify a program as an `ENTRYPOINT` in the Dockerfile*, that program will be *run at startup* and *its first argument will be `train` or `serve`*. The program can then look at that argument and decide what to do.
	  
	- If you are building *separate containers* for training and hosting (or building only for one or the other), you can define a program as an `ENTRYPOINT` in the Dockerfile and *ignore (or verify) the first argument passed in*.

### Running your container during training

>[!quote]
>When Amazon SageMaker runs **training**, your `train` script is run just like a regular Python program. A number of files are laid out for your use, **under the `/opt/ml` directory**:
```
/opt/ml
|-- input
|   |-- config
|   |   |-- hyperparameters.json
|   |   `-- resourceConfig.json
|   `-- data
|       `-- <channel_name>
|           `-- <input data>
|-- model
|   `-- <model files>
`-- output
    `-- failure
```

- **The input**
	- `/opt/ml/input/config` contains information to control how your program runs. `hyperparameters.json` is a **JSON-formatted** dictionary of *hyperparameter* names to values. **These values will always be strings**, so you may need to *convert* them. `resourceConfig.json` is a JSON-formatted file that describes the *network layout* used for *distributed training*. Since scikit-learn doesn’t support distributed training, we’ll ignore it here.
    
	- `/opt/ml/input/data/<channel_name>/` (for *File mode*) contains **the input data** for that *channel*. The channels are created based on the call to **CreateTrainingJob** but it’s generally important that *channels match what the algorithm expects*. The files for each channel will be copied from S3 to this directory, *preserving the tree structure indicated by the S3 key structure.*
    
	- `/opt/ml/input/data/<channel_name>_<epoch_number>` (for *Pipe mode*) is the pipe for a given epoch. Epochs start at zero and go up by one each time you read them. There is no limit to the number of epochs that you can run, but you must close each pipe before reading the next epoch.
	  
- **The output**
	- `/opt/ml/model/` is the directory where you **write the model** that your algorithm generates. Your model can be in any format that you want. It can be a single file or a whole directory tree. SageMaker will package any files in this directory into a compressed tar archive file. This file will be available at the S3 location returned in the `DescribeTrainingJob` result.
	  
	- `/opt/ml/output` is a directory where the algorithm can write a file `failure` that describes why the job failed. The *contents of this file will be returned in the `FailureReason` field* of the `DescribeTrainingJob` result. For jobs that *succeed*, there is *no reason to write* this file as it will be ignored.

### Running your container during hosting


>[!quote]
> **Hosting** has a very different model than training because hosting is responding to *inference requests* that come in via **HTTP**. In this example, we use our recommended Python serving stack to provide robust and scalable serving of inference requests:

![[amazon_sagemaker_inference_byo_.webp]]

Amazon SageMaker uses two **URLs** in the container:

- `/ping` will receive **`GET` requests** from the infrastructure. Your program returns *200* if the container is up and *accepting requests*.
    
- `/invocations` is the endpoint that receives **client inference `POST` requests**. The format of the request and the response is up to the algorithm. If the client supplied `ContentType` and `Accept` *headers*, these will be passed in as well.

>[!important]
>The container will have the model files in the same place they were written during training:
```
/opt/ml
`-- model
    `-- <model files>
```

### The parts of the sample container

>[!quote]
>In the `container` directory are all the components you need to package the sample algorithm for Amazon SageMager:
```
.
|-- Dockerfile
|-- build_and_push.sh
`-- decision_trees
    |-- nginx.conf
    |-- predictor.py
    |-- serve
    |-- train
    `-- wsgi.py
```

Let's discuss each of these in turn:
- **`Dockerfile`** describes how to build your Docker container image. More details below.
- **`build_and_push.sh`** is a script that uses the Dockerfile to build your container images and then pushes it to ECR. We'll invoke the commands directly later in this notebook, but you can just copy and run the script for your own algorithms.
- **`model`** is the directory which contains the files that will be installed in the container.
- **`local_test`** is a directory that shows how to test your new container on any computer that can run **Docker**, including an **Amazon SageMaker** *notebook instance*. Using this method, you can quickly iterate using small datasets to eliminate any structural bugs before you use the container with Amazon SageMaker. We'll walk through local testing later in this notebook.

>These five show the standard structure of our Python containers, although you are free to choose a different toolset and therefore could have a different layout. If you’re writing in a different programming language, you’ll certainly have a different layout depending on the frameworks and tools you choose.

The files that we’ll put in the container are:

- **``nginx.conf``** is the configuration file for the nginx front-end. Generally, you should be able to take this file as-is.
  
- **``predictor.py``** is the program that actually implements the Flask web server and the decision tree predictions for this app. You’ll want to customize the actual prediction parts to your application. Since this algorithm is simple, we do all the processing here in this file, but you may choose to have separate files for implementing your custom logic.
  
- **``serve``** is the program started when the container is started for hosting. It simply launches the gunicorn server which runs multiple instances of the Flask app defined in `predictor.py`. You should be able to take this file as-is.
  
- **``train``** is the program that is invoked when the container is run for training. You will modify this program to implement your training algorithm.
  
- **``wsgi.py``** is a small wrapper used to invoke the Flask app. You should be able to take this file as-is.
  
In summary, the two files you will probably want to change for your application are `train` and `predictor.py`.



-----------
##  Recommended Notes

- [[Amazon SageMaker Python SDK 3 Frameworks]]
- Amazon Guide on [Bring Your Own Container for distributed parallel training](https://docs.aws.amazon.com/sagemaker/latest/dg/data-parallel-use-api.html#data-parallel-bring-your-own-container).
- Docker has become very popular in the programming and devops communities for its flexibility and well-defined specification of the code to be run. It is the underpinning of many services built in the past few years, such as [Amazon ECS](https://aws.amazon.com/ecs/).
- [Docker home page](http://www.docker.com)
- [Getting started with Docker](https://docs.docker.com/get-started/)
- [Dockerfile reference](https://docs.docker.com/engine/reference/builder/)
- `` `docker run `` reference [https://docs.docker.com/engine/reference/run/](https://docs.docker.com/engine/reference/run/)



----------
##  Citations

-  [source link](https://sagemaker-examples.readthedocs.io/en/latest/advanced_functionality/scikit_bring_your_own/scikit_bring_your_own.html) for the doc
- *code package link*: [github repo](https://github.com/aws/amazon-sagemaker-examples/blob/main/advanced_functionality/scikit_bring_your_own/scikit_bring_your_own.ipynb)




