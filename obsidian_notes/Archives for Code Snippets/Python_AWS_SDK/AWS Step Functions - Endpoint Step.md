---
tags:
  - code
  - code_snippet
  - python/aws_python_sdk
  - aws/sagemaker
  - aws/step_function
keywords: 
topics: 
language: python
date of note: 2025-05-20
---

## Code Snippet Summary

>[!important]



## Code

```python
!{sys.executable} -m pip install --upgrade stepfunctions
```


### Endpoint Config Step

- `stepfunctions.steps.sagemaker.EndpointConfigStep`
	- [reference](https://aws-step-functions-data-science-sdk.readthedocs.io/en/latest/sagemaker.html#stepfunctions.steps.sagemaker.EndpointConfigStep)
	- Creates a Task State to [create an endpoint configuration in SageMaker](https://docs.aws.amazon.com/sagemaker/latest/dg/API_CreateEndpointConfig.html).
	- **state_id** ([_str_](https://docs.python.org/3.6/library/stdtypes.html#str "(in Python v3.6)")) 
		- State name whose length **must be** less than or equal to 128 unicode characters. State names **must be** unique within the scope of the whole state machine.
	- **endpoint_config_name** ([_str_](https://docs.python.org/3.6/library/stdtypes.html#str "(in Python v3.6)") _or_ [_Placeholder_](https://aws-step-functions-data-science-sdk.readthedocs.io/en/latest/placeholders.html#stepfunctions.inputs.Placeholder "stepfunctions.inputs.Placeholder")) 
		- The name of the endpoint configuration to create. We recommend to use [`ExecutionInput`](https://aws-step-functions-data-science-sdk.readthedocs.io/en/latest/placeholders.html#stepfunctions.inputs.ExecutionInput "stepfunctions.inputs.ExecutionInput") placeholder collection to pass the value dynamically in each execution.
	- **model_name** ([_str_](https://docs.python.org/3.6/library/stdtypes.html#str "(in Python v3.6)") _or_ [_Placeholder_](https://aws-step-functions-data-science-sdk.readthedocs.io/en/latest/placeholders.html#stepfunctions.inputs.Placeholder "stepfunctions.inputs.Placeholder")) 
		- The name of the SageMaker model to attach to the endpoint configuration. We recommend to use [`ExecutionInput`](https://aws-step-functions-data-science-sdk.readthedocs.io/en/latest/placeholders.html#stepfunctions.inputs.ExecutionInput "stepfunctions.inputs.ExecutionInput") placeholder collection to pass the value dynamically in each execution.
	- **initial_instance_count** ([_int_](https://docs.python.org/3.6/library/functions.html#int "(in Python v3.6)") _or_ [_Placeholder_](https://aws-step-functions-data-science-sdk.readthedocs.io/en/latest/placeholders.html#stepfunctions.inputs.Placeholder "stepfunctions.inputs.Placeholder")) 
		- The initial number of instances to run in the `Endpoint` created from this `Model`.
	- 


### Endpoint Step

- `stepfunctions.steps.sagemaker.EndpointStep`
	- [reference](https://aws-step-functions-data-science-sdk.readthedocs.io/en/latest/sagemaker.html#stepfunctions.steps.sagemaker.EndpointStep)





-----------
##  Recommended Notes


- [[AWS Step Functions - One-Step Processing Workflow]]
- Documentation
	- [Build a machine learning workflow using Step Functions and SageMaker](https://sagemaker-examples.readthedocs.io/en/latest/step-functions-data-science-sdk/machine_learning_workflow_abalone/machine_learning_workflow_abalone.html#Build-a-machine-learning-workflow-using-Step-Functions-and-SageMaker)
