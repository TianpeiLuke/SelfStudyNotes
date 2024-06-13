---
tags:
  - code
  - code_snippet
  - aws/sagemaker
  - model/deploy_production
  - model/prediction
keywords: 
topics: 
language: python
date of note: 2024-03-28
---

## Code Snippet Summary

>[!important] Highlight
>The task to host model on SageMaker for real-time prediction:
>- **deploy** the model.
>- choose data for **prediction**
>- **clean up**, i.e. *delete endpoint* and *delete model resources*
>
>-- [link](https://sagemaker-examples.readthedocs.io/en/latest/advanced_functionality/scikit_bring_your_own/scikit_bring_your_own.html#Hosting-your-model) 


### Prerequisite: get model 

#### Using trained estimator

[[SageMaker SDK Training via Training API]]

#### Attached to other trained estimator

```python
from sagemaker.estimator import Estimator

# create an estimator instance by attaching to an existing training job
training_job_name="xxxx"

estimator = Estimator.attach(training_job_name,													sagemaker_session=session)
```

- `sagemaker.estimator.Estimator`:  [reference](https://sagemaker.readthedocs.io/en/stable/api/training/estimators.html#sagemaker.estimator.Estimator)
	- `attach()`: Attach to an existing training job.  [reference](https://sagemaker.readthedocs.io/en/stable/api/training/estimators.html#sagemaker.estimator.Estimator.attach)
		- Create an Estimator bound to an existing training job. 
		- After attaching, if the training job has a Complete status, it can be `deploy()` ed to create a SageMaker Endpoint and return a `Predictor`.

#### Create Model from existing S3 bucket

```python
from sagemaker.model import Model 

# create model using s3 bucket and docker image URI

image = ...
model_data = "s3://{}.."
model = Model(model_data=model_data,
			  role=sagemaker.get_execution_role(),
			  image_uri=image
			  )


# create model based on existing estimator object
model = Model(model_data=estimator.model_data,
			  role=sagemaker.get_execution_role(),
			  image_uri=estimator.image_name
			  )
```

- `sagemaker.model.Model`: A SageMaker `Model` that can be deployed to an `Endpoint`. [reference](https://sagemaker.readthedocs.io/en/stable/api/inference/model.html)
	- **`image_uri`**: A Docker image URI.
	- **`model_data`**: Location of SageMaker model data. 
	- **`role`**: An AWS IAM role (either name or full ARN). The Amazon SageMaker training jobs and APIs that create Amazon SageMaker endpoints use this role to access training data and model artifacts. 
	- **`sagemaker_session`**: A SageMaker Session object, used for SageMaker interactions.
	  
	- `source_dir`: The absolute, relative, or S3 URI Path to a directory with any other training source code dependencies aside from the entry point file.
	- `name`: The model name.
	- `entry_point`:  The absolute or relative path to the local Python source file that should be executed as the entry point to model hosting.
	- `code_location`: Name of the S3 bucket where custom code is uploaded.
	  
	- `predictor_cls`: A function to call to create a **predictor**. If not None, `deploy` will return the result of invoking this function on the created endpoint name.

### Data Input from DataFrame

```python
from io import StringIO
import pandas as pd

df = pd.read_csv('data.tsv', sep='\t', index_col=None)

input_str = test.drop(['label'], axis=1).to_csv(header=None, sep=',', index=False).strip('\n').split('\n')

data = pd.read_csv(StringIO(input_str[:]), index_col=None)
```

- For `text/csv`, the value for the Body argument to `invoke_endpoint()` should be a string with commas separating the values for each feature. For example, a record for a model with four features might look like `1.5,16.0,14,23.0`. Any transformations performed on the training data should also be performed on the data before obtaining inference. The order of the features matters and must remain unchanged.
- `application/json` is significantly more flexible and provides multiple possible formats for developers to use in their applications.

## Code

### Deploy the model

- Deploying the model to SageMaker hosting just requires a **`deploy` call** on the fitted model. This call takes an instance count, instance type, and optionally serializer and deserializer functions. These are used when the *resulting predictor* is created on the endpoint.

```python
from sagemaker.serializers import CSVSerializer
from sagemaker.predictor import Predictor

# deploy via Model object
endpoint_name = '...'
predictor = model.deploy(initial_instance_count=1,
						 instance_type='ml.m5.4xlarge',
						 serializer=CSVSerializer,
						 endpoint_name=endpoint_name,
						 predictor_cls=Predictor
						)

# deploy via Estimator object
predictor = estimator.deploy(initial_instance_count=1,
						     instance_type='ml.m5.4xlarge',
							 serializer=CSVSerializer,
							 endpoint_name=endpoint_name
			)

```

- `sagemaker.estimator.Estimator.deploy()`: Deploy the trained model to an Amazon SageMaker endpoint. And then return `sagemaker.Predictor` object. [reference](https://sagemaker.readthedocs.io/en/stable/api/training/estimators.html#sagemaker.estimator.Estimator.deploy)
	- **`initial_instance_count`**: The initial number of instances to run in the `Endpoint` created from this `Model`.
	- **`instance_type`**: The **EC2 instance** type to deploy this Model to.
	- **`serializer`**: A serializer object, used to encode data for an inference endpoint.
	- **`deserializer`**: A deserializer object, used to decode data from an inference endpoint.
	  
	- `endpoint_name`: **Name** to use for creating an Amazon SageMaker **endpoint**. If not specified, the *name of the training job* is used.
	- `model_name`: Name to use for creating an Amazon SageMaker model. If not specified, the estimator generates a default job name based on the training image name and current timestamp.
	  
	- `model_data_download_timeout`: The timeout value, in seconds, to download and extract model data from Amazon S3 to the individual inference instance associated with this production variant.
	- `container_startup_health_check_timeout`:  The timeout value, in **seconds**, for your inference container to pass health check by SageMaker Hosting. See [reference](https://docs.aws.amazon.com/sagemaker/latest/dg/your-algorithms-inference-code.html#your-algorithms-inference-algo-ping-requests) 
	  
	  
- `sagemaker.model.Model.deploy()`: Deploy this `Model` to an `Endpoint` and *optionally* return a `Predictor`.  [reference](https://sagemaker.readthedocs.io/en/stable/api/inference/model.html#sagemaker.model.Model.deploy)
	- Create a SageMaker `Model` and `EndpointConfig`, and deploy an `Endpoint` from this `Model`. If `self.predictor_cls` is not None, this method returns the result of invoking `self.predictor_cls` on the created endpoint name.
	- The name of the created *model* is accessible in the `name` field of this `Model` after deploy returns.
	- The name of the created *endpoint* is accessible in the `endpoint_name` field of this `Model` after deploy returns.
	- Parameters are similar as above, except for `model_name` field, which can be accessed via the `Model` object that calls this method.
	  
	- If `self.predictor_cls` is `None`, return `None`.
	- if `self.predictor_cls` is not `None`,  return the invocation of `self.predictor_cls`. In this time, we can use **Predictor** class from `sagemaker.predictor`.

### Use Predictor to Test Result

- Prediction is as easy as **calling predict** with the **predictor** we got back from deploy and the data we want to do predictions with. The serializers take care of doing the data conversions for us.

```python
response = predictor.predict(test_data.values).decode("utf-8")
```

- `sagemaker.predictor.Predictor`: Make prediction requests to an Amazon SageMaker endpoint. [reference](https://sagemaker.readthedocs.io/en/stable/api/inference/predictors.html)
	- **`endpoint_name`**:  Name of the Amazon SageMaker endpoint to which requests are sent.
	- **`sagemaker_session`**: A SageMaker Session object, used for SageMaker interactions.
	- Behavior for **serialization** of input data and **deserialization** of result data can be configured through initializer arguments. If not specified, *a sequence of* **bytes** is expected and the API sends it in the request body without modifications. In response, the API returns *the sequence of* **bytes** from the prediction result without any modifications.
		- `serializer`: A serializer object, used to encode data for an inference endpoint
		- `deserializer`: A deserializer object, used to decode data from an inference endpoint
		  
		  
	- **`predict()`**: [reference](https://sagemaker.readthedocs.io/en/stable/api/inference/predictors.html#sagemaker.predictor.Predictor.predict)
		- `data`: Input data for which you want the model to provide inference. If a **serializer** was specified when creating the Predictor, the result of the serializer is sent as input data. Otherwise the data must be sequence of bytes, and the predict method then sends **the bytes** in the request body as is.


### Use SagaMaker Runtime Client  to Test Result

```python
import boto3
import json

runtime = boto3.Session().client('sagemaker-runtime')

endpoint_name = '...'
content_type = 'text/csv',

response = runtime.invoke_endpoint(EndpointName=endpoint_name,
								   ContentType=content_type,
								   Body= input_str[0])

result = json.loads(response['Body'].read().decode())
```

- `boto3.Session()`:  [reference](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/core/session.html)
	- `client(service_name)`:  Create a low-level service client by name.
	- `boto3.client('sagemaker-runtime')` returns the `SageMakerRuntime.Client` object [reference](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/sagemaker-runtime.html)
	  
- `SageMakerRuntime.Client`: The Amazon SageMaker runtime API. [reference](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/sagemaker-runtime.html)
	- `invoke_endpoint()`: After you deploy a model into production using Amazon SageMaker hosting services, your client applications use this API to get inferences from the model hosted at the specified endpoint. It calls `InvokeEndpoint` API.  [reference](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/sagemaker-runtime/client/invoke_endpoint.html)


### Clean Up

#### Delete Endpoint and Endpoint configuration

```python
import boto3

# Specify your AWS Region
aws_region='<aws_region>'

# Specify the name of your endpoint and endpoint configuration
endpoint_name='<endpoint_name>'
endpoint_config_name=`'<endpoint_name>'`

# Create a low-level SageMaker service client.
sagemaker_client = boto3.client('sagemaker', region_name=aws_region)

# Delete endpoint
sagemaker_client.delete_endpoint(EndpointName=endpoint_name)
sagemaker_client.delete_endpoint_config(EndpointConfigName=endpoint_config_name)
```

- [SageMaker Service](https://docs.aws.amazon.com/sagemaker/latest/APIReference/API_Operations_Amazon_SageMaker_Service.html) `client = 'sagemaker'`. 
	- **`delete_endpoint()`**: Deletes an endpoint. SageMaker frees up all of the resources that were deployed when the endpoint was created. [Python SDK reference](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/sagemaker/client/delete_endpoint.html#)
	- **`delete_endpoint_config()`**: Deletes an endpoint configuration. The `DeleteEndpointConfig` API deletes only the specified configuration. It does not delete endpoints created using the configuration. [Python SDK reference](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/sagemaker/client/delete_endpoint_config.html#)
- `Estimator.delete_endpoint`: [reference](https://sagemaker.readthedocs.io/en/stable/api/training/estimators.html#sagemaker.estimator.EstimatorBase.delete_endpoint)
- `sagemaker.session.Session()`: [reference](https://sagemaker.readthedocs.io/en/stable/api/utility/session.html)
	- **`delete_endpoint()`**: Delete an Amazon SageMaker `Endpoint`. [reference](https://sagemaker.readthedocs.io/en/stable/api/utility/session.html#sagemaker.session.Session.delete_endpoint)
	- **`delete_endpoint_config()`**: Delete an Amazon SageMaker endpoint configuration. [reference](https://sagemaker.readthedocs.io/en/stable/api/utility/session.html#sagemaker.session.Session.delete_endpoint_config)
#### Delete Model

```python
import boto3

# Specify your AWS Region
aws_region='<aws_region>'

# Specify the name of your endpoint configuration
model_name='<model_name>'

# Create a low-level SageMaker service client.
sagemaker_client = boto3.client('sagemaker', region_name=aws_region)

# Delete model
sagemaker_client.delete_model(ModelName=model_name) 
```

- [SageMaker Service](https://docs.aws.amazon.com/sagemaker/latest/APIReference/API_Operations_Amazon_SageMaker_Service.html) `client = 'sagemaker'`. 
	- **`delete_model()`**: Deletes a model. The `DeleteModel` API deletes only the model entry that was created in SageMaker when you called the `CreateModel` API. It does not delete model artifacts, inference code, or the IAM role that you specified when creating the model. [Python SDK reference](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/sagemaker/client/delete_model.html#)
	  
- `sagemaker.session.Session()`: [reference](https://sagemaker.readthedocs.io/en/stable/api/utility/session.html)
	- **`delete_model()`**: Delete an Amazon SageMaker Model. [reference](https://sagemaker.readthedocs.io/en/stable/api/utility/session.html#sagemaker.session.Session.delete_model)

-----------
##  Recommended Notes

- [[SageMaker BYO Container Entry point]]
- [[SageMaker SDK Training via Training API]]
- [[Amazon SageMaker Python SDK 2 Deploy a Pre-Trained Model]]
- [[Amazon SageMaker Python SDK 3 Frameworks]]
	- [[Amazon SageMaker Python SDK 3.1.2 Pytorch Deploy and Hosting]]
	- [[Amazon SageMaker Python SDK 3.1.3 BYO Model and Attach]]
- Amazon SageMaker Python SDK [Hosting your model](https://sagemaker-examples.readthedocs.io/en/latest/advanced_functionality/scikit_bring_your_own/scikit_bring_your_own.html#Hosting-your-model)
- Amazon SageMaker Developer Guide. [Deploy models for inference](https://docs.aws.amazon.com/sagemaker/latest/dg/deploy-model.html)
	- [Model Development](https://docs.aws.amazon.com/sagemaker/latest/dg/how-it-works-deployment.html)
	- [Real-time Inference](https://docs.aws.amazon.com/sagemaker/latest/dg/realtime-endpoints.html)
		- [Automatically Scale Amazon SageMaker Models](https://docs.aws.amazon.com/sagemaker/latest/dg/endpoint-auto-scaling.html)
	- [Use Batch Transform](https://docs.aws.amazon.com/sagemaker/latest/dg/batch-transform.html)
	- [Use Docker Containers to build Models](https://docs.aws.amazon.com/sagemaker/latest/dg/docker-containers.html)
	- [Delete Endpoints and Resources](https://docs.aws.amazon.com/sagemaker/latest/dg/realtime-endpoints-delete-resources.html)
- AWS SDK **Boto3** package [guide](https://boto3.amazonaws.com/v1/documentation/api/latest/guide/quickstart.html)
	- `Session`: [reference](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/core/session.html)
	- `SageMakerRuntime`: [reference](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/sagemaker-runtime.html)
- `Estimator` class [reference](https://sagemaker.readthedocs.io/en/stable/api/training/estimators.html)
- `Model` class [reference](https://sagemaker.readthedocs.io/en/stable/api/inference/model.html)
- `Predictor` class [reference](https://sagemaker.readthedocs.io/en/stable/api/inference/predictors.html)
- Amazon SageMaker Python SDK Utility API [doc](https://sagemaker.readthedocs.io/en/stable/api/utility/index.html)
- Amazon SageMaker Runtime [wiki](https://docs.aws.amazon.com/sagemaker/latest/APIReference/API_Operations_Amazon_SageMaker_Runtime.html)
- Amazon SageMaker Services [link](https://docs.aws.amazon.com/sagemaker/latest/APIReference/API_Operations_Amazon_SageMaker_Service.html)