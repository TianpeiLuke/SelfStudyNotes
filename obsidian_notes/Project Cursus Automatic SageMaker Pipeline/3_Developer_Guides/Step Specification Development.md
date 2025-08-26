---
tags:
  - project
  - design/design_architecture
  - aws/sagemaker_pipeline
  - documentation
aliases: 
date of note: 2025-07-16
---
Step specifications define how your step connects with other steps in the pipeline. They provide the metadata needed for automatic dependency resolution, semantic matching, and pipeline assembly.

## Purpose of Step Specifications

Step specifications serve several important purposes:

1. **Declarative Metadata**: They provide a declarative way to define what a step is and how it connects
2. **Dependency Management**: They define the inputs needed from other steps and outputs provided to others
3. **Semantic Matching**: They enable intelligent matching between producer and consumer steps
4. **Validation Rules**: They enforce architectural constraints at design time
5. **Pipeline Topology**: They define the step's role in the pipeline (source, internal, sink)

## Specification Structure

A step specification is defined using the `StepSpecification` class and includes the following key components:

```python
from typing import Dict, List, Optional

from ..pipeline_deps.base_specifications import StepSpecification, NodeType, DependencySpec, OutputSpec, DependencyType
from ..pipeline_script_contracts.your_script_contract import YOUR_SCRIPT_CONTRACT
from ..pipeline_registry.step_names import get_spec_step_type

def _get_your_script_contract():
    """Get the script contract for this step."""
    from ..pipeline_script_contracts.your_script_contract import YOUR_SCRIPT_CONTRACT
    return YOUR_SCRIPT_CONTRACT

YOUR_STEP_SPEC = StepSpecification(
    step_type=get_spec_step_type("YourStepName"),
    node_type=NodeType.INTERNAL,
    script_contract=_get_your_script_contract(),
    dependencies={
        "input_data": DependencySpec(
            logical_name="input_data",
            dependency_type=DependencyType.PROCESSING_OUTPUT,
            required=True,
            compatible_sources=["PreviousStep", "AlternativeStep"],
            semantic_keywords=["data", "input", "features"],
            data_type="S3Uri",
            description="Input data for processing"
        )
    },
    outputs={
        "output_data": OutputSpec(
            logical_name="output_data",
            output_type=DependencyType.PROCESSING_OUTPUT,
            property_path="properties.ProcessingOutputConfig.Outputs['output_data'].S3Output.S3Uri",
            aliases=["processed_data", "transformed_data"],
            data_type="S3Uri",
            description="Processed output data"
        )
    }
)
```

### Critical Fields in Step Specification

| Field | Critical? | Description | How to Determine |
|-------|----------|-------------|-----------------|
| `step_type` | ✅ Required | Step identifier | Use `get_spec_step_type("YourStepName")` |
| `node_type` | ✅ Required | Position in DAG | Usually `NodeType.INTERNAL` |
| `script_contract` | ✅ Required | Script interface | Reference your script contract |
| `dependencies` | ✅ Required | Inputs from other steps | Analyze what your step needs |
| `outputs` | ✅ Required | Outputs for next steps | Analyze what your step produces |

## How to Develop a Step Specification

### 1. Choose the Node Type

The node type defines the step's position in the pipeline topology:

- **NodeType.SOURCE**: Entry point steps with no dependencies (e.g., data loading)
- **NodeType.INTERNAL**: Processing steps with both dependencies and outputs
- **NodeType.SINK**: Terminal steps that consume but don't produce outputs (e.g., registration)

### 2. Define Dependencies

Dependencies define what your step needs from other steps. For each input your script requires:

1. **Identify Upstream Steps**: Which steps can produce this input?
2. **Determine Logical Name**: Choose a descriptive name (matching script contract)
3. **Set Dependency Type**: Specify the type of dependency (processing output, model artifacts, etc.)
4. **Mark Required/Optional**: Is this input required or optional?
5. **Define Compatible Sources**: List step types that can provide this input
6. **Add Semantic Keywords**: Keywords for semantic matching

Example dependency specification:

```python
"processed_data": DependencySpec(
    logical_name="processed_data",
    dependency_type=DependencyType.PROCESSING_OUTPUT,
    required=True,
    compatible_sources=["TabularPreprocessing", "FeatureEngineering"],
    semantic_keywords=["tabular", "processed", "features"],
    data_type="S3Uri",
    description="Processed tabular data for model training"
)
```

### 3. Define Outputs

Outputs define what your step produces for other steps. For each output your script generates:

1. **Choose Logical Name**: A descriptive name (matching script contract)
2. **Set Output Type**: Specify the type of output
3. **Define Property Path**: Path to the output in SageMaker step
4. **Add Optional Aliases**: Alternative names for backward compatibility
5. **Document Data Type**: Format of the output data

Example output specification:

