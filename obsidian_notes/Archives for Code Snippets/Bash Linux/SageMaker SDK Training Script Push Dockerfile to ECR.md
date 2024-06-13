---
tags:
  - code
  - code_snippet
  - aws/sagemaker
  - model/training
  - docker
keywords: 
topics:
  - Dockerfile writting
language: bash
date of note: 2024-03-27
---

## Code Snippet Summary

>[!important] 
>The following code build and push docker file to Amazon ECR. It contains three parts:
>- **Prepare** names and **retrieve** account information from *AWS CLI*
>- **Create** container repository in **Amazon ECR** if it does not exists in ECR
>- **Authenticate** ECR login with Docker
>- **Build** *Docker image* locally 
>- **Push** it to *Amazon ECR*

## Background Knowledge
### Location of Dockerfile and the `build_and_push` file

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


- **`Dockerfile`** describes how to build your Docker container image. More details below.
- **`build_and_push.sh`** is a script that uses the Dockerfile to build your container images and then pushes it to ECR. We'll invoke the commands directly later in this notebook, but you can just copy and run the script for your own algorithms.

### The Dockerfile

- The **Dockerfile** *describes the image that we want to build*. You can think of it as describing the *complete operating system installation* of the system that you want to run. A Docker container running is quite a bit lighter than a full operating system, however, because it takes advantage of Linux on the host machine for the basic operations.

### Building and registering the container

