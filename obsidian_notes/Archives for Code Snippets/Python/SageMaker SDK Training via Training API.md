---
tags:
  - code
  - code_snippet
  - aws/sagemaker
  - model/training
keywords: 
topics: 
language: python
date of note: 2024-03-28
---

## Code Snippet Summary

>[!important] Highlight
>In order to use **SageMaker** to fit our algorithm, we'll create an `Estimator` that defines *how to use the container to train*. This includes the *configuration* we need to invoke SageMaker training:
> 
> - The __container name__. This is constructed as in the shell commands above.
> - The __role__. As defined above.
> - The __instance count__ which is the number of machines to use for training.
> - The __instance type__ which is the type of machine to use for training.
> - The __output path__ determines where the model artifact will be written.
> - The __session__ is the SageMaker session object that we defined above.
>
>Then we use `fit()` on the estimator to train against the data that we uploaded above.

## Prerequisite
### Prepare account id, region, role and registry URL in ECR

```python
import boto3
import sagemaker
from sagemaker import get_execution_role


# This instantiates a SageMaker session that we will be operating in.
session = sagemaker.Session()

# This object represents the IAM role that we are assigned.
role = sagemaker.get_execution_role()

# Get region name 
region = boto3.session.Session().region_name

# registry URL for uploaded Docker Image in ECR
account_id = boto3.client('sts').get_caller_identity().get('Account')
algorithm_name = ...
tag = ':latest'
uri_suffix = 'amazonaws.com'
if region in ['cn-north-1', 'cn-northwest-1']:
	uri_suffix = 'amazonaws.com.cn'

# format image uri
image = '{account_id}.dkr.ecr.{region}.{uri_suffix}/{algorithm_name}:{tag}'.format(account_id=account_id, 
		   region=region, 
		   uri_suffix=uri_suffix, 
		   algorithm_name=algorithm_name, 
		   tag=tag
		   )
```

- `session = sagemaker.Session()` start a new session. 
- `boto3.session.Session`: A session stores configuration state and allows you to create service clients and resources. [reference](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/core/session.html)
	- `boto_session`: Use this **Botocore session** instead of creating a new default one.
