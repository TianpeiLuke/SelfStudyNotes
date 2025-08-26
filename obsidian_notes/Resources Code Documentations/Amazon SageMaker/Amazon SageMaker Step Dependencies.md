---
tags:
  - excerpt
  - documentation
  - code_package
  - aws/sagemaker_pipeline
  - aws/sagemaker
  - python/sdk
aliases: 
keywords: 
topics: 
language: python
date of note: 2025-07-22
name: 
version: 
year:
---

##  Excerpt

>[!quote]
>There are two types of step dependencies: a [data dependency](https://docs.aws.amazon.com/sagemaker/latest/dg/build-and-manage-steps.html#build-and-manage-data-dependency) and a [custom dependency](https://docs.aws.amazon.com/sagemaker/latest/dg/build-and-manage-steps.html#build-and-manage-custom-dependency). 
>- To create **data dependencies** between steps, pass the properties or the outputs of one step as the input to another step in the pipeline. This is called property reference. 
>- Alternatively, you can specify a **custom dependency** to make sure that a pipeline execution does not start a new step until all dependent steps are completed.



#### [Data Dependency — Property Reference](https://sagemaker.readthedocs.io/en/v2.92.2/amazon_sagemaker_model_building_pipeline.html#id8)

>[!quote]
>A **step property** is an attribute of a step that represents the output values from a step execution. For example, `TrainingStep.Properties.TrainingJobName` is a property of a [`sagemaker.workflow.steps.TrainingStep`](https://sagemaker.readthedocs.io/en/v2.92.2/workflows/pipelines/sagemaker.workflow.pipelines.html#sagemaker.workflow.steps.TrainingStep "sagemaker.workflow.steps.TrainingStep").

>[!quote]
> For a step that references a SageMaker job (e.g. [`sagemaker.workflow.steps.ProcessingStep`](https://sagemaker.readthedocs.io/en/v2.92.2/workflows/pipelines/sagemaker.workflow.pipelines.html#sagemaker.workflow.steps.ProcessingStep "sagemaker.workflow.steps.ProcessingStep"), [`sagemaker.workflow.steps.TrainingStep`](https://sagemaker.readthedocs.io/en/v2.92.2/workflows/pipelines/sagemaker.workflow.pipelines.html#sagemaker.workflow.steps.TrainingStep "sagemaker.workflow.steps.TrainingStep"), or [`sagemaker.workflow.steps.TransformStep`](https://sagemaker.readthedocs.io/en/v2.92.2/workflows/pipelines/sagemaker.workflow.pipelines.html#sagemaker.workflow.steps.TransformStep "sagemaker.workflow.steps.TransformStep")), the **step property** matches the *attributes* of that SageMaker job. 
> - For example, [`sagemaker.workflow.steps.TrainingStep`](https://sagemaker.readthedocs.io/en/v2.92.2/workflows/pipelines/sagemaker.workflow.pipelines.html#sagemaker.workflow.steps.TrainingStep "sagemaker.workflow.steps.TrainingStep"). properties match the attributes that result from calling `DescribeTrainingJob`. `TrainingJobName` is an attribute from a `DescribeTrainingJob` result. 
> - Therefore, `TrainingJobName` is a [`sagemaker.workflow.steps.TrainingStep`](https://sagemaker.readthedocs.io/en/v2.92.2/workflows/pipelines/sagemaker.workflow.pipelines.html#sagemaker.workflow.steps.TrainingStep "sagemaker.workflow.steps.TrainingStep") property, and can be referenced as `TrainingStep.Properties.TrainingJobName`.
> 
>You can build data dependencies from one step to another using this kind of property reference. These data dependencies are then used by SageMaker Pipelines to construct the directed acyclic graph (DAG) from the pipeline definition. These properties can be referenced as placeholder values and are resolved at runtime.

For each step type you can refer to the following properties for data dependency creation:

##### [TrainingStep](https://sagemaker.readthedocs.io/en/v2.92.2/amazon_sagemaker_model_building_pipeline.html#id9)

Referable Property List:

- [DescribeTrainingJob](https://docs.aws.amazon.com/sagemaker/latest/APIReference/API_DescribeTrainingJob.html#API_DescribeTrainingJob_ResponseSyntax)
    


>[!example]
>Example:
> ```python
> step_train = TrainingStep(...)
> model = Model(
>     image_uri="my-dummy-image",
>     model_data=step_train.properties.ModelArtifacts.S3ModelArtifacts,
>     ...
> )
> # assume your training job will produce a metric called "val:acc"
> # and you would like to use it to demtermine if you want to create
> # a SageMaker Model for it.
> step_condition = ConditionStep(
>     conditions = [
>         ConditionGreaterThanOrEqualTo(
>             left=step_train.properties.FinalMetricDataList['val:acc'].Value
>             right=0.95
>     )],
>     if_steps = [step_model_create],
> )
> ```


##### [ProcessingStep](https://sagemaker.readthedocs.io/en/v2.92.2/amazon_sagemaker_model_building_pipeline.html#id10)

Referable Property List:

- [DescribeProcessingJob](https://docs.aws.amazon.com/sagemaker/latest/APIReference/API_DescribeProcessingJob.html#API_DescribeProcessingJob_ResponseSyntax)

>[!example]
> ```python
> sklearn_processor = SKLearnProcessor(
>     framework_version="0.23-1",
>     instance_type="ml.m5.xlarge",
>     instance_count=1,
>     base_job_name="sklearn-abalone-preprocess",
>     sagemaker_session=PipelineSession(),
>     role=sagemaker.get_execution_role(),
> )
> 
> step_process = ProcessingStep(
>     name="MyProcessingStep",
>     ...,
>     step_args = sklearn_processor.run(
>         ...,
>         outputs=[
>             ProcessingOutput(output_name="train", source="/opt/ml/processing/train"),
>         ],
>         code="./local/preprocess.py",
>         job_arguments=["--input-data", "s3://my-input"]
>     ),
> )
> 
> step_args = estimator.fit(inputs=TrainingInput(
>     s3_data=step_process.properties.ProcessingOutputConfig.Outputs["train"].S3Output.S3Uri,
> ))
> ```

##### [TransformStep](https://sagemaker.readthedocs.io/en/v2.92.2/amazon_sagemaker_model_building_pipeline.html#id11)[](https://sagemaker.readthedocs.io/en/v2.92.2/amazon_sagemaker_model_building_pipeline.html#transformstep "Permalink to this headline")

Referable Property List:

[DescribeTransformJob](https://docs.aws.amazon.com/sagemaker/latest/APIReference/API_DescribeTransformJob.html#API_DescribeTransformJob_ResponseSyntax)

>[!example]
> ```python
> step_transform = TransformStep(...)
> 
> transform_output = step_transform.TransformOutput.S3OutputPath
> ```


##### [TuningStep](https://sagemaker.readthedocs.io/en/v2.92.2/amazon_sagemaker_model_building_pipeline.html#id12)

Referable Property List:

- [DescribeHyperParameterTuningJob](https://docs.aws.amazon.com/sagemaker/latest/APIReference/API_DescribeHyperParameterTuningJob.html#API_DescribeHyperParameterTuningJob_ResponseSyntax)
    
- [ListTrainingJobsForHyperParameterTuningJob](https://docs.aws.amazon.com/sagemaker/latest/APIReference/API_ListTrainingJobsForHyperParameterTuningJob.html#API_ListTrainingJobsForHyperParameterTuningJob_ResponseSyntax)
    

>[!example]
>Example:
> 
> ```python
> step_tune = TuningStep(...)
> # tuning step can launch multiple training jobs, thus producing multiple model artifacts
> # we can create a model with the best performance
> best_model = Model(
>     model_data=Join(
>         on="/",
>         values=[
>             "s3://my-bucket",
>             # from DescribeHyperParameterTuningJob
>             step_tune.properties.BestTrainingJob.TrainingJobName,
>             "output/model.tar.gz",
>         ],
> )
> # we can also access any top-k best as we wish
> second_best_model = Model(
>     model_data=Join(
>         on="/",
>         values=[
>             "s3://my-bucket",
>             # from ListTrainingJobsForHyperParameterTuningJob
>             step_tune.properties.TrainingJobSummaries[1].TrainingJobName,
>             "output/model.tar.gz",
>         ],
> )
> ```

[`sagemaker.workflow.steps.TuningStep`](https://sagemaker.readthedocs.io/en/v2.92.2/workflows/pipelines/sagemaker.workflow.pipelines.html#sagemaker.workflow.steps.TuningStep "sagemaker.workflow.steps.TuningStep") also has a helper function to generate any `top-k` model data URI easily:

```python
model_data = step_tune.get_top_model_s3_uri(
    top_k=0, # best model
    s3_bucket="s3://my-bucekt",
)
```

##### [CreateModelStep](https://sagemaker.readthedocs.io/en/v2.92.2/amazon_sagemaker_model_building_pipeline.html#id13)

Referable Property List:

- [DescribeModel](https://docs.aws.amazon.com/sagemaker/latest/APIReference/API_DescribeModel.html#API_DescribeModel_ResponseSyntax)
    

>[!example]
>Example:

step_model = CreateModelStep(...)
model_data = step_model.PrimaryContainer.ModelDataUrl

##### [LambdaStep](https://sagemaker.readthedocs.io/en/v2.92.2/amazon_sagemaker_model_building_pipeline.html#id14)[](https://sagemaker.readthedocs.io/en/v2.92.2/amazon_sagemaker_model_building_pipeline.html#lambdastep "Permalink to this headline")

Referable Property List:

- `OutputParameters`: A list of key-value pairs [OutputParameter](https://docs.aws.amazon.com/sagemaker/latest/APIReference/API_OutputParameter.html) as the output of the Lambda execution.
    

Example:

str_outputParam = LambdaOutput(output_name="output1", output_type=LambdaOutputTypeEnum.String)
int_outputParam = LambdaOutput(output_name"output2", output_type=LambdaOutputTypeEnum.Integer)
bool_outputParam = LambdaOutput(output_name"output3", output_type=LambdaOutputTypeEnum.Boolean)
float_outputParam = LambdaOutput(output_name"output4", output_type=LambdaOutputTypeEnum.Float)

step_lambda = LambdaStep(
    name="MyLambdaStep",
    lambda_func=Lambda(
        function_arn="arn:aws:lambda:us-west-2:123456789012:function:sagemaker_test_lambda",
        session=PipelineSession(),
    ),
    inputs={"arg1": "foo", "arg2": 5},
    outputs=[
        str_outputParam, int_outputParam, bool_outputParam, float_outputParam
   ],
)
output_ref = step_lambda.OutputParameters["output1"]

Where the lambda function with `arn arn:aws:lambda:us-west-2:123456789012:function:sagemaker_test_lambda` should output like this:

def handler(event, context):
    ...
    return {
        "output1": "string_value",
        "output2": 1,
        "output3": True,
        "output4": 2.0,
    }

Note that the output parameters can not be nested. Otherwise, the value will be treated as a single string. For instance, if your lambda outputs

{
    "output1": {
        "nested_output1": "my-output"
    }
}

This will be resolved as `{"output1": "{\"nested_output1\":\"my-output\"}"}` by which if you refer `step_lambda.OutputParameters["output1"]["nested_output1"]` later, a non-retryable client error will be thrown.

##### [CallbackStep](https://sagemaker.readthedocs.io/en/v2.92.2/amazon_sagemaker_model_building_pipeline.html#id15)[](https://sagemaker.readthedocs.io/en/v2.92.2/amazon_sagemaker_model_building_pipeline.html#callbackstep "Permalink to this headline")

Referable Property List:

- `OutputParameters`: A list of key-value pairs [OutputParameter](https://docs.aws.amazon.com/sagemaker/latest/APIReference/API_OutputParameter.html) defined by [SendPipelineExecutionStepSuccess](https://docs.aws.amazon.com/sagemaker/latest/APIReference/API_SendPipelineExecutionStepSuccess.htmlcall.) call.
    

Example:

param = ParameterInteger(name="MyInt")
outputParam = CallbackOutput(output_name="output1", output_type=CallbackOutputTypeEnum.String)
step_callback = CallbackStep(
    name="MyCallbackStep",
    depends_on=["TestStep"],
    sqs_queue_url="https://sqs.us-east-2.amazonaws.com/123456789012/MyQueue",
    inputs={"arg1": "foo", "arg2": 5, "arg3": param},
    outputs=[outputParam],
)
output_ref = step_callback.OutputParameters["output1]

The output parameters cannot be nested. If the values are nested, they will be treated as a single string value. For example, a nested output value of

{
    "output1": {
        "nested_output1": "my-output"
    }
}

is resolved as `{"output1": "{\"nested_output1\":\"my-output\"}"}`. If you try to refer to `step_callback.OutputParameters["output1"]["nested_output1"]` this will throw a non-retryable client error.

##### [QualityCheckStep](https://sagemaker.readthedocs.io/en/v2.92.2/amazon_sagemaker_model_building_pipeline.html#id16)[](https://sagemaker.readthedocs.io/en/v2.92.2/amazon_sagemaker_model_building_pipeline.html#qualitycheckstep "Permalink to this headline")

Referable Property List:

- `CalculatedBaselineConstraints`: The baseline constraints file calculated by the underlying Model Monitor container.
    
- `CalculatedBaselineStatistics`: The baseline statistics file calculated by the underlying Model Monitor container.
    
- `BaselineUsedForDriftCheckStatistics & BaselineUsedForDriftCheckConstraints`: These are the two properties used to set drift_check_baseline in the Model Registry. The values set in these properties vary depending on the parameters passed to the step.
    

##### [ClarifyCheckStep](https://sagemaker.readthedocs.io/en/v2.92.2/amazon_sagemaker_model_building_pipeline.html#id17)[](https://sagemaker.readthedocs.io/en/v2.92.2/amazon_sagemaker_model_building_pipeline.html#clarifycheckstep "Permalink to this headline")

Referable Property List:

- `CalculatedBaselineConstraints`: The baseline constraints file calculated by the underlying Clarify container.
    
- `BaselineUsedForDriftCheckConstraints`: This property is used to set drift_check_baseline in the Model Registry. The values set in this property will vary depending on the parameters passed to the step.
    

More examples about QualityCheckStep and ClarifyCheckStep can be found in [SageMaker Pipelines integration with Model Monitor and Clarify](https://github.com/aws/amazon-sagemaker-examples/tree/main/sagemaker-pipelines/tabular/model-monitor-clarify-pipelines) notebook

##### [EMRStep](https://sagemaker.readthedocs.io/en/v2.92.2/amazon_sagemaker_model_building_pipeline.html#id18)[](https://sagemaker.readthedocs.io/en/v2.92.2/amazon_sagemaker_model_building_pipeline.html#emrstep "Permalink to this headline")

Referable Property List:

- `ClusterId`: The Id of the EMR cluster.
    

You can see more details at [AWS official developer guide for Step Introductions](https://docs.aws.amazon.com/sagemaker/latest/dg/build-and-manage-steps.html)

#### [Custom Dependency](https://sagemaker.readthedocs.io/en/v2.92.2/amazon_sagemaker_model_building_pipeline.html#id19)[](https://sagemaker.readthedocs.io/en/v2.92.2/amazon_sagemaker_model_building_pipeline.html#id1 "Permalink to this headline")

To build a custom dependency, simply add the desired step or steps to another step’s `depends_on` attribute as follows:

step_1 = ProcessingStep(
    name="MyProcessingStep",
    step_args=sklearn_processor.run(
        inputs=inputs,
        code="./my-local/my-first-script.py"
    ),
)

step_2 = ProcessingStep(
    name="MyProcessingStep",
    step_args=sklearn_processor.run(
        inputs=inputs,
        code="./my-local/my-second-script.py"
    ),
    depends_on=[step_1.name],
)

In this case, `step_2` will start only when `step_1` is done.

### [Property File](https://sagemaker.readthedocs.io/en/v2.92.2/amazon_sagemaker_model_building_pipeline.html#id20)[](https://sagemaker.readthedocs.io/en/v2.92.2/amazon_sagemaker_model_building_pipeline.html#property-file "Permalink to this headline")

A [`sagemaker.workflow.properties.PropertyFile`](https://sagemaker.readthedocs.io/en/v2.92.2/workflows/pipelines/sagemaker.workflow.pipelines.html#sagemaker.workflow.properties.PropertyFile "sagemaker.workflow.properties.PropertyFile") is designed to store information that is output from [`sagemaker.workflow.steps.ProcessingStep`](https://sagemaker.readthedocs.io/en/v2.92.2/workflows/pipelines/sagemaker.workflow.pipelines.html#sagemaker.workflow.steps.ProcessingStep "sagemaker.workflow.steps.ProcessingStep"). The [`sagemaker.workflow.functions.JsonGet`](https://sagemaker.readthedocs.io/en/v2.92.2/workflows/pipelines/sagemaker.workflow.pipelines.html#sagemaker.workflow.functions.JsonGet "sagemaker.workflow.functions.JsonGet") function processes a property file . You can use JsonPath notation to query the information.

sklearn_processor = SKLearnProcessor(
    framework_version="0.23-1",
    instance_type="ml.m5.xlarge",
    instance_count=1,
    base_job_name="sklearn-abalone-preprocess",
    sagemaker_session=session,
    role=sagemaker.get_execution_role(),
)

step_args = sklearn_processor.run(
    outputs=[
        ProcessingOutput(output_name="train", source="/opt/ml/processing/train"),
        ProcessingOutput(output_name="validation", source="/opt/ml/processing/validation"),
        ProcessingOutput(output_name="test", source="/opt/ml/processing/test"),
        ProcessingOutput(output_name="hyperparam", source="/opt/ml/processing/evaluation"),
    ],
    code="./local/preprocess.py",
    job_arguments=["--input-data", "s3://my-input"],
)

hyperparam_report = PropertyFile(
    name="AbaloneHyperparamReport",
    output_name="hyperparam",
    path="hyperparam.json",
)

step_process = ProcessingStep(
   name="PreprocessAbaloneData",
   step_args=step_args,
   property_files=[hyperparam_report],
)

To retrieve a file produced by the [`sagemaker.workflow.steps.ProcessingStep`](https://sagemaker.readthedocs.io/en/v2.92.2/workflows/pipelines/sagemaker.workflow.pipelines.html#sagemaker.workflow.steps.ProcessingStep "sagemaker.workflow.steps.ProcessingStep") as a property file, the `ProcessingOutput.output_name` and the `PropertyFile.output_name` values must be the same. For this example, assume that the `hyperparam.json` value produced by the ProcessingStep in the `/opt/ml/processing/evaluation` directory looks similar to the following:

{
    "hyperparam": {
        "eta": {
            "value": 0.6
        }
    }
}

Then, you can query this value using [`sagemaker.workflow.functions.JsonGet`](https://sagemaker.readthedocs.io/en/v2.92.2/workflows/pipelines/sagemaker.workflow.pipelines.html#sagemaker.workflow.functions.JsonGet "sagemaker.workflow.functions.JsonGet") and use the value for any subsequent steps:

eta = JsonGet(
 step_name=step_process.name,
 property_file=hyperparam_report,
 json_path="hyperparam.eta.value",
)

### [Conditions](https://sagemaker.readthedocs.io/en/v2.92.2/amazon_sagemaker_model_building_pipeline.html#id21)[](https://sagemaker.readthedocs.io/en/v2.92.2/amazon_sagemaker_model_building_pipeline.html#conditions "Permalink to this headline")

Condition step is used to evaluate the condition of step properties to assess which action should be taken next in the pipeline. It takes a list of conditions, and a list steps to execute if all conditions are evaluated to be true, and another list of steps to execute otherwise. For instance:

step_condition = ConditionStep(
    # The conditions are evaluated with operator AND
    conditions = [condition_1, condition_2, condition_3, condition_4],
    if_steps = [step_register],
    else_steps = [step_fail],
)

There are eight types of condition are supported, they are:

- [`sagemaker.workflow.conditions.ConditionEquals`](https://sagemaker.readthedocs.io/en/v2.92.2/workflows/pipelines/sagemaker.workflow.pipelines.html#sagemaker.workflow.conditions.ConditionEquals "sagemaker.workflow.conditions.ConditionEquals")
    
- [`sagemaker.workflow.conditions.ConditionGreaterThan`](https://sagemaker.readthedocs.io/en/v2.92.2/workflows/pipelines/sagemaker.workflow.pipelines.html#sagemaker.workflow.conditions.ConditionGreaterThan "sagemaker.workflow.conditions.ConditionGreaterThan")
    
- [`sagemaker.workflow.conditions.ConditionGreaterThanOrEqualTo`](https://sagemaker.readthedocs.io/en/v2.92.2/workflows/pipelines/sagemaker.workflow.pipelines.html#sagemaker.workflow.conditions.ConditionGreaterThanOrEqualTo "sagemaker.workflow.conditions.ConditionGreaterThanOrEqualTo")
    
- [`sagemaker.workflow.conditions.ConditionLessThan`](https://sagemaker.readthedocs.io/en/v2.92.2/workflows/pipelines/sagemaker.workflow.pipelines.html#sagemaker.workflow.conditions.ConditionLessThan "sagemaker.workflow.conditions.ConditionLessThan")
    
- [`sagemaker.workflow.conditions.ConditionLessThanOrEqualTo`](https://sagemaker.readthedocs.io/en/v2.92.2/workflows/pipelines/sagemaker.workflow.pipelines.html#sagemaker.workflow.conditions.ConditionLessThanOrEqualTo "sagemaker.workflow.conditions.ConditionLessThanOrEqualTo")
    
- [`sagemaker.workflow.conditions.ConditionIn`](https://sagemaker.readthedocs.io/en/v2.92.2/workflows/pipelines/sagemaker.workflow.pipelines.html#sagemaker.workflow.conditions.ConditionIn "sagemaker.workflow.conditions.ConditionIn")
    
- [`sagemaker.workflow.conditions.ConditionNot`](https://sagemaker.readthedocs.io/en/v2.92.2/workflows/pipelines/sagemaker.workflow.pipelines.html#sagemaker.workflow.conditions.ConditionNot "sagemaker.workflow.conditions.ConditionNot")
    
- [`sagemaker.workflow.conditions.ConditionOr`](https://sagemaker.readthedocs.io/en/v2.92.2/workflows/pipelines/sagemaker.workflow.pipelines.html#sagemaker.workflow.conditions.ConditionOr "sagemaker.workflow.conditions.ConditionOr")
    

[`sagemaker.workflow.properties.PropertyFile`](https://sagemaker.readthedocs.io/en/v2.92.2/workflows/pipelines/sagemaker.workflow.pipelines.html#sagemaker.workflow.properties.PropertyFile "sagemaker.workflow.properties.PropertyFile") and [`sagemaker.workflow.functions.JsonGet`](https://sagemaker.readthedocs.io/en/v2.92.2/workflows/pipelines/sagemaker.workflow.pipelines.html#sagemaker.workflow.functions.JsonGet "sagemaker.workflow.functions.JsonGet") introduced above is particularly handy when used together with conditions. Here is an example:

step_train = TrainingStep(...)
model = Model(
    image_uri="my-dummy-image",
    model_data=step_train.properties.ModelArtifacts.S3ModelArtifacts,
    ...
)

step_args = sklearn_processor.run(
    outputs=[
        ProcessingOutput(output_name="train", source="/opt/ml/processing/train"),
        ProcessingOutput(output_name="validation", source="/opt/ml/processing/validation"),
        ProcessingOutput(output_name="test", source="/opt/ml/processing/test"),
        ProcessingOutput(output_name="hyperparam", source="/opt/ml/processing/evaluation"),
    ],
    code="./local/preprocess.py",
    job_arguments=["--input-data", "s3://my-input"],
)

eval_report = PropertyFile(
    name="AbaloneHyperparamReport",
    output_name="hyperparam",
    path="hyperparam.json",
)

step_process = ProcessingStep(
    name="PreprocessAbaloneData",
    step_args=step_args,
    property_files=[eval_report],
)

eval_score = JsonGet(
    step_name=step_process.name,
    property_file=eval_report,
    json_path="eval.accuracy",
)

# register the model if evaluation score is satisfactory
register_arg = model.register(
    content_types=["application/json"],
    response_types=["application/json"],
    inference_instances=["ml.m5.large"],
    transform_instances=["ml.m5.large"],
    model_package_group_name="my-model-pkg-name",
    approval_status="Approved",
)
step_register = ModelStep(
    name="MyModelCreationStep",
    step_args=register_arg,
)
# otherwise, transit to a failure step
step_fail = FailStep(name="FailStep", ...)

cond = ConditionStep(
   conditions = [ConditionGreaterThanOrEqualTo(left=eval_score, right=0.95)],
   if_steps = [step_register],
   else_steps = [step_fail],
)


-----------
##  Recommended Notes

- SageMaker Python SDK 
	- [data-dependency-property-reference](https://sagemaker.readthedocs.io/en/v2.92.2/amazon_sagemaker_model_building_pipeline.html#data-dependency-property-reference)

- API Reference 
	- [DescribeTrainingJob](https://docs.aws.amazon.com/sagemaker/latest/APIReference/API_DescribeTrainingJob.html#sagemaker-DescribeTrainingJob-response-OutputDataConfig)
	- [API_OutputDataConfig](https://docs.aws.amazon.com/sagemaker/latest/APIReference/API_OutputDataConfig.html)



----------
##  Citations

- *code source*:
- *code package link*




