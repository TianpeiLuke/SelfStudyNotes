---
tags:
  - excerpt
  - documentation
  - code_package
  - aws/sagemaker
  - model/deploy_production
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

## Deploy PyTorch Models

- After a PyTorch Estimator has been fit, you can host the newly created model in SageMaker.
  
- After calling `fit`, you can call **`deploy`** on a **`PyTorch` Estimator** to create a SageMaker Endpoint. The Endpoint runs a SageMaker-provided PyTorch model server and hosts the model produced by your training script, which was run when you called `fit`. This was the model you saved to **`model_dir`**.
  
- `deploy` returns a **`Predictor` object**, which you can use to do inference on the Endpoint hosting your PyTorch model. Each `Predictor` provides a `predict` method which can do inference with numpy arrays or Python lists. Inference arrays or lists are *serialized* and sent to the PyTorch model server by an **`InvokeEndpoint`** *SageMaker operation*.
  
- `predict` returns the result of inference against your model. By default, the inference result a *NumPy array*.

```python
# Train my estimator
pytorch_estimator = PyTorch(entry_point='train_and_deploy.py',
                            instance_type='ml.p3.2xlarge',
                            instance_count=1,
                            framework_version='1.8.0',
                            py_version='py3')
pytorch_estimator.fit('s3://my_bucket/my_training_data/')

# Deploy my estimator to a SageMaker Endpoint and get a Predictor
predictor = pytorch_estimator.deploy(instance_type='ml.m4.xlarge',
                                     initial_instance_count=1)

# `data` is a NumPy array or a Python list.
# `response` is a NumPy array.
response = predictor.predict(data)
```

### Model Directory Structure

- In general, if you use the **same version** of PyTorch for both **training and inference** with the SageMaker Python SDK, the SDK should take care of ensuring that the contents of your `model.tar.gz` file are organized correctly.