```python
"model_artifacts": OutputSpec(
    logical_name="model_artifacts",
    output_type=DependencyType.MODEL_ARTIFACTS,
    property_path="properties.ModelArtifacts.S3ModelArtifacts",
    aliases=["model", "trained_model"],
    data_type="S3Uri",
    description="Trained model artifacts"
)
```

### 4. Connect to Script Contract

Link the specification to your script contract:

```python
def _get_your_script_contract():
    """Get the script contract for this step."""
    from ..pipeline_script_contracts.your_script_contract import YOUR_SCRIPT_CONTRACT
    return YOUR_SCRIPT_CONTRACT

YOUR_STEP_SPEC = StepSpecification(
    # Other fields...
    script_contract=_get_your_script_contract(),
    # Other fields...
)
```

### 5. Support Job Type Variants (If Needed)

For steps that need job type variants (training, calibration, etc.):

```python
# Define variants with different compatible sources or dependencies
YOUR_STEP_TRAINING_SPEC = StepSpecification(
    # Training-specific specification
)

YOUR_STEP_CALIBRATION_SPEC = StepSpecification(
    # Calibration-specific specification
)

# Provide a function to select the appropriate specification
def get_your_step_spec(job_type: str = None):
    """Get the appropriate specification based on job type."""
    if job_type and job_type.lower() == "calibration":
        return YOUR_STEP_CALIBRATION_SPEC
    else:
        return YOUR_STEP_TRAINING_SPEC  # Default to training
```

## Step-to-Step Alignment

### Analyzing Upstream Steps

To ensure proper alignment with upstream steps:

1. **Examine the upstream step's outputs**:

```python
# Load the upstream step's specification
from src.pipeline_step_specs.upstream_step_spec import UPSTREAM_STEP_SPEC

# Examine its outputs
for output_name, output_spec in UPSTREAM_STEP_SPEC.outputs.items():
    print(f"Output: {output_name}")
    print(f"  Logical Name: {output_spec.logical_name}")
    print(f"  Type: {output_spec.output_type}")
    print(f"  Data Type: {output_spec.data_type}")
```

2. **Match your dependencies to upstream outputs**:

```python
# Example: If upstream output is:
#   "processed_data": OutputSpec(
#       logical_name="processed_data",
#       output_type=DependencyType.PROCESSING_OUTPUT,
#       ...
#   )

# Your matching dependency should be:
"training_data": DependencySpec(
    logical_name="training_data",
    dependency_type=DependencyType.PROCESSING_OUTPUT,  # Match the upstream type
    compatible_sources=["UpstreamStep"],  # Include the upstream step type
    # Other fields...
)
```

### Analyzing Downstream Steps

Similarly, analyze downstream steps to ensure your outputs match their needs:

```python
# Load the downstream step's specification
from src.pipeline_step_specs.downstream_step_spec import DOWNSTREAM_STEP_SPEC

# Examine its dependencies
for dep_name, dep_spec in DOWNSTREAM_STEP_SPEC.dependencies.items():
    print(f"Dependency: {dep_name}")
    print(f"  Logical Name: {dep_spec.logical_name}")
    print(f"  Required: {dep_spec.required}")
    print(f"  Compatible Sources: {dep_spec.compatible_sources}")
```

## OutputSpec Creation Guidelines

When creating output specifications, follow these guidelines:

1. **Match Script Output**: Each output specification should correspond to an output generated by your script
2. **Use Consistent Logical Names**: The logical name should match the key in the script contract's `expected_output_paths`
3. **Define Correct Property Path**: Use the standard format for property paths:
   - For processing outputs: `properties.ProcessingOutputConfig.Outputs['logical_name'].S3Output.S3Uri`
   - For model artifacts: `properties.ModelArtifacts.S3ModelArtifacts`
4. **Include Aliases If Needed**: Add aliases for backward compatibility or semantic matching
5. **Document Data Format**: Clearly describe the output format in the description

### Property Path Guidelines

Property paths follow a standardized format based on output type:

| Output Type | Property Path Format | Example |
|-------------|---------------------|---------|
| ProcessingOutput | `properties.ProcessingOutputConfig.Outputs['logical_name'].S3Output.S3Uri` | `properties.ProcessingOutputConfig.Outputs['processed_data'].S3Output.S3Uri` |
| ModelArtifacts | `properties.ModelArtifacts.S3ModelArtifacts` | `properties.ModelArtifacts.S3ModelArtifacts` |
| TransformOutput | `properties.TransformOutput.S3OutputPath` | `properties.TransformOutput.S3OutputPath` |

## DependencySpec Creation Guidelines

When creating dependency specifications:

1. **Match Script Input**: Each dependency specification should correspond to an input needed by your script
2. **Use Descriptive Logical Name**: The logical name should match the key in the script contract's `expected_input_paths`
3. **Specify Required Status**: Clearly indicate whether the dependency is required or optional
4. **List All Compatible Sources**: Include all step types that can produce this dependency
5. **Add Rich Semantic Keywords**: Include keywords that help with semantic matching

