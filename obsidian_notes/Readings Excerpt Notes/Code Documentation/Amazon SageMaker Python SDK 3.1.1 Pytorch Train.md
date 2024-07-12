---
tags:
  - excerpt
  - documentation
  - code_package
  - aws/sagemaker
  - model/training
aliases: 
keywords: 
topics:
  - code/doc
language: python
date of note: 2024-03-27
name: Amazon SageMaker Python SDK Doc
version: 
year: 2024
---


>[!quote]
> - [PyTorch](https://sagemaker.readthedocs.io/en/stable/frameworks/pytorch/index.html)
>     - [PyTorch](https://sagemaker.readthedocs.io/en/stable/frameworks/pytorch/sagemaker.pytorch.html)
>     - [Use PyTorch with the SageMaker Python SDK](https://sagemaker.readthedocs.io/en/stable/frameworks/pytorch/using_pytorch.html)

## Train a Model with PyTorch

>[!important]
>To train a PyTorch model by using the SageMaker Python SDK:
> 
> 1. [Prepare a training script](https://sagemaker.readthedocs.io/en/stable/frameworks/pytorch/using_pytorch.html#prepare-a-pytorch-training-script)
>     
> 2. [Create a `sagemaker.pytorch.PyTorch` Estimator](https://sagemaker.readthedocs.io/en/stable/frameworks/pytorch/using_pytorch.html#create-an-estimator)
>     
> 3. [Call the estimator’s `fit` method](https://sagemaker.readthedocs.io/en/stable/frameworks/pytorch/using_pytorch.html#call-the-fit-method)

### Prepare a PyTorch Training Script

- Prepare your script in a *separate source file* than the notebook, terminal session, or source file you’re using to submit the script to SageMaker via a `PyTorch` Estimator. This will be discussed in further detail below.

- The training script is very similar to a training script you might run outside of SageMaker, but you can access useful **properties** about the training environment through various environment variables. For example:
	- `SM_NUM_GPUS`: An integer representing the **number of GPUs** available to the host.
    
	- `SM_MODEL_DIR`: A string representing the path to **the directory** to write **model artifacts** to. These artifacts are uploaded to **S3** for model hosting.
    
	- `SM_OUTPUT_DATA_DIR`: A string representing the **filesystem path** to write **output artifacts** to. Output artifacts may include *checkpoints*, *graphs*, and *other files to save*, *not including model artifacts.* These artifacts are compressed and uploaded to S3 to **the same S3 prefix** as the model artifacts.
    
	- `SM_CHANNEL_XXXX`: A string that represents the path to the directory that contains the **input data** for the **specified channel**. For example, if you specify two input channels in the PyTorch estimator’s `fit` call, named ‘train’ and ‘test’, the environment variables `SM_CHANNEL_TRAIN` and `SM_CHANNEL_TEST` are set.


>[!example]
>A typical training script **loads data** from the input channels, **configures** training with **hyperparameters**, **trains a model**, and **saves a model** to `model_dir` so that it can be hosted later. 
>- **Hyperparameters** are passed to your script as **arguments** and can be retrieved with an **`argparse.ArgumentParser`** instance. For example, a training script might start with the following:
> ```python
> import argparse
> import os
> 
> if __name__ =='__main__':
> 
>     parser = argparse.ArgumentParser()
> 
>     # hyperparameters sent by the client are passed as command-line arguments to the script.
>     parser.add_argument('--epochs', type=int, default=50)
>     parser.add_argument('--batch-size', type=int, default=64)
>     parser.add_argument('--learning-rate', type=float, default=0.05)
>     parser.add_argument('--use-cuda', type=bool, default=False)
> 
>     # Data, model, and output directories
>     parser.add_argument('--output-data-dir', type=str, default=os.environ['SM_OUTPUT_DATA_DIR'])
>     parser.add_argument('--model-dir', type=str, default=os.environ['SM_MODEL_DIR'])
>     parser.add_argument('--train', type=str, default=os.environ['SM_CHANNEL_TRAIN'])
>     parser.add_argument('--test', type=str, default=os.environ['SM_CHANNEL_TEST'])
> 
>     args, _ = parser.parse_known_args()
> 
>     # ... load from args.train and args.test, train a model, write model to args.model_dir.
> ```
> 

>[!info]
>Because SageMaker **imports your training script**, you should put your training code in a main guard (`if __name__=='__main__':`) if you are using the same script to **host your model**, so that SageMaker does not inadvertently run your training code at the wrong point in execution.

#### Save the Model

- In order to save your trained PyTorch model for deployment on SageMaker, your *training script* should *save your model* to a certain filesystem path called `model_dir`. This value is accessible through the environment variable `SM_MODEL_DIR`. 
  
- The following code demonstrates how to save a trained PyTorch model named `model` as `model.pth` at the
```python
import argparse
import os
import torch

if __name__=='__main__':
    # default to the value in environment variable `SM_MODEL_DIR`. Using args makes the script more portable.
    parser.add_argument('--model-dir', type=str, default=os.environ['SM_MODEL_DIR'])
    args, _ = parser.parse_known_args()

    # ... train `model`, then save it to `model_dir`
    with open(os.path.join(args.model_dir, 'model.pth'), 'wb') as f:
        torch.save(model.state_dict(), f)
```

- After your training job is complete, SageMaker *compresses* and *uploads the serialized model to S3*, and your model data will be available in the S3 `output_path` you specified when you created the **PyTorch Estimator**.

#### Using third-party libraries

- If there are other packages you want to use with your script, you can include a `requirements.txt` file in **the same directory as your training script** to install other dependencies at runtime. Both `requirements.txt` and your training script should be put in **the same folder**. You must specify this folder in `source_dir` argument when creating PyTorch estimator.
- The function of installing packages using `requirements.txt` is supported for all PyTorch versions during **training**. 
- When **serving** a PyTorch model, support for this function varies with PyTorch versions.
- For PyTorch 1.3.1 or newer, `requirements.txt` must be under **folder `code`**. The SageMaker PyTorch Estimator will automatically save `code` in `model.tar.gz` **after training** (assuming you set up your script and `requirements.txt` correctly as stipulated in the previous paragraph).
- In the case of bringing **your own trained model** for deployment, you must **save `requirements.txt` under folder `code` in `model.tar.gz`** yourself or specify it through `dependencies`.

>[!info]
>A `requirements.txt` file is a text file that contains a list of items that are installed by using `pip install`. You can also specify the version of an item to install. For information about the format of a `requirements.txt` file, see [Requirements Files](https://pip.pypa.io/en/stable/user_guide/#requirements-files) in the pip documentation.

>[!important]
>If you were to use **your own custom Docker Image**, the **SageMaker Python SDK** and the [**SageMaker Training Toolkit**](https://github.com/aws/sagemaker-training-toolkit/) need to be installed.
>
>To do so, you can add the following lines to your `requirements.txt` file:
> ```txt
> sagemaker
> sagemaker-training
> ```

#### Deep Learning Framework-Specific SageMaker Toolkits and Containers

Framework-specific Toolkits exist. You might want to use them in your applications for framework-specific features.

>[!example]
>For Training Toolkits, see:
>- [SageMaker PyTorch Training Toolkit](https://github.com/aws/sagemaker-pytorch-training-toolkit)


>[!example]
>For Inference Toolkits, see:
>- [SageMaker PyTorch Inference Toolkit](https://github.com/aws/sagemaker-pytorch-inference-toolkit)

>[!example]
> Moreover, for more information on the container runtime environment, including specific framework versions and configurations, see [AWS Deep Learning Containers](https://github.com/aws/deep-learning-containers/)
> - [Images for PyTorch](https://github.com/aws/deep-learning-containers/tree/master/pytorch)

### Create an Estimator

- You run PyTorch training scripts on SageMaker by creating **`PyTorch` Estimators**. SageMaker training of your script is invoked when you call `fit` on a `PyTorch` Estimator.

>[!example]
>The following code sample shows how you train a custom PyTorch script `pytorch-train.py`, passing in three hyperparameters (*‘epochs’, ‘batch-size’, and ‘learning-rate’*), and using two input channel directories (*‘train’ and ‘test’*).
> ```python
> pytorch_estimator = PyTorch('pytorch-train.py',
>                             instance_type='ml.p3.2xlarge',
>                             instance_count=1,
>                             framework_version='1.8.0',
>                             py_version='py3',
>                             hyperparameters = {'epochs': 20, 'batch-size': 64, 'learning-rate': 0.1})
>                             
> pytorch_estimator.fit({'train': 's3://my-data-bucket/path/to/my/training/data',
>                        'test': 's3://my-data-bucket/path/to/my/test/data'})
> ```

- `sagemaker.pytorch.estimator.PyTorch`: Handle end-to-end training and deployment of **custom PyTorch code**. [reference](https://sagemaker.readthedocs.io/en/stable/frameworks/pytorch/sagemaker.pytorch.html)
	- This `Estimator` executes a PyTorch script in a *managed PyTorch execution environment*. 
		  
	- The managed PyTorch environment is an *Amazon-built Docker container* that **executes functions** defined in the **supplied `entry_point` Python script** within a SageMaker Training Job.
		  
	- Training is started by calling `fit()` on this Estimator. After training is complete, calling `deploy()` creates a hosted SageMaker endpoint and returns an `PyTorchPredictor` instance that can be used to perform inference against the hosted model.
	  
	- Technical documentation on preparing PyTorch scripts for SageMaker training and using the PyTorch Estimator is available on the project home-page: [https://github.com/aws/sagemaker-python-sdk](https://github.com/aws/sagemaker-python-sdk)

### Call the fit Method

- You start your training script by calling `fit` on a `PyTorch` Estimator. `fit` takes both required and optional arguments.

### Distributed PyTorch Training

- SageMaker supports the [**PyTorch DistributedDataParallel (DDP)**](https://pytorch.org/docs/master/generated/torch.nn.parallel.DistributedDataParallel.html) package. You simply need to check the variables in your training script, such as the world size and the rank of the current host, when initializing process groups for distributed training. 
- And then, launch the training job using the [`sagemaker.pytorch.estimator.PyTorch`](https://sagemaker.readthedocs.io/en/stable/frameworks/pytorch/sagemaker.pytorch.html#sagemaker.pytorch.estimator.PyTorch "sagemaker.pytorch.estimator.PyTorch") estimator class with the **`pytorchddp` option** as the **distribution strategy**.

#### Adapt Your Training Script

- To initialize distributed training in your script, call [torch.distributed.init_process_group](https://pytorch.org/docs/master/distributed.html#torch.distributed.init_process_group) with the desired **backend** and the **rank of the current host**.

```python
import torch.distributed as dist

if args.distributed:
    # Initialize the distributed environment.
    world_size = len(args.hosts)
    os.environ['WORLD_SIZE'] = str(world_size)
    host_rank = args.hosts.index(args.current_host)
    dist.init_process_group(backend=args.backend, rank=host_rank)
```

>[!info]
>SageMaker sets `'MASTER_ADDR'` and `'MASTER_PORT'` environment variables for you, but you can also overwrite them.
> **Supported backends:**
> 
> - `gloo` and `tcp` for CPU instances
> - `gloo` and `nccl` for **GPU instances** 

#### Launching a Distributed Training Job

>[!important]
>You can run multi-node distributed PyTorch training jobs using the [`sagemaker.pytorch.estimator.PyTorch`](https://sagemaker.readthedocs.io/en/stable/frameworks/pytorch/sagemaker.pytorch.html#sagemaker.pytorch.estimator.PyTorch "sagemaker.pytorch.estimator.PyTorch") estimator class. With `instance_count=1`, the estimator submits a single-node training job to SageMaker; with **`instance_count` greater than one**, a **multi-node training job** is launched.

- To run a distributed training script that adopts the [PyTorch DistributedDataParallel (DDP) package](https://pytorch.org/docs/master/generated/torch.nn.parallel.DistributedDataParallel.html), choose the **`pytorchddp`** as the distributed training option in the `PyTorch` estimator.

>[!important]
>With the `pytorchddp` option, the **SageMaker PyTorch estimator** runs a *SageMaker training container* for PyTorch, *sets up the environment for MPI*, and *launches the training job* using the **`mpirun` command** on **each worker** with the given information **during the PyTorch DDP initialization**.

>[!example]
>The following examples show how to set a PyTorch estimator to run a **distributed training job** on two `ml.p4d.24xlarge` instances.
> ```python
> from sagemaker.pytorch import PyTorch
> 
> # Using PyTorch DDP with the mpirun backend
> pt_estimator = PyTorch(
>     entry_point="train_ptddp.py",
>     role="SageMakerRole",
>     framework_version="1.12.0",
>     py_version="py38",
>     instance_count=2,
>     instance_type="ml.p4d.24xlarge",
>     distribution={
>         "pytorchddp": {
>             "enabled": True
>         }
>     }
> )
> 
> # Using PyTorch DDP with the torchrun backend
> pt_estimator = PyTorch(
>     entry_point="train_ptddp.py",
>     role="SageMakerRole",
>     framework_version="1.13.1",
>     py_version="py38",
>     instance_count=2,
>     instance_type="ml.p4d.24xlarge",
>     distribution={
>         "torch_distributed": {
>             "enabled": True
>         }
>     }
> )
> ```

#### Choose Launcher Option

>[!info]
> The following **launcher options** are available for launching **PyTorch distributed training**. [reference](https://docs.aws.amazon.com/sagemaker/latest/dg/data-parallel-use-api.html)
> 
> - **`pytorchddp`** – This option runs **`mpirun`** and **sets up environment variables** needed for running PyTorch distributed training on SageMaker. To use this option, pass the following dictionary to the **`distribution` parameter**.
> ```python
> { "pytorchddp": { "enabled": True } }
> ```
> 
> - **`torch_distributed`** – This option runs **`torchrun`** and **sets up environment variables** needed for running PyTorch distributed training on SageMaker. To use this option, pass the following dictionary to the `distribution` parameter.
> ```python
> { "torch_distributed": { "enabled": True } }
> ```
> 
> - **`smdistributed`** – This option also runs **`mpirun`** but with **`smddprun`** that **sets up environment variables** needed for running PyTorch distributed training on SageMaker.
> ```python
> { "smdistributed": { "dataparallel": { "enabled": True } } }
> ```


>[!quote]
>- If you chose to replace **NCCL `AllGather`** to **SMDDP `AllGather`**, you can use *all three options*. Choose one option that fits with your use case.
>  
>- If you chose to replace **NCCL `AllReduce`** with **SMDDP `AllReduce`**, you should choose one of the **`mpirun`**-based options: **`smdistributed`** or **`pytorchddp`**. 

You can also add additional MPI options as follows.
```python
{ 
    "pytorchddp": {
        "enabled": True, 
        "custom_mpi_options": "-verbose -x NCCL_DEBUG=VERSION"
    }
}
```
or 
```python
{ 
    "smdistributed": { 
        "dataparallel": {
            "enabled": True, 
            "custom_mpi_options": "-verbose -x NCCL_DEBUG=VERSION"
        }
    }
}
```

>[!important]
>Considerations for activating SMDDP collective operations and using the right distributed training launcher options
> - SMDDP `AllReduce` and SMDDP `AllGather` are **not mutually compatible** at present.
>     
> - SMDDP `AllReduce` is **activated by default** when using `smdistributed` or `pytorchddp`, which are `mpirun`-based launchers, and NCCL `AllGather` is used.
>     
> - SMDDP `AllGather` is **activated by default** when using `torch_distributed` launcher, and `AllReduce` falls back to NCCL.
>     
> - SMDDP `AllGather` can **also be activated** when using the `mpirun`-based launchers with an additional environment variable set as follows.
> ```bash
> export SMDATAPARALLEL_OPTIMIZE_SDP=true
> ```


- Check details on `AllGather` and `AllReduce` operations in [[Amazon SageMaker distributed data parallelism library]]

-----
##  Citations

- Amazon SageMaker - [Use PyTorch with the SageMaker Python SDK](https://sagemaker.readthedocs.io/en/stable/frameworks/pytorch/using_pytorch.html)
- [SageMaker PyTorch Training Examples](https://sagemaker-examples.readthedocs.io/en/latest/training/frameworks.html#pytorch)
- [SageMaker Distributed Training Examples](https://sagemaker-examples.readthedocs.io/en/latest/training/distributed_training/index.html)
- [Pytorch Lightning on SageMaker](https://docs.aws.amazon.com/sagemaker/latest/dg/data-parallel-modify-sdp-pt-lightning.html)
- [SageMaker PyTorch Training Toolkit](https://github.com/aws/sagemaker-pytorch-training-toolkit)
- [SageMaker PyTorch Inference Toolkit](https://github.com/aws/sagemaker-pytorch-inference-toolkit)
- [Images for PyTorch](https://github.com/aws/deep-learning-containers/tree/master/pytorch)
- [Deep Learning Container (DLC) Dockerfiles for PyTorch](https://github.com/aws/deep-learning-containers/tree/master/pytorch)
- [Deep Learning Container (DLC) Images](https://docs.aws.amazon.com/deep-learning-containers/latest/devguide/deep-learning-containers-images.html)
- Check on [doc](https://docs.aws.amazon.com/sagemaker/latest/dg/data-parallel-use-api.html) for launching distributed training job using Sagemaker SDK
- Data Parallelism using SageMaker API [link](https://docs.aws.amazon.com/sagemaker/latest/dg/data-parallel-use-api.html)
- [PyTorch DistributedDataParallel (DDP)](https://pytorch.org/docs/master/generated/torch.nn.parallel.DistributedDataParallel.html)
- For more information about setting up PyTorch DDP in your training script, see [Getting Started with Distributed Data Parallel](https://pytorch.org/tutorials/intermediate/ddp_tutorial.html) in the PyTorch documentation.
- For more information about setting up `torchrun` in your training script, see [torchrun (Elastic Launch)](https://pytorch.org/docs/stable/elastic/run.html) in _the PyTorch documentation_.
- Amazon SageMaker Frameworks [link](https://sagemaker.readthedocs.io/en/stable/frameworks/index.html)
	- `sagemaker.pytorch.estimator.PyTorch`  [reference](https://sagemaker.readthedocs.io/en/stable/frameworks/pytorch/sagemaker.pytorch.html)
- `Estimator` class [reference](https://sagemaker.readthedocs.io/en/stable/api/training/estimators.html)
- [PyTorch Training Examples](https://github.com/awslabs/amazon-sagemaker-examples/tree/master/sagemaker-python-sdk)
- *code source*: [https://github.com/aws/sagemaker-python-sdk](https://github.com/aws/sagemaker-python-sdk)
- *code package link*: 