> [!important]
> For PyTorch versions 1.2 and higher, the contents of `model.tar.gz` should be organized as follows:
> - **Model files** in the *top-level directory*
>     
> - **Inference script** (and any other **source files**) in a directory named `code/` (for more about the inference script, see [The SageMaker PyTorch Model Server](https://sagemaker.readthedocs.io/en/stable/frameworks/pytorch/using_pytorch.html#the-sagemaker-pytorch-model-server))
>     
> - *Optional* **requirements file** located at `code/requirements.txt` (for more about requirements files, see [Using third-party libraries](https://sagemaker.readthedocs.io/en/stable/frameworks/pytorch/using_pytorch.html#using-third-party-libraries))
> 
> ```txt
> model.tar.gz/
> |- model.pth
> |- code/
>   |- inference.py
>   |- requirements.txt  # only for versions 1.3.1 and higher
> ```
> In this example, `model.pth` is the model file saved from training, `inference.py` is the inference script, and `requirements.txt` is a requirements file.

- The `PyTorch` and `PyTorchModel` classes repack `model.tar.gz` to include the inference script (and related files), as long as the `framework_version` is set to 1.2 or higher.

### The SageMaker PyTorch Model Server

- The PyTorch Endpoint you create with `deploy` runs a SageMaker PyTorch model server. 

>[!quote]
> **The model server** *loads the model* that was saved by your training script and *performs inference* on the model in response to *SageMaker InvokeEndpoint API calls*.

>[!important]
> You can configure two components of the **SageMaker PyTorch model server**: **Model loading** and **model serving**. 
> - **Model loading** is the process of *deserializing* your saved model back into a PyTorch model. 
> - **Serving** is the process of translating InvokeEndpoint requests to inference calls on the loaded model.

You configure the PyTorch model server by defining functions in the Python source file you passed to the PyTorch constructor.

#### Load a Model

>[!important]
> Before a model can be served, it must be loaded. The SageMaker PyTorch model server **loads your model** by invoking a **`model_fn` function** that you must provide in your script when you are not using Elastic Inference. 

>[!info]
>The `model_fn` should have the following signature:
> ```python
> def model_fn(model_dir, context)
> ```
> - `context` is an *optional argument* that contains **additional serving information**, such as *the GPU ID and batch size*. If specified in the function declaration, the context will be created and passed to the function by SageMaker. For more information about `context`, see the [Serving Context class](https://github.com/pytorch/serve/blob/master/ts/context.py).

- SageMaker will inject the **directory** where your *model files* and **sub-directories**, saved by `save`, have been mounted. 
- Your model function should **return a model object** that can be used for *model serving*.


> [!example]
> The following code-snippet shows an example `model_fn` implementation. It loads the model parameters from a `model.pth` file in the SageMaker model directory `model_dir`. As explained in the preceding example, `context` is an optional argument that passes additional information.
> 
> ```python
> import torch
> import os
> 
> def model_fn(model_dir, context):
>     model = Your_Model()
>     with open(os.path.join(model_dir, 'model.pth'), 'rb') as f:
>         model.load_state_dict(torch.load(f))
>     return model
> ```

#### Serve a PyTorch Model

After the SageMaker model server has *loaded your model* by calling `model_fn`, SageMaker will *serve your model.* 

> [!important]
> **Model serving** is the process of *responding to inference requests*, received by SageMaker `InvokeEndpoint` API calls. The SageMaker PyTorch model server breaks request handling into **three steps**:
> 
> - **input processing**,
>     
> - **prediction**, and
>     
> - **output processing**.
> 
>In a similar way to model loading, you configure these steps by defining functions in your *Python source file*.

>[!info]
>*Each step* involves invoking a python function, with information about the *request* and *the return value from the previous function* in the **chain**. Inside the SageMaker PyTorch model server, the process looks like:
> ```python
> # Deserialize the Invoke request body into an object we can perform prediction on
> input_object = input_fn(request_body, request_content_type, context)
> 
> # Perform prediction on the deserialized object, with the loaded model
> prediction = predict_fn(input_object, model, context)
> 
> # Serialize the prediction result into the desired response content type
> output = output_fn(prediction, response_content_type, context)
> ```
> 
The above code sample shows the three function definitions:
> 
> - **`input_fn`**: Takes request data and **deserializes the data** into an *object* for prediction.
>     
> - **`predict_fn`**: Takes the *deserialized request object* and **performs inference** against the *loaded model*.
>     
> - **`output_fn`**: Takes **the result of prediction** and **serializes** this according to the *response content type*.
> 

>[!quote]
>The SageMaker PyTorch model server provides *default implementations of these functions.* You can provide your own implementations for these functions in your hosting script. If you omit any definition then the SageMaker PyTorch model server will use its default implementation for that function.

##### Process Model Input

>[!info]
>When an `InvokeEndpoint` operation is made against an *Endpoint running a SageMaker PyTorch model server*, the model server receives two pieces of information:
> 
> - **The request Content-Type**, for example “application/x-npy”
>     
> - **The request data body**, a byte array

> [!important]
> The SageMaker PyTorch model server will invoke an `input_fn` function in your **hosting script**, passing in this information. If you define an `input_fn` function definition, it should **return an object that can be passed to `predict_fn`** and have the following signature:
> 
> ```python
> def input_fn(request_body, request_content_type, context)
> ```
> - **`request_body`** is a **byte buffer**
> - **`request_content_type`** is a Python *string*.
> - `context` is an optional argument that contains additional serving information

>[!quote]
>The SageMaker PyTorch model server provides a *default implementation* of `input_fn`. This function deserializes JSON, CSV, or NPY encoded data into a torch.Tensor.

> [!example]
> The example below shows a custom `input_fn` for preparing pickled torch.Tensor.
> ```python
> import numpy as np
> import torch
> from six import BytesIO
> 
> def input_fn(request_body, request_content_type):
>     """An input_fn that loads a pickled tensor"""
>     if request_content_type == 'application/python-pickle':
>         return torch.load(BytesIO(request_body))
>     else:
>         # Handle other content-types here or raise an Exception
>         # if the content type is not supported.
>         pass
> ```

##### Get Predictions from a PyTorch Model

> [!info]
> After the inference request has been deserialized by `input_fn`, the SageMaker PyTorch model server *invokes `predict_fn`* on the *return value of `input_fn`*.

> [!important]
> The `predict_fn` function has the following signature:
> ```python
> def predict_fn(input_object, model, context)
> ```
> - **`input_object`** is the object returned from **`input_fn`**
> - **`model`** is the model loaded by **`model_fn`**. 
> - If you are using **multiple GPUs**, then specify the `context` argument, which contains information such as the GPU ID for a dynamically-selected GPU and the batch size.
> 

>[!quote]
>The default implementation of `predict_fn` invokes the loaded model’s `__call__` function on `input_object`, and returns the resulting value. The return-type should be a torch.Tensor to be compatible with the default `output_fn`.


>[!example]
>The following example shows an overridden `predict_fn`:
> ```python
> import torch
> import numpy as np
> 
> def predict_fn(input_data, model):
>     device = torch.device('cuda' if torch.cuda.is_available() else 'cpu')
>     model.to(device)
>     model.eval()
>     with torch.no_grad():
>         return model(input_data.to(device))
> ```
> 


>[!example]
> The following example is for use cases with **multiple GPUs** and shows an overridden `predict_fn` that uses the `context` argument to **dynamically select a GPU device** for making predictions:
> ```python
> import torch
> import numpy as np
> 
> def predict_fn(input_data, model, context):
>     device = torch.device("cuda:" + str(context.system_properties.get("gpu_id")) if torch.cuda.is_available() else "cpu")
>     model.to(device)
>     model.eval()
>     with torch.no_grad():
>         return model(input_data.to(device))
> ```


>[!important]
>If you implement your own prediction function, you should take care to ensure that:
> 
> - The **first** argument is expected to be the **return value from `input_fn`**. If you use the default `input_fn`, this will be a `torch.Tensor`.
>     
> - The **second** argument is the **loaded model**.
>     
> - The **return value** should be of the **correct type** to be passed as the **first argument** to **`output_fn`**. If you use the default `output_fn`, this should be a `torch.Tensor`.

##### Process Model Output

>[!info]
>*After invoking `predict_fn`*, *the model server invokes `output_fn`*, passing in *the return value* from `predict_fn` and *the content type* for the response, as specified by the `InvokeEndpoint` request.

>[!important]
>The `output_fn` has the following signature:
> ```python
> def output_fn(prediction, content_type, context)
> ```
> - `prediction` is the *result* of invoking `predict_fn` 
> - the content type for the response, as specified by *the `InvokeEndpoint` request*. The function should return **a byte array of data** serialized to `content_type`.
> - `context` is an optional argument that contains additional serving information.

>[!quote]
>The default implementation expects `prediction` to be a torch.Tensor and can serialize the result to JSON, CSV, or NPY. It accepts **response content types** of `application/json`, `text/csv`, and `application/x-npy`.





----------
##  Citations

- Amazon SageMaker Pytorch
	- [Deploy PyTorch Models](https://sagemaker.readthedocs.io/en/stable/frameworks/pytorch/using_pytorch.html#id27)
	- [The SageMaker PyTorch Model Server](https://sagemaker.readthedocs.io/en/stable/frameworks/pytorch/using_pytorch.html#id32)
- [SageMaker PyTorch Training Toolkit](https://github.com/aws/sagemaker-pytorch-training-toolkit)
- [SageMaker PyTorch Inference Toolkit](https://github.com/aws/sagemaker-pytorch-inference-toolkit)
- [Images for PyTorch](https://github.com/aws/deep-learning-containers/tree/master/pytorch)
- For more information on the default **inference handler functions**, please refer to: [SageMaker PyTorch Default Inference Handler](https://github.com/aws/sagemaker-pytorch-inference-toolkit/blob/master/src/sagemaker_pytorch_serving_container/default_pytorch_inference_handler.py).
- Amazon SageMaker Frameworks [link](https://sagemaker.readthedocs.io/en/stable/frameworks/index.html)
	- `sagemaker.pytorch.estimator.PyTorch`  [reference](https://sagemaker.readthedocs.io/en/stable/frameworks/pytorch/sagemaker.pytorch.html)
- `Estimator` class [reference](https://sagemaker.readthedocs.io/en/stable/api/training/estimators.html)
- `Predictor` class [reference](https://sagemaker.readthedocs.io/en/stable/api/inference/predictors.html)
- *code source*: [https://github.com/aws/sagemaker-python-sdk](https://github.com/aws/sagemaker-python-sdk)
- *code package link*: 

