---
tags:
  - code
  - code_snippet
  - aws/step_function
  - aws/sagemaker
keywords: 
topics: 
language: python
date of note: 2024-04-07
---

## Code Snippet Summary

>[!important]
>In this example, we need to build a `Processor`  and launch a `ProcessingJob`  in Amazon SageMaker using **SageMaker Python SDK**

- We first obtain  `session` , `region` and `role`

```python
import sagemaker
from sagemaker import get_execution_role
import boto3

region = boto3.session.Session().region_name
session = sagemaker.Session()

role = get_execution_role()
```

## Code

### Build `ScriptProcessor` using BYO container 

```python
from sagemaker.processing import ScriptProcessor

# this is the image URI stored in ECR
processing_repository_uri = '{}.dkr.ecr.{}.{}/{}'.format(account_id, region, uri_suffix, ecr_repository + tag)


script_processor = ScriptProcessor(command=['python3'],
                image_uri=processing_repository_uri,
                role=role,
                sagemaker_session=session,
                instance_count=1,
                instance_type='ml.c4.xlarge')
```

- `ScriptProcessor` Initializes a `ScriptProcessor` instance. [reference](https://sagemaker.readthedocs.io/en/stable/api/training/processing.html#sagemaker.processing.ScriptProcessor)
	- Handles **Amazon SageMaker processing** tasks for jobs using a machine learning framework. 
	  
	- **`role`**: An AWS IAM role name or ARN. Amazon SageMaker Processing uses this role to access AWS resources, such as data stored in Amazon S3.
    - **`image_uri`**: The URI of the Docker image to use for the processing jobs.  
    - `command`: The **command to run**, along with any command-line flags. Example: [“python3”, “-v”].
    - `instance_count`: The number of instances to run a processing job with.
    - **`instance_type`**:The type of EC2 instance to use for processing, for example, `‘ml.c4.xlarge’`.
	- `sagemaker_session`: Session object which manages interactions with Amazon SageMaker and any other AWS services needed.
	  
### Prepare Input and Output Schema

```python
from stepfunctions.inputs import ExecutionInput
from sagemaker.processing import (ProcessingInput, 
								  ProcessingOutput
								  )

input_schema = {
	"PreprocessingJobName": str,
	"InputMessage": str,
	"OutputProcessedMessage": str
	}

# a placeholder define the input structure and format. This allows for dynamic passing values at execution
input_placeholder = ExecutionInput(schema=input_schema)

# initiate ProcessingInput and ProcessingOutput
processing_inputs=[ProcessingInput(input_name='input_messages',                                source=input_placeholder["InputMessage"],
                   destination='/opt/ml/processing/input'
                                  )
                  ]
                    
processing_outputs=[ProcessingOutput(output_name='processed_message',
		         destination=input_placeholder["OutputProcessedMessage"],
                 source='/opt/ml/processing/output/processed'
			                         ),
                    ]
```

>[!info]
>- Note that in **BYO container**, the data and code are all stored in `/opt/ml/processing` directory. 
>	- Save *input data* under `/opt/ml/processing/input`
>	- Save *output data* under `/opt/ml/processing/output`
>	- Save *code and customized module* under `/opt/ml/processing/code`


- `stepfunctions.ExecutionInput`: Top-level class for execution input placeholders. [reference](https://aws-step-functions-data-science-sdk.readthedocs.io/en/stable/placeholders.html#stepfunctions.inputs.ExecutionInput)

- `processing.ProcessingInput`: Initializes a `ProcessingInput` instance. [reference](https://sagemaker.readthedocs.io/en/stable/api/training/processing.html#sagemaker.processing.ProcessingInput)
	- Accepts parameters that specify an **Amazon S3 input** for a processing job.
	- Also provides a method to *turn those parameters into a dictionary*.
	  
	- **`source`**: The source for the input. 
		- If a local path is provided, it will automatically be *uploaded* to S3 under: `“s3://<default-bucket-name>/<job-name>/input/<input-name>”`.
	- **`destination`**: The destination of the input.
	- **`input_name`**:  The name for the input. 
		- If a name is not provided, one will be generated (eg. “input-1”).
	- `s3_data_type`: Valid options are “ManifestFile” or “S3Prefix”.
	- `s3_input_mode`: Valid options are “Pipe”, “File” or “FastFile”.
	- `s3_data_distribution_type`: Valid options are “FullyReplicated” or “ShardedByS3Key”.


- `processing.ProcessingOutput`: Initializes a `ProcessingOutput` instance. [reference](https://sagemaker.readthedocs.io/en/stable/api/training/processing.html#sagemaker.processing.ProcessingOutput)
	- Accepts parameters that specify an **Amazon S3 output** for a processing job.
	- It also provides a method to turn those parameters into a dictionary.
	  
	- **`source`**: The source for the output.
	- **`destination`**: The destination of the output.
		- If a destination is not provided, one will be generated: `“s3://<default-bucket-name>/<job-name>/output/<output-name>”` 
		- Note: this does not apply when used with [`ProcessingStep`](https://sagemaker.readthedocs.io/en/stable/workflows/pipelines/sagemaker.workflow.pipelines.html#sagemaker.workflow.steps.ProcessingStep "sagemaker.workflow.steps.ProcessingStep").
	- **`output_name`**:  The name for the output. 
		- If a name is not provided, one will be generated (eg. “output-1”).

### Launch ProcessingJob

```python
script_processor.run(code='my_script.py',
                     inputs=processing_inputs,
                     outputs=processing_outputs
                     )
```

- **`ScriptProcessor.run()`** Runs a processing job. [reference](https://sagemaker.readthedocs.io/en/stable/api/training/processing.html#sagemaker.processing.ScriptProcessor.run)
	- **`code`** ([_str_](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.12)")) – This can be an **S3 URI** or a **local path** to a file with the framework script to run.
	- **`inputs`** (list\[[`ProcessingInput`](https://sagemaker.readthedocs.io/en/stable/api/training/processing.html#sagemaker.processing.ProcessingInput "sagemaker.processing.ProcessingInput")\]):  Input files for the processing job.
		- These **must be** provided as [`ProcessingInput`](https://sagemaker.readthedocs.io/en/stable/api/training/processing.html#sagemaker.processing.ProcessingInput "sagemaker.processing.ProcessingInput") objects (default: None).
    - **`outputs`** (list\[[`ProcessingOutput`](https://sagemaker.readthedocs.io/en/stable/api/training/processing.html#sagemaker.processing.ProcessingOutput "sagemaker.processing.ProcessingOutput")\]): Outputs for the processing job.
	    - These can be specified as either path strings or [`ProcessingOutput`](https://sagemaker.readthedocs.io/en/stable/api/training/processing.html#sagemaker.processing.ProcessingOutput "sagemaker.processing.ProcessingOutput") objects (default: None).
	      
	- `arguments`: A list of **string arguments** to be passed to a processing job (default: None).
	- `wait`: Whether the call should *wait until the job completes* (default: True).
    - `logs`: Whether to *show the logs* produced by the job. Only meaningful when wait is True (default: True).
    - `job_name`: *Processing job name*. 
	    - If not specified, the processor generates a default job name, based on the base job name and current timestamp.


>[!example] 
>In this example, we not only pass script to container but also pass our own module to corresponding sub folder under `/opt/ml/processing/code`
>
> ```python
> # input config
> code_input = ProcessingInput(source=input_data, destination='/opt/ml/processing/input')
> 
> package_input = ProcessingInput(source='../../dockers/docker/bsm/processing/', 
>                   destination="/opt/ml/processing/input/code/bsm_processing/")
> # output config
> output = ProcessingOutput(output_name='processed_data',
>                       destination=f's3://{bucket}/processed_data/{output_date}/',
>                       source='/opt/ml/processing/output/processed')
> # run local code               
> script_processor.run(code ='rnr_bsm_preprocessing_main.py',
>                      inputs=[code_input,
>                             package_input],
>        
>                       outputs=[output
>                               ]
>                      )
> ```
> 


-----------
##  Recommended Notes

- `ScriptProcessor` Handles Amazon SageMaker processing tasks for jobs using a machine learning framework. [reference](https://sagemaker.readthedocs.io/en/stable/api/training/processing.html#sagemaker.processing.ScriptProcessor)
	- **`ScriptProcessor.run()`** Runs a processing job. [reference](https://sagemaker.readthedocs.io/en/stable/api/training/processing.html#sagemaker.processing.ScriptProcessor.run)
- `processing.ProcessingInput`: Initializes a `ProcessingInput` instance. [reference](https://sagemaker.readthedocs.io/en/stable/api/training/processing.html#sagemaker.processing.ProcessingInput)
- `processing.ProcessingOutput`: [reference](https://sagemaker.readthedocs.io/en/stable/api/training/processing.html#sagemaker.processing.ProcessingOutput)
  
- [[Amazon SageMaker Python SDK 4 Processing]]
	- [[Amazon SageMaker Python SDK 4.1 BYO Processing Container]]
- [[Amazon SageMaker Python SDK 5 Workflow and Step Function]]
- For BYO container, check steps to build one
	- [[SageMaker BYO Container Entry point]]
- Build Processing Workflow using Step functions
	- [[AWS Step Functions - One-Step Processing Workflow]]