## Specification Validation

### Contract Alignment Validation

Always validate alignment between specification and contract:

```python
result = YOUR_STEP_SPEC.validate_contract_alignment()
if not result.is_valid:
    print(f"Contract alignment issues: {result.errors}")
else:
    print("Contract alignment validated successfully!")
```

### Property Path Consistency

Validate property path consistency in your outputs:

```python
for output in YOUR_STEP_SPEC.outputs.values():
    expected = f"properties.ProcessingOutputConfig.Outputs['{output.logical_name}'].S3Output.S3Uri"
    if output.property_path != expected:
        print(f"Property path inconsistency in {output.logical_name}")
```

### Cross-Step Validation

Validate compatibility with connected steps:

```python
# Validate upstream compatibility
from src.pipeline_deps.validation import validate_step_compatibility
result = validate_step_compatibility(UPSTREAM_STEP_SPEC, YOUR_STEP_SPEC)
if not result.is_valid:
    print(f"Upstream compatibility issues: {result.errors}")
```

## Specification Examples

### Source Node Example

```python
DATA_LOADING_SPEC = StepSpecification(
    step_type=get_spec_step_type("DataLoading"),
    node_type=NodeType.SOURCE,  # Source node has no dependencies
    script_contract=_get_data_loading_contract(),
    dependencies={},  # No dependencies for source nodes
    outputs={
        "data": OutputSpec(
            logical_name="data",
            output_type=DependencyType.PROCESSING_OUTPUT,
            property_path="properties.ProcessingOutputConfig.Outputs['data'].S3Output.S3Uri",
            aliases=["raw_data", "input_data"],
            data_type="S3Uri",
            description="Raw data loaded from source"
        )
    }
)
```

### Internal Node Example

```python
PREPROCESSING_SPEC = StepSpecification(
    step_type=get_spec_step_type("TabularPreprocessing"),
    node_type=NodeType.INTERNAL,
    script_contract=_get_preprocessing_contract(),
    dependencies={
        "raw_data": DependencySpec(
            logical_name="raw_data",
            dependency_type=DependencyType.PROCESSING_OUTPUT,
            required=True,
            compatible_sources=["DataLoading"],
            semantic_keywords=["raw", "data", "input"],
            data_type="S3Uri",
            description="Raw input data for preprocessing"
        )
    },
    outputs={
        "processed_data": OutputSpec(
            logical_name="processed_data",
            output_type=DependencyType.PROCESSING_OUTPUT,
            property_path="properties.ProcessingOutputConfig.Outputs['processed_data'].S3Output.S3Uri",
            aliases=["features", "preprocessed"],
            data_type="S3Uri",
            description="Processed tabular data ready for training"
        ),
        "metadata": OutputSpec(
            logical_name="metadata",
            output_type=DependencyType.PROCESSING_OUTPUT,
            property_path="properties.ProcessingOutputConfig.Outputs['metadata'].S3Output.S3Uri",
            data_type="S3Uri",
            description="Preprocessing metadata and statistics"
        )
    }
)
```

### Sink Node Example

```python
REGISTRATION_SPEC = StepSpecification(
    step_type=get_spec_step_type("ModelRegistration"),
    node_type=NodeType.SINK,  # Sink node has no outputs
    script_contract=_get_registration_contract(),
    dependencies={
        "model": DependencySpec(
            logical_name="model",
            dependency_type=DependencyType.MODEL_ARTIFACTS,
            required=True,
            compatible_sources=["XGBoostTraining", "PyTorchTraining"],
            semantic_keywords=["model", "artifact", "trained"],
            data_type="S3Uri",
            description="Trained model artifacts for registration"
        ),
        "metrics": DependencySpec(
            logical_name="metrics",
            dependency_type=DependencyType.PROCESSING_OUTPUT,
            required=True,
            compatible_sources=["ModelEvaluation"],
            semantic_keywords=["metrics", "evaluation", "performance"],
            data_type="S3Uri",
            description="Model evaluation metrics"
        )
    },
    outputs={}  # No outputs for sink nodes
)
```

## Best Practices

1. **Use Descriptive Names**: Choose clear, descriptive logical names
2. **Be Explicit About Requirements**: Clearly mark dependencies as required or optional
3. **Provide Rich Semantic Metadata**: Include comprehensive descriptions and keywords
4. **Validate Contract Alignment**: Always validate specification against contract
5. **Use Standard Property Paths**: Follow the established patterns for property paths
6. **Consider Job Type Variants**: Implement variants if your step needs different behavior for different job types
7. **Test Compatibility**: Verify compatibility with upstream and downstream steps

By following these guidelines, your step specifications will enable robust dependency resolution and seamless integration with the pipeline architecture.



-----------
##  Recommended Notes

- [[Step Specification Design as Declarative Pipeline Architecture]]
- [[Base Step Specification]]