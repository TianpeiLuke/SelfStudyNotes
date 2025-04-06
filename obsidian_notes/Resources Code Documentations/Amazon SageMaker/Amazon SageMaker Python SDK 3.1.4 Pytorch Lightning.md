---
tags:
  - excerpt
  - documentation
  - code_package
  - aws/sagemaker
  - pytorch/lightning
aliases: 
keywords: 
topics:
  - code/doc
language: python
date of note: 2024-03-31
name: Amazon SageMaker Python SDK Doc
version: 
year: 2024
---
## Use the SMDDP library in your PyTorch Lightning training script

> [!important]
> - If you want to bring your [PyTorch Lightning](https://pytorch-lightning.readthedocs.io/en/latest/starter/introduction.html) training script and run a *distributed data parallel training job* in SageMaker, you can run the training job with minimal changes in your training script. 
>   
> - The necessary changes include the following: 
> 	- import the **`smdistributed.dataparallel` library**’s PyTorch modules, 
> 	- **set up the environment variables** for PyTorch Lightning to accept the SageMaker environment variables that are preset by the SageMaker training toolkit, and 
> 	- *activate* the **SMDDP library** by setting **the process group backend** to **`"smddp"`.**
> 	  
>--  [Pytorch Lightning on SageMaker](https://docs.aws.amazon.com/sagemaker/latest/dg/data-parallel-modify-sdp-pt-lightning.html)

>[!example]
>To learn more, walk through the following instructions that break down the steps with code examples.
- Import the `pytorch_lightning` library and the `smdistributed.dataparallel.torch` modules.
   
```python
import lightning as pl
import smdistributed.dataparallel.torch.torch_smddp
```

- Instantiate the [LightningEnvironment](https://pytorch-lightning.readthedocs.io/en/stable/api/pytorch_lightning.plugins.environments.LightningEnvironment.html)
   
```python
from lightning.fabric.plugins.environments.lightning import LightningEnvironment

env = LightningEnvironment()
env.world_size = lambda: int(os.environ["WORLD_SIZE"])
env.global_rank = lambda: int(os.environ["RANK"])
```

- **For PyTorch DDP** – Create an object of the **[DDPStrategy](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.strategies.DDPStrategy.html) class** with **`"smddp"`** for **`process_group_backend`** and `"gpu"` for `accelerator`, and pass that to the [Trainer](https://pytorch-lightning.readthedocs.io/en/stable/common/trainer.html) class.
   
```python
import lightning as pl
from lightning.pytorch.strategies import DDPStrategy

ddp = DDPStrategy(
    cluster_environment=env, 
    process_group_backend="smddp", 
    accelerator="gpu"
)

trainer = pl.Trainer(
    max_epochs=200, 
    strategy=ddp, 
    devices=num_gpus, 
    num_nodes=num_nodes
)
```

- **For PyTorch FSDP** – Create an object of the [FSDPStrategy](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.strategies.FSDPStrategy.html) class (with [**wrapping policy**](https://pytorch.org/docs/stable/fsdp.html) of choice) with `"smddp"` for `process_group_backend` and `"gpu"` for `accelerator`, and pass that to the [Trainer](https://pytorch-lightning.readthedocs.io/en/stable/common/trainer.html) class.

```python
import lightning as pl
from lightning.pytorch.strategies import FSDPStrategy

from functools import partial
from torch.distributed.fsdp.wrap import size_based_auto_wrap_policy

policy = partial(
    size_based_auto_wrap_policy, 
    min_num_params=10000
)

fsdp = FSDPStrategy(
    auto_wrap_policy=policy,
    process_group_backend="smddp", 
    cluster_environment=env
)

trainer = pl.Trainer(
    max_epochs=200, 
    strategy=fsdp, 
    devices=num_gpus, 
    num_nodes=num_nodes
)
```

After you have completed adapting your training script, proceed to [Step 2: Launch a distributed training job using the SageMaker Python SDK](https://docs.aws.amazon.com/sagemaker/latest/dg/data-parallel-use-api.html).


### The dependencies for Pytorch Lightning

>[!info]
>- **PyTorch Lightning** and its utility libraries such as **Lightning Bolts** are not preinstalled in the *SageMaker PyTorch DLCs*.
>- When you construct a SageMaker PyTorch estimator and submit a training job request in [Step 2: Launch a distributed training job using the SageMaker Python SDK](https://docs.aws.amazon.com/sagemaker/latest/dg/data-parallel-use-api.html), you need to provide `requirements.txt` to install `pytorch-lightning` and `lightning-bolts` in the SageMaker PyTorch training container.
> ```txt
> # requirements.txt
> pytorch-lightning
> lightning-bolts
> ```
> For example, the tree-structured directory should look like the following.
> ```txt
> ├── pytorch_training_launcher_jupyter_notebook.ipynb
> └── sub-folder-for-your-code
>     ├──  adapted-training-script.py
>     └──  requirements.txt
> ```
> 


- For more information about specifying the source directory to place the `requirements.txt` file along with your training script and a job submission, see [[Amazon SageMaker Python SDK 3.1.2 Pytorch Deploy and Hosting]]. 






----------
##  Citations

- [Pytorch Lightning on SageMaker](https://docs.aws.amazon.com/sagemaker/latest/dg/data-parallel-modify-sdp-pt-lightning.html)
- Check distributed training strategies in Pytorch Lightning in [[Pytorch Lightning 5 Distributed Training Strategies]]
- [SageMaker PyTorch Training Toolkit](https://github.com/aws/sagemaker-pytorch-training-toolkit)
- [SageMaker PyTorch Inference Toolkit](https://github.com/aws/sagemaker-pytorch-inference-toolkit)
- [Images for PyTorch](https://github.com/aws/deep-learning-containers/tree/master/pytorch)
- For more information on the default **inference handler functions**, please refer to: [SageMaker PyTorch Default Inference Handler](https://github.com/aws/sagemaker-pytorch-inference-toolkit/blob/master/src/sagemaker_pytorch_serving_container/default_pytorch_inference_handler.py).
- Amazon SageMaker Frameworks [link](https://sagemaker.readthedocs.io/en/stable/frameworks/index.html)
	- `sagemaker.pytorch.estimator.PyTorch`  [reference](https://sagemaker.readthedocs.io/en/stable/frameworks/pytorch/sagemaker.pytorch.html)
	- `sagemaker.pytorch.model.PyTorchModel` [reference](https://sagemaker.readthedocs.io/en/stable/frameworks/pytorch/sagemaker.pytorch.html#pytorch-model)
- `Estimator` class [reference](https://sagemaker.readthedocs.io/en/stable/api/training/estimators.html)
- `Predictor` class [reference](https://sagemaker.readthedocs.io/en/stable/api/inference/predictors.html)
- *code source*: [https://github.com/aws/sagemaker-python-sdk](https://github.com/aws/sagemaker-python-sdk)
- *code package link*: 

