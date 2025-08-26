---
tags:
  - project
  - design/standardization
  - documentation
  - aws/sagemaker_pipeline
aliases: 
date of note: 2025-07-16
---

>[!important]
>This document centralizes all alignment guidance for pipeline step development. Refer to this file whenever you need to ensure consistency across script contracts, step specifications, and step builders.

## Alignment Principles

1. **Script ↔ Contract**  
   - Scripts must use exactly the paths defined in their Script Contract.  
   - Environment variable names, input/output directory structures, and file patterns must match the contract.

2. **Contract ↔ Specification**  
   - Logical names in the Script Contract (`expected_input_paths`, `expected_output_paths`) must match dependency names in the Step Specification.  
   - Property paths in `OutputSpec` must correspond to the contract’s output paths.

3. **Specification ↔ Dependencies**  
   - Dependencies declared in the Step Specification must match upstream step outputs by logical name or alias.  
   - `DependencySpec.compatible_sources` must list all steps that produce the required output.

4. **Builder ↔ Configuration**  
   - Step Builders must pass configuration parameters to SageMaker components according to the config class.  
   - Environment variables set in the builder (`_get_processor_env_vars`) must cover all `required_env_vars` from the contract.

## Examples

### Script ↔ Contract

```python
from src.pipeline_script_contracts.tabular_preprocess_contract import TABULAR_PREPROCESS_CONTRACT

# Script path must match contract exactly
input_path = TABULAR_PREPROCESS_CONTRACT.expected_input_paths["DATA"] + "/file.csv"
assert "/opt/ml/processing/input/data" in input_path
```

### Contract ↔ Specification

```python
from src.pipeline_step_specs.step_specification import StepSpecification, DependencySpec

spec = StepSpecification(
    step_type="TabularPreprocessing",
    dependencies={
        "DATA": DependencySpec(
            logical_name="DATA",
            compatible_sources=["CradleDataLoading"]
        )
    },
    outputs={}
)
assert "DATA" in spec.dependencies
```

### Specification ↔ Dependencies

```python
from src.pipeline_step_specs.step_specification import StepSpecification, DependencySpec, OutputSpec
from src.pipeline_deps.dependency_resolver import UnifiedDependencyResolver

# Define a spec with dependency and output
spec = StepSpecification(
    step_type="XGBoostTraining",
    dependencies={
        "training_data": DependencySpec(
            logical_name="training_data",
            compatible_sources=["TabularPreprocessing"]
        )
    },
    outputs={
        "training_data": OutputSpec(
            logical_name="training_data",
            property_path="properties.ProcessingOutputConfig.Outputs['ProcessedTabularData'].S3Output.S3Uri"
        )
    }
)
# Resolve using a registry and available steps list
resolver = UnifiedDependencyResolver(spec_registry)
matches = resolver.find_compatible_sources(
    spec.dependencies["training_data"],
    available_steps
)
assert any(m.step.step_type == "TabularPreprocessing" for m in matches)
```

### Builder ↔ Configuration

```python
from src.pipeline_steps.builder_tabular_preprocessing_step import TabularPreprocessingStepBuilder
from src.pipeline_script_contracts.tabular_preprocess_contract import TABULAR_PREPROCESS_CONTRACT

builder = TabularPreprocessingStepBuilder(config_instance)
env_vars = builder._get_processor_env_vars()
for var in TABULAR_PREPROCESS_CONTRACT.required_env_vars:
    assert var in env_vars
```

### Real-World Examples

#### Script Implementation Example

```python
# nlp-pipeline/dockers/xgboost_atoz/pipeline_scripts/tabular_preprocess.py
from src.pipeline_script_contracts.tabular_preprocess_contract import TABULAR_PREPROCESS_CONTRACT

def main():
    # Use contract paths
    input_dir = TABULAR_PREPROCESS_CONTRACT.expected_input_paths["DATA"]
    output_dir = TABULAR_PREPROCESS_CONTRACT.expected_output_paths["processed_data"]
    # e.g. "/opt/ml/processing/input/data" and "/opt/ml/processing/output"
    print(f"Reading from {input_dir}, writing to {output_dir}")
```

#### Step Specification Example

```python
# src/pipeline_step_specs/tabular_preprocess_spec.py
from src.pipeline_deps.base_specifications import StepSpecification, DependencySpec, OutputSpec
from src.pipeline_script_contracts.tabular_preprocess_contract import TABULAR_PREPROCESS_CONTRACT

TABULAR_PREPROCESS_SPEC = StepSpecification(
    step_type="TabularPreprocessing",
    script_contract=TABULAR_PREPROCESS_CONTRACT,
    dependencies={
        "DATA": DependencySpec(
            logical_name="DATA",
            compatible_sources=["CradleDataLoading"]
        )
    },
    outputs={
        "processed_data": OutputSpec(
            logical_name="processed_data",
            property_path="properties.ProcessingOutputConfig.Outputs['ProcessedTabularData'].S3Output.S3Uri"
        )
    }
)
assert "DATA" in TABULAR_PREPROCESS_SPEC.dependencies
```

#### Builder Implementation Example

```python
# src/pipeline_steps/builder_tabular_preprocessing_step.py
from src.pipeline_steps.builder_tabular_preprocessing_step import TabularPreprocessingStepBuilder

builder = TabularPreprocessingStepBuilder(config_instance)
inputs = builder._get_inputs({"DATA": "s3://bucket/data"})
assert inputs[0].destination == "/opt/ml/processing/input/data"
```

#### Model Evaluation Builder Example

```python
# src/pipeline_steps/builder_model_eval_step_xgboost.py
from src.pipeline_steps.builder_model_eval_step_xgboost import XGBoostModelEvalStepBuilder
from src.pipeline_steps.config_model_eval_step_xgboost import XGBoostModelEvalConfig

# Instantiate config with required fields
config = XGBoostModelEvalConfig(
    region="us-west-2",
    pipeline_s3_loc="s3://bucket/prefix",
    processing_entry_point="model_evaluation_xgb.py",
    processing_source_dir="src/pipeline_scripts",
    processing_instance_count=1,
    processing_volume_size=30,
    processing_instance_type_large="ml.m5.4xlarge",
    processing_instance_type_small="ml.m5.xlarge",
    use_large_processing_instance=False,
    pipeline_name="test-pipeline",
    job_type="evaluation",
    hyperparameters=...,
    xgboost_framework_version="1.7-1"
)
builder = XGBoostModelEvalStepBuilder(config)
env_vars = builder._get_environment_variables()
assert "LABEL_FIELD" in env_vars and "ID_FIELD" in env_vars
```

#### XGBoost Training Script Contract Example

```python
# src/pipeline_script_contracts/xgboost_train_contract.py
from src.pipeline_script_contracts.xgboost_train_contract import XGBOOST_TRAIN_CONTRACT

# Verify entry point and input paths
assert XGBOOST_TRAIN_CONTRACT.entry_point == "train_xgb.py"
assert "train_data" in XGBOOST_TRAIN_CONTRACT.expected_input_paths
```


## Usage

- When creating or modifying a script contract, update the corresponding Section in this file.  
- When defining a new Step Specification, validate alignment against this document.  
- Step Builders should include a validation check against these rules in unit tests.


-----------
##  Recommended Notes

- [Validation Checklist](Validation%20Checklist.md)  
- [Common Pitfalls](Common%20Pitfalls%20to%20Avoid.md)