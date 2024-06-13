---
tags:
  - code
  - code_snippet
  - aws/lambda
keywords: 
topics: 
language: python
date of note: 2024-04-02
---

## Code Snippet Summary

>[!important]
>Task for this Lambda Function:
>- Fetch the **S3 URLs** for input
>- Fetch the **S3 URLs** for output
>- Fetch the **State Machine ARN**
>- Fetch the *Input and Output Format*
>- Create client for `stepfunctions` service
>- Start **execution** of the state machine with given input format.

## Code

```python
import json
import boto3


def lambda_handler(event, context):
    region = ...
    account_id = ...
    workflow_name = ...
    
    bucket_input = ...
    key_input = ...
    
    prefix = key
    kwarg_input = f"s3://{bucket_input}/{key_input}"
    
    bucket_output = ...
    key_output = ...
    
    kwarg_output = f's3://{bucket_output}/{key_output}/'
    
    stateMachineArn = f'arn:aws:states:{region}:{account_id}:stateMachine:{workflow_name}'
    kwarg_transform_jobname = ...
    
    response = boto3.client('stepfunctions').start_execution(
        stateMachineArn = stateMachineArn,
        input=json.dumps({"PreprocessingJobName": kwarg_transform_jobname,
                          "Input":  kwarg_input,
                          "Output": kwarg_output
                         })
        )
        
        
    return {"statusCode": 200, "body": f"Success!: {kwarg_input}"}

```

- retrieval of S3 bucket and key from S3 URL: [[AWS - retrieve the S3 bucket and file from S3 URL]]
- `boto3`: AWS SDK [guide](https://boto3.amazonaws.com/v1/documentation/api/latest/guide/quickstart.html)
	- `boto3.client` [reference](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/core/boto3.html#boto3.client)
	- **`boto3.client('stepfunctions')`**: create `stepfunction` client; 
		- `SFN.Client`:  A low-level client representing AWS Step Functions (SFN).[reference](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/stepfunctions.html)
			- **Step Functions** is a service that lets you coordinate the components of distributed applications and microservices using visual workflows.
			- You can use Step Functions to build applications from individual components, each of which performs a *discrete function*, or **task**, allowing you to scale and change applications quickly.
			- Step Functions provides a *console* that helps *visualize the components* of your application as a series of steps.
			- Step Functions **automatically triggers and tracks each step**, and *retries steps* when there are errors, so your application executes predictably and in the right order every time. 
			- Step Functions **logs** the state of each step, so you can quickly diagnose and debug any issues.
			- **`start_execution()`**: Starts a state machine execution. [reference](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/stepfunctions/client/start_execution.html)
				- **`stateMachineArn`**:  The Amazon Resource Name (ARN) of the state machine to execute. 
					- **An unqualified state machine ARN** – Refers to a state machine ARN that *isn’t qualified with a version or alias ARN*. The following is an example of an unqualified state machine ARN. `arn:<partition>:states:<region>:<account-id>:stateMachine:<myStateMachine>`
					- **A state machine version ARN** – Refers to a *version ARN*, which is a combination of *state machine ARN* and *the version number* separated by a *colon* (:). The following is an example of the ARN for version 10. `arn:<partition>:states:<region>:<account-id>:stateMachine:<myStateMachine>:10` 
					- **A state machine alias ARN** – Refers to an *alias ARN*, which is a combination of state machine ARN and *the alias name* separated by a *colon* (:). The following is an example of the ARN for an alias named `PROD`. `arn:<partition>:states:<region>:<account-id>:stateMachine:<myStateMachine:PROD>` 
				- **`input`**: The string that contains the **JSON input data** for the execution. 
				- **Response** dictionary 
					- `executionArn`: The Amazon Resource Name (ARN) that identifies the execution.
					- `startDate`: The date the execution is started.
```python
{
    'executionArn': 'string',
    'startDate': datetime(2015, 1, 1)
}
```



-----------
##  Recommended Notes

- **AWS SDK `boto3`** package [guide](https://boto3.amazonaws.com/v1/documentation/api/latest/guide/quickstart.html)
	- `boto3.client('stepfunctions')` and `SFN.Client` [reference](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/stepfunctions.html)
		- `start_execution()`: [reference](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/stepfunctions/client/start_execution.html)
- [Step Functions examples using SDK for Python (Boto3)](https://docs.aws.amazon.com/code-library/latest/ug/python_3_sfn_code_examples.html)
	- [Create a state machine](https://github.com/awsdocs/aws-doc-sdk-examples/blob/main/python/example_code/stepfunctions/state_machines.py#L28) (`CreateStateMachine`)
	- [Create an activity](https://github.com/awsdocs/aws-doc-sdk-examples/blob/main/python/example_code/stepfunctions/activities.py#L31) (`CreateActivity`)
	- [Delete a state machine](https://github.com/awsdocs/aws-doc-sdk-examples/blob/main/python/example_code/stepfunctions/state_machines.py#L138) (`DeleteStateMachine`)
	- [Delete an activity](https://github.com/awsdocs/aws-doc-sdk-examples/blob/main/python/example_code/stepfunctions/activities.py#L118) (`DeleteActivity`)
	- [Describe a state machine](https://github.com/awsdocs/aws-doc-sdk-examples/blob/main/python/example_code/stepfunctions/state_machines.py#L75) (`DescribeStateMachine`)
	- [Describe a state machine run](https://github.com/awsdocs/aws-doc-sdk-examples/blob/main/python/example_code/stepfunctions/state_machines.py#L118) (`DescribeExecution`)
	- [Get task data for an activity](https://github.com/awsdocs/aws-doc-sdk-examples/blob/main/python/example_code/stepfunctions/activities.py#L73) (`GetActivityTask`)
	- [List activities](https://github.com/awsdocs/aws-doc-sdk-examples/blob/main/python/example_code/stepfunctions/activities.py#L51) (`ListActivities`)
	- [List state machines](https://github.com/awsdocs/aws-doc-sdk-examples/blob/main/python/example_code/stepfunctions/state_machines.py#L53) (`ListStateMachines`)
	- [Send a success response to a task](https://github.com/awsdocs/aws-doc-sdk-examples/blob/main/python/example_code/stepfunctions/activities.py#L95) (`SendTaskSuccess`)
	- [Start a state machine run](https://github.com/awsdocs/aws-doc-sdk-examples/blob/main/python/example_code/stepfunctions/state_machines.py#L95) (`StartExecution`)
- [AWS SDK Examples: Step Functions](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/python/example_code/stepfunctions#code-examples)
- [AWS Command Line Interface (CLI)](https://aws.amazon.com/cli/)
- [AWS CLI Command Reference](https://docs.aws.amazon.com/cli/latest/)