- `boto3.client`: Create a low-level service client by name using the default session. [reference](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/core/session.html#boto3.session.Session.client)
	- **`service_name`**: You can get a list of available services via [`get_available_services()`](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/core/session.html#boto3.session.Session.get_available_services "boto3.session.Session.get_available_services"). 
	- In this code, we called *'sts'* as *Security Token Service (STS)* to retrieve caller's account information. 
	- Similar to the **AWS CLI** command `aws sts get-caller-identity`. [[SageMaker SDK Training Script Push Dockerfile to ECR#Prepare and Retrieve Information]]

  
## Code

### Create an `Estimator`

- Create `Estimator` class based on uploaded Docker Image in ECR. 
	- `Estimator` is a high level interface for SageMaker training.
	- Docker Image pushed to ECR [[SageMaker SDK Training Script Push Dockerfile to ECR]]

- Use generic `sagemaker.estimator.Estimator` Framework for *BYO container* 
	- Check other Frameworks in SageMaker. [[Amazon SageMaker Python SDK 3 Frameworks]]
	- Provide following parameters for `Estimator` class. [reference](https://sagemaker.readthedocs.io/en/stable/api/training/estimators.html#sagemaker.estimator.Estimator)
		- *docker image, account, login permission*
			- **`image_uri`**: The container image to use for training. 
			- **`role`**: An **AWS IAM role** (either name or full ARN). The Amazon SageMaker training jobs and APIs that create Amazon SageMaker endpoints use this role to access training data and model artifacts. After the endpoint is created, the inference code might use the IAM role, if it needs to access an AWS resource.
			- **`sagemaker_session`**: Session object which manages interactions with Amazon SageMaker APIs and any other AWS services needed.
		- *device related*
			- **`instance_count`**: Number of **Amazon EC2 instances** to use for training. Required if instance_groups is not set.
			- **`instance_type`**: **Type** of EC2 instance to use for training,
			- `volume`: Size in **GB** of the storage volume to use for storing input and output data during training (default: 30).
		- *training parameters* 
			- **`output_path`**: S3 location for saving the *training result (model artifacts and output files)*.
			- `max_run`: Timeout in **seconds** for training (default: 24 hours = 24 * 60 * 60).
			- `metric_definitions`: A list of dictionaries that defines the metric(s) used to evaluate the training jobs.
			- `hyperparameters`: Dictionary containing the hyperparameters to initialize this estimator with.
		- *third party dependencies*
			- **`source_dir`**: The absolute, relative, or S3 URI Path to a **directory** with any other *training source code dependencies* aside from *the entry point file*.
				- *Structure within this directory* is **preserved** when *training* on Amazon SageMaker.
				- If the directory points to *S3*, no code is uploaded and the S3 location is used instead.
				- If `source_dir` is an *S3* URI, it must point to a **`tar.gz` file**.
			- `code_location`: Name of the S3 bucket where custom code is uploaded.
				- If not specified, the *default bucket* created by `sagemaker.session.Session` is used.
			- **`entry_point`**: The absolute or relative path to the **local Python source file** that should be executed as the *entry point* to **model hosting**.
				- If `source_dir` is specified, then `entry_point` must point to a file located at the **root** of `source_dir`.
			- `dependencies`: A list of absolute or relative paths to directories with any additional libraries that should be exported to the container.
				- The library folders are copied to SageMaker in the *same folder* where the *`entry_point` is copied*.
				- If the `source_dir` points to S3, code will be *uploaded* and the *S3 location* will be used instead.
				- Both `entry_point` file, dependency file as well as additional file in S3 will be copied to `opt/ml/code` directory in the container.
		- *checkpointing* 
			- `checkpoint_s3_uri`
			- `checkpoint_local_path`

```python
from sagemaker.estimator import Estimator

learner = sagemaker.estimator.Estimator(image, role, 1, 
							'ml.c4.xlarge',
							output_path=output_path,
							sagemaker_session=session,
							volume_size = 500,
							max_run = 4 * 24 * 60 * 60,
							metric_definitions = [
	{'Name': 'Train Loss', 'Regex': 'train_loss=([0-9\\\\.]+)'},
	{'Name': 'Validation Loss', 'Regex': 'val_loss=([0-9\\\\.]+)'},
	{'Name': 'Validation F1 Score', 'Regex': 'f1_score/val=([0-9\\\\.]+)'},
	{'Name': 'Validation AUC ROC', 'Regex': 'auroc/val=([0-9\\\\.]+)'}
							],
							hyperparameters=hyperparameters,
						    checkpoint_s3_uri=checkpoint_s3_bucket,
						checkpoint_local_path=checkpoint_local_path,
	)
```


### Fit `Estimator` using training script in Docker Image

- call `train` script in Docker Image via `Estimator.fit()` method. [reference](https://sagemaker.readthedocs.io/en/stable/api/training/estimators.html#sagemaker.estimator.Estimator.fit)
	- The S3 path in *'train'* will be used to pull training data. Saved in `SM_CHANNEL_TRAIN` channel.
	- Similarly *'val'* will map to `SM_CHANNEL_VAL`; *'test'* will map to `SM_CHANNEL_TEST`
	- Check [[Amazon SageMaker Python SDK 1 Training Model with SDK]]

```python
 learner.fit({'train': os.path.join(s3_location, 'train'),
	        'val': os.path.join(s3_location, 'val'),
            'test': os.path.join(s3_location, 'test')
             })
```

- The input of `fit()` can be 
	- **string**: the **S3 location** where training data is saved,  or local path in local mode.
	- **`sagemaker.inputs.TrainingInput`**: **channel configuration** for **S3 data sources** that can provide additional information as well as the *path* to the training dataset. See [`sagemaker.inputs.TrainingInput()`](https://sagemaker.readthedocs.io/en/stable/api/utility/inputs.html#sagemaker.inputs.TrainingInput "sagemaker.inputs.TrainingInput") for full details.
	- **`sagemaker.inputs.FileSystemInput`**: *channel configuration* for a **file system data source** that can provide additional information as well as the path to the training dataset. See [`FileSystemInput()`](https://sagemaker.readthedocs.io/en/stable/api/utility/inputs.html#sagemaker.inputs.FileSystemInput "sagemaker.inputs.FileSystemInput") objects.
	- **dictionary**: If using multiple channels for training data, you can specify a dict mapping channel names to strings or [`TrainingInput()`](https://sagemaker.readthedocs.io/en/stable/api/utility/inputs.html#sagemaker.inputs.TrainingInput "sagemaker.inputs.TrainingInput") objects or [`FileSystemInput()`](https://sagemaker.readthedocs.io/en/stable/api/utility/inputs.html#sagemaker.inputs.FileSystemInput "sagemaker.inputs.FileSystemInput") objects.

- `sagemaker.inputs.TrainingInput`: Amazon SageMaker channel configurations for **S3 data sources**. [reference](https://sagemaker.readthedocs.io/en/stable/api/utility/inputs.html#sagemaker.inputs.TrainingInput)
	- **`s3_data`**: Defines the location of S3 data to train on.
	- `s3_data_type`: Valid values: `'S3Prefix'`, `'ManifestFile'`, `'AugmentedManifestFile'`
	- **`content_type`**: MIME type of the input data (default: None).
	- `input_mode`: Optional override for this channel’s input mode (default: None). `'File’`, `'Pipe'` or `'FastFile'`. 
- `sagemaker.inputs.FileSystemInput`: Amazon SageMaker channel configurations for file system data sources in Amazon File system (`‘EFS’`, `‘FSxLustre’`). [reference](https://sagemaker.readthedocs.io/en/stable/api/utility/inputs.html#sagemaker.inputs.FileSystemInput)

### Hyperparameter Tuning

- use `tuner` package from SageMaker SDK [reference](https://sagemaker.readthedocs.io/en/stable/api/training/tuner.html)
- `sagemaker.tuner.HyperparameterTuner`: Defines interaction with **Amazon SageMaker hyperparameter tuning jobs.**  [reference](https://sagemaker.readthedocs.io/en/stable/api/training/tuner.html#sagemaker.tuner.HyperparameterTuner) 
	- **`estimator`**: An estimator object that has been initialized with the desired configuration. *There does not need to be a training job associated with this instance.*
	- **`objective_metric_name`**: *Name* of the metric for evaluating training jobs.
	- **`objective_type`**: The *type* of the objective metric for evaluating training jobs. This value can be either ‘Minimize’ or ‘Maximize’ (default: ‘Maximize’).
	- **`hyperparameter_ranges`**: Dictionary of parameter ranges. The *keys* of the dictionary are *the names of the hyperparameter,* and the *values* are the appropriate **parameter range class** to represent the range. These parameter ranges can be one of three types: 
		- *Continuous*: defined using `sagemaker.tuner.ContinuousParameter` 
		- *Integer*:  defined using `sagemaker.tuner.IntegerParameter` 
		- *Categorical*: defined using `sagemaker.tuner.CategoricalParameter` 
	- **`metric_definitions`** : A list of dictionaries that defines the *metric(s)* used to evaluate the training jobs. 
	
	- `strategy`:  Strategy to be used for hyperparameter estimations. Available options are: *‘Bayesian’*, *‘Random’*, *‘Hyperband’*, *‘Grid’* (default: *‘Bayesian’*). See [reference]([https://docs.aws.amazon.com/sagemaker/latest/dg/automatic-model-tuning-how-it-works.html](https://docs.aws.amazon.com/sagemaker/latest/dg/automatic-model-tuning-how-it-works.html))
	- `max_jobs`: Maximum total number of training jobs to start for the hyperparameter tuning job. Default 1 except for `strategy='Grid'`.
	- `max_parallel_jobs`: Maximum number of parallel training jobs to start (default: 1).
	- `early_stopping_type`: pecifies whether early stopping is enabled for the job. Can be either ‘Auto’ or ‘Off’ (default: ‘Off’). 
	- `max_runtime_in_seconds`: The maximum time in seconds that a hyperparameter tuning job can run.

```python
from sagemaker.tuner import IntegerParameter, CategoricalParameter, ContinuousParameter, HyperparameterTuner

objective_metric_name = 'Validation F1 Score'
objective_type = 'Maximize'

metric_definitions = [
{'Name': 'Train Loss', 'Regex': 'train_loss=([0-9\\.]+)'},
{'Name': 'Validation Loss', 'Regex': 'val_loss=([0-9\\.]+)'},
{'Name': 'Validation F1 Score', 'Regex': 'f1_score/val=([0-9\\.]+)'},
{'Name': 'Validation AUC ROC', 'Regex': 'auroc/val=([0-9\\.]+)'},
]

# define the range of hyperparameter
hyperparameter_ranges = {
	"lr": ContinuousParameter(min_value=1e-3, max_value=1e-1, scaling_type='Logarithmic'),
	"max_sen_len": IntegerParameter(min_value=350, max_value=1000, scaling_type='Linear'),
	"batch_size": CategoricalParameter([64, 128, 256]),
	"epochs": IntegerParameter(10, 20),
	"optimizer": CategoricalParameter(['Adam', 'SGD'])
}


# create Hyperparameter Tuner
tuner = HyperparameterTuner(
	learner,
	objective_metric_name,
	hyperparameter_ranges,
	metric_definitions,
	max_jobs=4,
	max_parallel_jobs=2,
	objective_type=objective_type
)

# start tuning jobs
tuner.fit({'train_test_val':train_location})
```



-----------
##  Recommended Notes

- [[Amazon SageMaker Python SDK 1 Training Model with SDK]]
- [[Amazon SageMaker Python SDK 3 Frameworks]]
	- [[Amazon SageMaker Python SDK 3.1.1 Pytorch Train]]
- Using your Algorithm in Amazon SageMaker [doc](https://sagemaker-examples.readthedocs.io/en/latest/advanced_functionality/scikit_bring_your_own/scikit_bring_your_own.html#Part-2:-Using-your-Algorithm-in-Amazon-SageMaker)
- Amazon SageMaker Python SDK **Boto3** package [guide](https://boto3.amazonaws.com/v1/documentation/api/latest/guide/quickstart.html)
- `Estimator` class [reference](https://sagemaker.readthedocs.io/en/stable/api/training/estimators.html)
- `sagemaker.inputs.TrainingInput()` [reference](https://sagemaker.readthedocs.io/en/stable/api/utility/inputs.html#sagemaker.inputs.TrainingInput "sagemaker.inputs.TrainingInput")
- `sagemaker.inputs.FileSystemInput()` [reference](https://sagemaker.readthedocs.io/en/stable/api/utility/inputs.html#sagemaker.inputs.FileSystemInput "sagemaker.inputs.FileSystemInput")
- `HyperparameterTuner` class [reference](https://sagemaker.readthedocs.io/en/stable/api/training/tuner.html)
- Amazon SageMaker Python SDK Utility API [doc](https://sagemaker.readthedocs.io/en/stable/api/utility/index.html)
- `sagemaker.session.Session` [reference](https://sagemaker.readthedocs.io/en/stable/api/utility/session.html)