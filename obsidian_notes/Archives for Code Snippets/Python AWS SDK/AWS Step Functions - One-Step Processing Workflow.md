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
>In this example, we create a **Workflow** by accepting one `ProcessingStep` using created `Processor` from Amazon SageMaker SDK.
>- See [[SageMaker SDK Script Processor]] on the creation of a `ScriptProcessor`:
>  ```python
>  from sagemaker.processing import ScriptProcessor
>  script_processor = ScriptProcessor(...)
>  ```
>- Use `ExecutionInput` to define a common schema for input including the *input channel*, *output channel* and *job name* etc.
>- Use `sagemaker.processing.ProcessingInput` and `sagemaker.processing.ProcessingOutput` to define the input and output of ProcessingJob.
>  ```python
> from sagemaker.processing import (ProcessingInput, ProcessingOutput)
> 
>  processing_inputs=[ProcessingInput(...)]
>  processing_outputs = [ProcessingOutput(...])
>  ```
>- Use `ProcessingStep` to initiate a **ProcessingStep** using `script_processor` and `processing_inputs`, `processing_outputs` defined above.
>- Use `Chain` to create a **Chain** with just `ProcessingStep`.
>- Use `Workflow` to create a **AWS Workflow** based on `Chain` above.
>- Execute `Workflow` with `execute()` method.

- Install Step Function SDK
```python
# install stepfunctions
!{sys.executable} -m pip install --upgrade stepfunctions
```
## Code

```python
from stepfunctions.workflow import Workflow
from stepfunctions.inputs import ExecutionInput
```

### Create one-step Workflow with Processing Step

```python
from stepfunctions.inputs import ExecutionInput
from stepfunctions.steps import (Chain, ProcessingStep)
from stepfunctions.workflow import Workflow


input_schema = {
	"PreprocessingJobName": str,
	"InputMessage": str,
	"OutputProcessedMessage": str
	}
# a placeholder define the input structure and format. This allows for dynamic passing values at execution
input_placeholder = ExecutionInput(schema=input_schema)

# definition Processor, Processing Input and Output
# script_processor = ...
# processing_inputs = ...
# processing_outputs = ...

# create a processing step
processing_step = ProcessingStep("Processing Step",
            processor = script_processor,
		    job_name = input_placeholder["PreprocessingJobName"],
		    inputs = processing_inputs,
		    outputs = processing_outputs,
		    container_entrypoint=["python3", "/opt/program/my_script.py"],
)

# create Workflow by Chaining one-step only
workflow_chain = Chain([processing_step])

workflow = Workflow(
    name="Processsing Workflow",
    definition=workflow_chain,
    role=workflow_execution_role
)

workflow.create()

# execute Workflow
execution = workflow.execute(inputs={"PreprocessingJobName":         "bsm-batch-preprocessing-daily-{}".format(uuid.uuid1().hex),
                                     "InputMessage":                  inputs_source,
                                     "OutputProcessedMessage":        outputs_processed_destination
                                    }
                            )
# get status return                     
execution_output = execution.get_output(wait=True)
```

