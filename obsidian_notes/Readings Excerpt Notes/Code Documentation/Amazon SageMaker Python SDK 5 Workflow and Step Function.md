---
tags:
  - excerpt
  - documentation
  - code_package
  - aws/sagemaker
  - model/pipeline
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

# Workflows

- [AWS Step Functions](https://sagemaker.readthedocs.io/en/stable/workflows/step_functions/index.html)
- [AWS Step Functions Python SDK website](https://aws-step-functions-data-science-sdk.readthedocs.io/en/stable/)
- [Step](https://aws-step-functions-data-science-sdk.readthedocs.io/en/stable/steps.html)

- You can use the [AWS Step Functions Python SDK](https://aws-step-functions-data-science-sdk.readthedocs.io/en/stable/) to easily *create **workflows*** that process and publish machine learning models using **Amazon SageMaker** and **AWS Step Functions**.
  
- You can create **multi-step machine learning workflows** in Python that orchestrate AWS infrastructure at scale, without having to provision and integrate the AWS services separately.

- [Workshop on using AWS Step Functions with SageMaker](https://www.sagemakerworkshop.com/step/)

> [!info]
> You can create machine learning workflows in Python that orchestrate AWS infrastructure at scale, without having to provision and integrate the AWS services separately.
> - **Workflow** - A sequence of steps designed to perform some work
> - **Step** - A unit of work within a workflow
> - **ML Pipeline** - A type of workflow used in data science to create and train machine learning models

## AWS Step Functions Data Science SDK

- The **AWS Step Functions Data Science SDK** is built to PyPI and can be installed with pip as follows.
```python
pip install stepfunctions
```

### Overview of SDK

> [!important]
> The AWS Step Functions Data Science SDK provides a Python API that enables you to create data science and machine learning workflows using AWS Step Functions and SageMaker directly in your Python code and Jupyter notebooks.
> 
> Using this SDK you can:
> 
> 1. **Create steps** that accomplish tasks.
> 2. **Chain** those steps together into **workflows**.
> 3. Include **retry**, **succeed**, or **fail steps**.
> 4. **Review** a **graphical representation** and **definition** for your *workflow*.
> 5. **Create a workflow** in **AWS Step Functions**.
> 6. Start and review **executions** in AWS Step Functions.
> 

### AWS Step Functions

- Using Step Functions, you can design and run workflows that combine services such as Amazon SageMaker, AWS Lambda, and Amazon Elastic Container Service (Amazon ECS), into feature-rich applications. 
  
- **Workflows** are made up of *a series of steps*, with *the output of one step acting as input to the next*.
  
- **The AWS Step Functions Data Science SDK** provides access to **AWS Step Functions** so that you can easily create and run machine learning and data science workflows directly in *Python*, and inside your *Jupyter Notebooks*.
  
- Workflows are created *locally* in Python, but when they are ready for **execution**, the workflow is first uploaded to **the AWS Step Functions** *service* for execution in the cloud.
- When you use the SDK to create, update, or execute workflows you are talking to *the Step Functions service* in the cloud. 
- Your workflows live in *AWS Step Functions* and can be re-used.

>[!info]
> Step Functions creates workflows out of steps called [**States**](https://docs.aws.amazon.com/step-functions/latest/dg/concepts-states.html), and expresses that workflow in the [Amazon States Language](https://docs.aws.amazon.com/step-functions/latest/dg/concepts-amazon-states-language.html). When you create a workflow in the AWS Step Functions Data Science SDK, it creates a **State Machine** representing your *workflow* and *steps* in **AWS Step Functions**.


## Building a Workflow

### Steps

- You create steps using the SDK, and chain them together into *sequential workflows*. Then, you can create those workflows in *AWS Step Functions* and execute them in *Step Functions* directly from your Python code.

>[!example]
> ```python
> # define a pass step
> start_pass_state = Pass(
>     state_id="MyPassState"
> )
> 
> # define a wait step
> wait_state = Wait(
>     state_id="Wait for 3 seconds",
>     seconds=3
> )
> 
> # define a Lambda step, and then defines a Retry and a Catch.
> lambda_state = LambdaStep(
>     state_id="Convert HelloWorld to Base64",
>     parameters={
>         "FunctionName": "MyLambda", #replace with the name of your function
>         "Payload": {
>         "input": "HelloWorld"
>         }
>     }
> )
> 
> lambda_state.add_retry(Retry(
>     error_equals=["States.TaskFailed"],
>     interval_seconds=15,
>     max_attempts=2,
>     backoff_rate=4.0
> ))
> 
> lambda_state.add_catch(Catch(
>     error_equals=["States.TaskFailed"],
>     next_step=Fail("LambdaTaskFailed")
> ))
> ```
> 

- Step 
	- **State** [API reference](https://aws-step-functions-data-science-sdk.readthedocs.io/en/stable/states.html)
	- **Choice Rules** [API reference](https://aws-step-functions-data-science-sdk.readthedocs.io/en/stable/choicerules.html)
	- **Compute** [API reference](https://aws-step-functions-data-science-sdk.readthedocs.io/en/stable/compute.html)
	- **SageMaker** [API reference](https://aws-step-functions-data-science-sdk.readthedocs.io/en/stable/sagemaker.html)
	- **Service Integration** [API reference](https://aws-step-functions-data-science-sdk.readthedocs.io/en/stable/services.html)

### Workflows

- After you define these steps, **chain** them together into a *logical sequence*.

>[!example]
> ```python
> workflow_definition=Chain([start_pass_state, wait_state, lambda_state])
> ```

- Once the steps are chained together, you can define **the workflow definition**.

>[!example]
> ```python
> workflow = Workflow(
>     name="MyWorkflow_v1234",
>     definition=workflow_definition,
>     role=stepfunctions_execution_role
> )
> ```
> 

### Visualizing a Workflow

- The following generates a graphical representation of your workflow.
- Please note that visualization currently only works in Jupyter notebooks.
- Visualization is not available in JupyterLab.

```python
workflow.render_graph(portrait=False)
```

### Review a Workflow Definition

- The following **renders the JSON** of the [Amazon States Language](https://docs.aws.amazon.com/step-functions/latest/dg/concepts-amazon-states-language.html) definition of the workflow you created.
```python
print(workflow.definition.to_json(pretty=True))
```

## Running a Workflow

### Create Workflow on AWS Step Functions

- The following **creates the workflow** in AWS Step Functions.
```python
workflow.create()
```

### Execute the Workflow

- The following **starts an execution** of your workflow in AWS Step Functions.
```python
execution = workflow.execute(inputs={
  "IsHelloWorldExample": True
})
```

### Export an AWS CloudFormation Template

- The following generates an **AWS CloudFormation Template** to *deploy your workflow*.
```python
get_cloudformation_template()
```

- The generated template contains only the **StateMachine** *resource*. 
- To reuse the **CloudFormation template** in a different region, please make sure to update the region specific *AWS resources* (such as the *Lambda ARN* and *Training Image*) in the **StateMachine** *definition*.

- **Workflow** [API reference](https://aws-step-functions-data-science-sdk.readthedocs.io/en/stable/workflow.html)



----------
##  Citations

- Amazon SageMaker Python SDK Documentation [link](https://sagemaker.readthedocs.io/en/stable/index.html)
- [Using the SageMaker Python SDK](https://sagemaker.readthedocs.io/en/stable/overview.html)
- [AWS Step Functions](https://docs.aws.amazon.com/step-functions/latest/dg/welcome.html).
- For more information about Step Functions concepts and use, see the Step Functions [documentation](https://docs.aws.amazon.com/step-functions/index.html).
- [AWS Step Functions Python SDK website](https://aws-step-functions-data-science-sdk.readthedocs.io/en/stable/)
- [Workshop on using AWS Step Functions with SageMaker](https://www.sagemakerworkshop.com/step/)
- [Amazon SageMaker Step Functions Examples](https://sagemaker-examples.readthedocs.io/en/latest/step-functions-data-science-sdk/index.html)
- Amazon SageMaker Workflows [link](https://sagemaker.readthedocs.io/en/stable/workflows/index.html)
- Step 
	- **State** [API reference](https://aws-step-functions-data-science-sdk.readthedocs.io/en/stable/states.html)
	- **Choice Rules** [API reference](https://aws-step-functions-data-science-sdk.readthedocs.io/en/stable/choicerules.html)
	- **Compute** [API reference](https://aws-step-functions-data-science-sdk.readthedocs.io/en/stable/compute.html)
	- **SageMaker** [API reference](https://aws-step-functions-data-science-sdk.readthedocs.io/en/stable/sagemaker.html)
	- **Service Integration** [API reference](https://aws-step-functions-data-science-sdk.readthedocs.io/en/stable/services.html)
- **Workflow** [API reference](https://aws-step-functions-data-science-sdk.readthedocs.io/en/stable/workflow.html)
- **Pipeline** [API reference](https://aws-step-functions-data-science-sdk.readthedocs.io/en/stable/pipelines.html)
- *code source*: [https://github.com/aws/sagemaker-python-sdk](https://github.com/aws/sagemaker-python-sdk)
- *code package link*: 

