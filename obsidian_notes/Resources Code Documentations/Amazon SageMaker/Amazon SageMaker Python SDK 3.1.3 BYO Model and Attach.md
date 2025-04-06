---
tags:
  - excerpt
  - documentation
  - code_package
  - aws/sagemaker
  - model/deploy_production
  - bring_your_own
  - container
aliases: 
keywords: 
topics:
  - code/doc
language: python
date of note: 2024-03-30
name: Amazon SageMaker Python SDK Doc
version: 
year: 2024
---


>[!quote]
> - [PyTorch](https://sagemaker.readthedocs.io/en/stable/frameworks/pytorch/index.html)
>     - [PyTorch](https://sagemaker.readthedocs.io/en/stable/frameworks/pytorch/sagemaker.pytorch.html)
>     - [Use PyTorch with the SageMaker Python SDK](https://sagemaker.readthedocs.io/en/stable/frameworks/pytorch/using_pytorch.html)

## Bring your own model

> [!important]
> You can deploy a PyTorch model that you trained outside of SageMaker by using the **`PyTorchModel` class**. Typically, you save a PyTorch model as a file with extension `.pt` or `.pth`. To do this, you need to:
> 
> - **Write an inference script**.
>     
> - Create the **directory structure** for your **model files**.
>     
> - Create the **`PyTorchModel` object**.
> 

### Write an inference script

>[!important]
>You must create an **inference script** that implements (*at least*) the `model_fn` function that *calls the loaded model to get a prediction*.

> [!important]
> Optionally, you can also implement `input_fn` and `output_fn` to *process input* and *output*, and `predict_fn` to *customize* how the **model server** gets *predictions from the loaded model*.

- See [[Amazon SageMaker Python SDK 3.1.2 Pytorch Deploy and Hosting]] for `input_fn`, `predict_fn`, `output_fn`
  
- Save the *inference script* in the **same folder** where you saved your *PyTorch model*. Pass the *filename of the inference script* as the **`entry_point` parameter** when you create the `PyTorchModel` object.

### Create the directory structure for your model files

>[!info]
>You have to create a **directory structure** and place your model files in the *correct location*. The `PyTorchModel` constructor *packs the files into a `tar.gz` file* and *uploads* it to S3.

> [!important]
> The **directory structure** where you saved your PyTorch model should look something like the following:
> ```txt
> |   my_model
> |           |--model.pth
> |
> |           code
> |               |--inference.py
> |               |--requirements.txt
> ```
> Where `requirements.txt` is an optional file that specifies **dependencies** on third-party libraries.

### Create a `PyTorchModel` object

> [!info]
> Now call the **[`sagemaker.pytorch.model.PyTorchModel`](https://sagemaker.readthedocs.io/en/stable/frameworks/pytorch/sagemaker.pytorch.html#sagemaker.pytorch.model.PyTorchModel "sagemaker.pytorch.model.PyTorchModel") constructor** to create a model object, and then call its `deploy()` method to deploy your model for inference.

>[!example]
> ```python
> from sagemaker import get_execution_role
> role = get_execution_role()
> 
> pytorch_model = PyTorchModel(model_data='s3://my-bucket/my-path/model.tar.gz', 
> 						  role=role,
>                           entry_point='inference.py')
> 
> predictor = pytorch_model.deploy(instance_type='ml.c4.xlarge', initial_instance_count=1)
> ```
> Now you can call the `predict()` method to get predictions from your deployed model.


## Attach an estimator to an existing training job

>[!info]
>You can attach a **PyTorch Estimator** to an *existing training job* using the `attach` method.
> ```python
> my_training_job_name = 'MyAwesomePyTorchTrainingJob'
> pytorch_estimator = PyTorch.attach(my_training_job_name)
> ```
> 

The `attach` method accepts the following arguments:
- `training_job_name:` The name of the training job to attach to.
- `sagemaker_session:` The Session used to interact with SageMaker




----------
##  Citations

- Amazon SageMaker Pytorch
	- [Bring your own model](https://sagemaker.readthedocs.io/en/stable/frameworks/pytorch/using_pytorch.html#id38)
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