- `stepfunctions.steps.ProcessingStep`: Creates a **Task State** to execute a **SageMaker Processing Job**.  [reference](https://aws-step-functions-data-science-sdk.readthedocs.io/en/stable/sagemaker.html#stepfunctions.steps.sagemaker.ProcessingStep)
	- **`processor`** ([_sagemaker.processing.Processor_](https://sagemaker.readthedocs.io/en/stable/api/training/processing.html#sagemaker.processing.Processor "(in sagemaker v2.73.0)")): The *processor* for the processing step.
	- **`job_name`**: Specify a processing job name, this is required for the processing job to run. 
		- We recommend to use [`ExecutionInput`](https://aws-step-functions-data-science-sdk.readthedocs.io/en/stable/placeholders.html#stepfunctions.inputs.ExecutionInput "stepfunctions.inputs.ExecutionInput") *placeholder collection* to pass the value **dynamically** in each execution.
	- **`inputs`** (list\[[`ProcessingInput`](https://sagemaker.readthedocs.io/en/stable/api/training/processing.html#sagemaker.processing.ProcessingInput "(in sagemaker v2.73.0)")\]): Input files for the processing job. 
		- These must be provided as [`ProcessingInput`](https://sagemaker.readthedocs.io/en/stable/api/training/processing.html#sagemaker.processing.ProcessingInput "(in sagemaker v2.73.0)") objects (default: None).
	- **`outputs`** (list\[[`ProcessingOutput`](https://sagemaker.readthedocs.io/en/stable/api/training/processing.html#sagemaker.processing.ProcessingOutput "(in sagemaker v2.73.0)")\]): Outputs for the processing job.
		- These can be specified as either path strings or [`ProcessingOutput`](https://sagemaker.readthedocs.io/en/stable/api/training/processing.html#sagemaker.processing.ProcessingOutput "(in sagemaker v2.73.0)") objects (default: None).
	- `experiment_config`: Specify the experiment config for the processing. (Default: None)
	- `container_arguments`: The *arguments for a container* used to run a processing job.
	- **`container_entrypoint`**: The **entrypoint** for a* container* used to run a processing job. 

- `stepfunctions.steps.Chain`: **Chain** is a logical group of states, that resembles a *linked list*. The start state is the head of the _Chain_ and the end state is the tail of the _Chain_. [reference](https://aws-step-functions-data-science-sdk.readthedocs.io/en/stable/states.html#stepfunctions.steps.states.Chain)
	- **`steps`**: List of states to be chained in-order. (default: [])

- `stepfunctions.workflow.Workflow`: Class for creating and managing a workflow. [reference](https://aws-step-functions-data-science-sdk.readthedocs.io/en/stable/workflow.html#stepfunctions.workflow.Workflow)
	- `name`: The name of the workflow. 
	- **`definition`** ([_State_](https://aws-step-functions-data-science-sdk.readthedocs.io/en/stable/states.html#stepfunctions.steps.states.State "stepfunctions.steps.states.State") _or_ [_Chain_](https://aws-step-functions-data-science-sdk.readthedocs.io/en/stable/states.html#stepfunctions.steps.states.Chain "stepfunctions.steps.states.Chain")): The [Amazon States Language](https://states-language.net/spec.html) definition of the workflow. 
	- `role`: The Amazon Resource Name (ARN) of the IAM role to use for creating, managing, and running the workflow.
	- **`execution_input`** ([_ExecutionInput_](https://aws-step-functions-data-science-sdk.readthedocs.io/en/stable/placeholders.html#stepfunctions.inputs.ExecutionInput "stepfunctions.inputs.ExecutionInput")_,_ _optional_): Placeholder collection that defines the placeholder variables for the workflow execution. 
		- This is also used to validate inputs provided when executing the workflow. (default: None)
		  
		  
	- `attach()`: Factory method to create an instance attached to an **existing workflow** in **Step Functions**.
		- `state_machine_arn`: The Amazon Resource Name (ARN) of the existing workflow.  
	- **`create()`**: **Creates the workflow** on **Step Functions**.
		- Return the Amazon Resource Name (ARN) of the workflow created.
	- **`execute()`**: **Starts** a single execution of the workflow.
		- **`name`**: The name of the workflow execution. 
			- If one is not provided, a workflow execution name will be auto-generated. (default: None)
		- **`inputs`**: Input data for the workflow execution.


## SageMaker Pipeline Implementation

- [[An End-to-End Training Deployment Pipeline on AWS]]


-----------
##  Recommended Notes

- `stepfunctions.ExecutionInput`: Top-level class for execution input placeholders. [reference](https://aws-step-functions-data-science-sdk.readthedocs.io/en/stable/placeholders.html#stepfunctions.inputs.ExecutionInput)
- `stepfunctions.steps.ProcessingStep`: Creates a **Task State** to execute a **SageMaker Processing Job**.  [reference](https://aws-step-functions-data-science-sdk.readthedocs.io/en/stable/sagemaker.html#stepfunctions.steps.sagemaker.ProcessingStep)
- `stepfunctions.steps.Chain`:  [reference](https://aws-step-functions-data-science-sdk.readthedocs.io/en/stable/states.html#stepfunctions.steps.states.Chain)
- `stepfunctions.workflow.Workflow`: Class for creating and managing a workflow. [reference](https://aws-step-functions-data-science-sdk.readthedocs.io/en/stable/workflow.html#stepfunctions.workflow.Workflow) 
  
- [[SageMaker SDK Script Processor]]
- Check [[AWS SageMaker Pipeline vs. AWS Step Functions State Machine]] to distinguish *SageMaker Pipeline* with *State Machine*
- Check on how to build BYO container [[SageMaker BYO Container Entry point]]
- Check User Guide on AWS Step Function, and Workflow [[Amazon SageMaker Python SDK 5 Workflow and Step Function]]