- The following shell code shows how to build the container image using `docker build` and push the container image to [ECR](https://aws.amazon.com/ecr/) using `docker push`. This code is also available as the shell script `container/build-and-push.sh`, which you can run as `build-and-push.sh decision_trees_sample` to build the image `decision_trees_sample`.

## Code

This code looks for an ECR repository in the account you’re using and the current default region (if you’re using a SageMaker notebook instance, this will be the region where the notebook instance was created). If the repository doesn’t exist, the script will create it.

```bash
%%sh

# The name of our algorithm
algorithm_name=sagemaker-decision-trees

cd container

chmod +x decision_trees/train
chmod +x decision_trees/serve

account=$(aws sts get-caller-identity --query Account --output text)

# Get the region defined in the current configuration (default to us-west-2 if none defined)
region=$(aws configure get region)
region=${region:-us-west-2}

fullname="${account}.dkr.ecr.${region}.amazonaws.com/${algorithm_name}:latest"

# If the repository doesn't exist in ECR, create it.
aws ecr describe-repositories --repository-names "${algorithm_name}" > /dev/null 2>&1

if [ $? -ne 0 ]
then
    aws ecr create-repository --repository-name "${algorithm_name}" > /dev/null
fi

# Get the login command from ECR and execute it directly
aws ecr get-login-password --region ${region}|docker login --username AWS --password-stdin ${fullname}

# Build the docker image locally with the image name and then push it to ECR
# with the full name.

docker build -t ${algorithm_name} .
docker tag ${algorithm_name} ${fullname}

docker push ${fullname}
```


## Interpretation

This script can be decomposed into three parts:
### Prepare and Retrieve Information

>[!important]
>- Define the name of algorithm `algorithm_name`
>- Make `train` and `serve` executable
>- Retrieve account id, region with [**AWS CLI**](https://aws.amazon.com/cli/) `aws`
>- Define full name (**registry URL**) of *ECR repository* `fullname` [^1]


```bash
%%sh

# The name of our algorithm
algorithm_name=sagemaker-decision-trees

cd container

chmod +x decision_trees/train
chmod +x decision_trees/serve

account=$(aws sts get-caller-identity --query Account --output text)

# Get the region defined in the current configuration (default to us-west-2 if none defined)
region=$(aws configure get region)
region=${region:-us-west-2}

fullname="${account}.dkr.ecr.${region}.amazonaws.com/${algorithm_name}:latest"
```

- `aws sts`: *Security Token Service (STS)* enables you to request temporary, limited-privilege credentials for users.  [reference](https://docs.aws.amazon.com/cli/latest/reference/sts/)
	- `aws sts get-caller-identity`: Returns details about the IAM user or role whose credentials are used to call the operation.
- `aws configure`: Configure AWS CLI options.  [reference](https://docs.aws.amazon.com/cli/latest/reference/configure/)
	- The following configuration variables are supported in the config file:
		- **aws_access_key_id** - The AWS access key part of your credentials
		- **aws_secret_access_key** - The AWS secret access key part of your credentials
		- **aws_session_token** - The session token part of your credentials (session tokens only)
		- **metadata_service_timeout** - The number of seconds to wait until the metadata service request times out. This is used if you are using an IAM role to provide your credentials.
		- **metadata_service_num_attempts** - The number of attempts to try to retrieve credentials. If you know for certain you will be using an IAM role on an Amazon EC2 instance, you can set this value to ensure any intermittent failures are retried. By default this value is 1.
	- `aws configure get`: Get a configuration value from the config file. [reference](https://docs.aws.amazon.com/cli/latest/reference/configure/get.html)


### Create Container Repository in ECR and Authenticate with Docker

>[!important]
>- Check if there exists repository in ECR with the same `algorithm_name`
>- If no, then **create a new repository** in ECR using given `algorithm_name`
>- **Retrieve** the *login password* for the ECR registry and uses it to **authenticate** with Docker, allowing subsequent Docker commands to *interact with the ECR registry*.

```bash
# If the repository doesn't exist in ECR, create it.
aws ecr describe-repositories --repository-names "${algorithm_name}" > /dev/null 2>&1

if [ $? -ne 0 ]
then
    aws ecr create-repository --repository-name "${algorithm_name}" > /dev/null
fi

# Get the login command from ECR and execute it directly
aws ecr get-login-password --region ${region}|docker login --username AWS --password-stdin ${fullname}
```

- `aws ecr`: *Amazon Elastic Container Registry (Amazon ECR)* is a managed container image registry service. Customers can use the familiar Docker CLI, or their preferred client, to push, pull, and manage images. [reference](https://docs.aws.amazon.com/cli/latest/reference/ecr/)
	- `aws ecr describe-repositories`: Describes image repositories in a registry. [reference](https://docs.aws.amazon.com/cli/latest/reference/ecr/describe-repositories.html)
		- `--repository-names`: A list of repositories to describe. If this parameter is omitted, then all repositories in a registry are described.
	- `aws ecr create-repository`: **Creates a repository**. [reference](https://docs.aws.amazon.com/cli/latest/reference/ecr/create-repository.html)
	- `aws ecr get-login-password`: **To log in to an Amazon ECR registry**. This command *retrieves and displays an authentication token* using the GetAuthorizationToken API that you can use to **authenticate to an Amazon ECR registry**. You can *pass* the authorization token to the *login command* of the *container client* of your preference, such as the **Docker CLI**. [reference](https://docs.aws.amazon.com/cli/latest/reference/ecr/get-login-password.html)

- `docker login`: Log in to a registry.  [reference](https://docs.docker.com/reference/cli/docker/login/)
	- `--username`: 
	- `--password-stdin`: Take the password from stdin.


#### Check if repo exists in ECR

>[!example] 
> ```bash
> aws ecr describe-repositories --repository-names "${algorithm_name}" > /dev/null 2>&1
> ```
> 
> - `> /dev/null`: This part of the command redirects the **standard output (stdout) to `/dev/null`**, which is a *special file* that **discards all data written to it**. In other words, it ***suppresses the output of the command***.
> - `2>&1`: This is a redirection operator that redirects the *standard error (stderr)* to the *same destination* as the *standard output (stdout)*. In this case, it **redirects the error output to `/dev/null` as well.**
> 	- `2>` redirects the **standard error (file descriptor 2)** to a file.
> 	- `&1` refers to **the file descriptor 1**, which represents *the standard output.*
> 	  
>>[!summary]	  
>> In summary, this command attempts to describe the repository with the name specified by `${algorithm_name}` in AWS ECR. However, it discards both the standard output and standard error by redirecting them to `/dev/null`. This means that any output or error messages generated by the command will be suppressed and not displayed in the console.

>[!important]
>This command is often used to check if a repository exists in ECR without displaying any output. The exit status of the command can be used to determine if the repository was found or not.

- [[Save Standard Output and Standard Error to files]]
#### Check the exit status of ECR check and Create repo if not exist

>[!example]
> ```bash
> if [ $? -ne 0 ]
> then
>     aws ecr create-repository --repository-name "${algorithm_name}" > /dev/null
> fi
> ```
> - `if [ $? -ne 0 ]`:
> 	- This is a shell conditional statement that **checks the exit status** of *the previous command.*
> 	- `$?` is a **special variable** that holds the exit status of the last executed command.
> 	- `-ne 0` means "not equal to zero." In shell scripting, an exit status of 0 typically indicates success, while a non-zero value indicates an error or failure.
> 	- So, this condition checks if the previous command (`aws ecr describe-repositories`) failed, meaning the specified repository does not exist.
> - `then aws ecr create-repository --repository-name "${algorithm_name}" > /dev/null`:
> 	- If the condition in step 2 is true (i.e., the repository does not exist), this block of code is executed.
> 	- It uses the AWS CLI to create a new repository in ECR with the specified repository name stored in the variable `${algorithm_name}`.
> 	- Similar to step 1, the `> /dev/null` part discards any output from the command.
> - `if [] then fi` is *if-else-then statement* in **bash shell**. 
>  
>>[!summary] 
>> In summary, this code snippet checks if a repository with the specified name exists in Amazon ECR. *If the repository does not exist* (i.e., the `describe-repositories` command *fails*), it **creates a new repository with that name.** The *output* of the commands is *discarded* by redirecting it to `/dev/null`.

>[!important]
>This code is commonly used in scenarios where you want to ensure that a specific repository exists in ECR before proceeding with further actions, such as pushing Docker images to that repository.

#### Retrieve Password from ECR and Authenticate with Docker

>[!example]
> ```bash
> # Get the login command from ECR and execute it directly
> aws ecr get-login-password --region ${region}|docker login --username AWS --password-stdin ${fullname}
> ```
> - This command retrieves the *login password* for Amazon ECR using the AWS CLI in the specified region stored in `${region}`.
> - The retrieved password is then piped (`|`) to the `docker login` command.
> - The `docker login` command **logs in to the Docker registry** using the provided username "AWS" and *the password* obtained from the previous command.
> 	- The `--password-stdin` flag indicates that *the password* is being provided through *the standard input*.
> 	  
>>[!summary]
>> In summary, this code snippet retrieves the login password for the ECR registry and uses it to **authenticate with Docker**, allowing *subsequent Docker commands to interact with the ECR registry*.


### Build Docker Image Locally and Push it to ECR

>[!important]
>- **Build Docker Image** with name `algorithm_name` in local environment
>- **Tag** the built image `algorithm_name` with a full name that includes the registry and repository details. 
>- **Push** the tagged local image to Amazon ECR, making it available for others to pull and use.

```bash
# Build the docker image locally with the image name and then push it to ECR
# with the full name.

docker build -t ${algorithm_name} .
docker tag ${algorithm_name} ${fullname}

docker push ${fullname}
```

- `docker build`: The `docker build` command builds **Docker images** from a **Dockerfile** and a "context". [reference](https://docs.docker.com/reference/cli/docker/image/build/)
	- `-t, --tag`: Name and optionally a tag in the `name:tag` format. In this context, the `${algorithm_name}` is the desired name for the 
	- `.`  (current directory) as `PATH` which store *Dockerfile*. A build's context is the set of files located in the specified `PATH` or `URL`. The build process can refer to any of the files in the context.
	- This command builds a *Docker image* using the **Dockerfile** present in the current directory (denoted by `.`).
	  
- `docker tag`:
	- This command creates an additional tag for the Docker image built in the previous step.
	- It associates the image tagged as `${algorithm_name}` with another tag specified by `${fullname}`.
	  
- `docker push`: Use `docker image push` to share your images to the [Docker Hub](https://hub.docker.com) registry or to a self-hosted one.  [reference](https://docs.docker.com/reference/cli/docker/image/push/)
	- This command pushes the *Docker image* tagged with `${fullname}` to a container registry.
	- `${fullname}` should match the tag assigned in the previous `docker tag` command.
	- Pushing the image to a *registry* allows others to *access and pull the image* from the registry.


-----------
##  Recommended Notes

- [[SageMaker BYO Container Entry point]]
- [[Amazon SageMaker Example Building Your Own Container 1 Docker]]
- [Amazon Elastic Container Registry (ECR)](https://aws.amazon.com/ecr/)
- [AWS Command Line Interface (CLI)](https://aws.amazon.com/cli/)
- [AWS CLI Command Reference](https://docs.aws.amazon.com/cli/latest/)
- [Docker CLI Reference](https://docs.docker.com/reference/cli/docker/)

[^1]: [Amazon ECR private registry](https://docs.aws.amazon.com/AmazonECR/latest/userguide/Registries.html)
