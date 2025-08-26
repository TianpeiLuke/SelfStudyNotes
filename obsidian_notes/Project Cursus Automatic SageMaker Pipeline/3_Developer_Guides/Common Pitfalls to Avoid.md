---
tags:
  - project
  - design/validation
  - aws/sagemaker_pipeline
aliases: 
date of note: 2025-07-16
---
When implementing new pipeline steps, there are several common mistakes that developers often make. This document outlines these pitfalls and provides guidance on how to avoid them.

## Script Implementation Pitfalls

### 1. Hardcoded Paths

**Problem**: Hardcoding container paths in your script makes it inflexible and breaks the contract alignment.

```python
# WRONG ❌
input_path = "/opt/ml/processing/input/data"  # Hardcoded path
output_path = "/opt/ml/processing/output/results"  # Hardcoded path
```

**Solution**: Use the script contract to get paths. See [Script Contract Development](Script%20Contract%20Development.md) for details and [Path Handling Best Practices](Best%20Practices.md#path-handling) for examples.

```python
# CORRECT ✅
contract = get_script_contract()
input_path = contract.expected_input_paths["input_data"]
output_path = contract.expected_output_paths["output_data"]
```

### 2. Missing Environment Variable Error Handling

**Problem**: Not handling missing environment variables can cause cryptic runtime errors.

```python
# WRONG ❌
learning_rate = float(os.environ["LEARNING_RATE"])  # Will fail if not set
```

**Solution**: Validate environment variables or provide defaults. For best practices on environment variable handling, see [Environment Variable Documentation](Best%20Practices.md#environment-variable-documentation).

```python
# CORRECT ✅
try:
    learning_rate = float(os.environ["LEARNING_RATE"])
except (KeyError, ValueError) as e:
    raise ValueError(f"Required environment variable LEARNING_RATE is missing or invalid: {str(e)}")

# Alternative with default
learning_rate = float(os.environ.get("LEARNING_RATE", "0.01"))
```

### 3. Directory vs. File Path Confusion

**Problem**: Treating a directory path as a file or vice versa leads to errors.

```python
# WRONG ❌
# If output_path is a directory, this will fail
with open(output_path, 'w') as f:  # Trying to open a directory as a file
    json.dump(data, f)
```

**Solution**: Be explicit about directory vs. file paths. See [Path Handling Best Practices](Best%20Practices.md#path-handling) for recommended patterns.

```python
# CORRECT ✅
output_dir = contract.expected_output_paths["output_data"]
output_file = os.path.join(output_dir, "results.json")
os.makedirs(os.path.dirname(output_file), exist_ok=True)
with open(output_file, 'w') as f:
    json.dump(data, f)
```

### 4. Insufficient Error Handling

**Problem**: Minimal error handling makes debugging difficult.

```python
# WRONG ❌
def process_data():
    data = pd.read_csv(input_path)
    result = data.groupby('category').sum()
    result.to_csv(output_path)
```

**Solution**: Add comprehensive error handling and logging. See [Error Handling Best Practices](Best%20Practices.md#error-handling) for detailed examples and patterns.

```python
# CORRECT ✅
def process_data():
    try:
        logger.info(f"Reading data from {input_path}")
        data = pd.read_csv(input_path)
        
        if data.empty:
            raise ValueError("Input data is empty")
        
        logger.info(f"Processing data with {len(data)} records")
        result = data.groupby('category').sum()
        
        logger.info(f"Writing results to {output_path}")
        result.to_csv(output_path)
        
    except pd.errors.EmptyDataError:
        logger.error(f"Empty CSV file: {input_path}")
        raise
    except pd.errors.ParserError as e:
        logger.error(f"Error parsing CSV: {str(e)}")
        raise
    except Exception as e:
        logger.error(f"Unexpected error: {str(e)}")
        raise
```

### 5. Not Creating Output Directories

**Problem**: Failing to create output directories before writing files.

```python
# WRONG ❌
with open(os.path.join(output_path, "output.csv"), 'w') as f:  # May fail if directory doesn't exist
    csv_writer = csv.writer(f)
    csv_writer.writerows(data)
```

**Solution**: Always create directories before writing files. See [Path Handling Best Practices](Best%20Practices.md#path-handling) for more examples.

```python
# CORRECT ✅
output_file = os.path.join(output_path, "output.csv")
os.makedirs(os.path.dirname(output_file), exist_ok=True)
with open(output_file, 'w') as f:
    csv_writer = csv.writer(f)
    csv_writer.writerows(data)
```

## Contract Development Pitfalls

### 1. Inconsistent Logical Names

**Problem**: Using different logical names in contract vs. specification leads to misalignment.

```python
# WRONG ❌
# In script contract
expected_input_paths={
    "data": "/opt/ml/processing/input/data"  # Logical name: "data"
}

# In step specification
dependencies={
    "input_data": DependencySpec(...)  # Different logical name: "input_data"
}
```

**Solution**: Use consistent logical names across contract and specification. See [Alignment Rules](Alignment%20Rules.md) for detailed guidance and [Logical Name Clarity](Best%20Practices.md#logical-name-clarity) for best practices.

```python
# CORRECT ✅
# In script contract
expected_input_paths={
    "input_data": "/opt/ml/processing/input/data"  # Logical name: "input_data"
}

# In step specification
dependencies={
    "input_data": DependencySpec(...)  # Same logical name: "input_data"
}
```

### 2. Missing Required Environment Variables

**Problem**: Not declaring all required environment variables in the contract.

```python
# WRONG ❌
# Script uses LEARNING_RATE but contract doesn't declare it
YOUR_SCRIPT_CONTRACT = ScriptContract(
    entry_point="your_script.py",
    expected_input_paths={...},
    expected_output_paths={...},
    required_env_vars=[
        # Missing LEARNING_RATE
    ],
    # ...
)
```

**Solution**: Declare all environment variables used by the script.

```python
# CORRECT ✅
YOUR_SCRIPT_CONTRACT = ScriptContract(
    entry_point="your_script.py",
    expected_input_paths={...},
    expected_output_paths={...},
    required_env_vars=[
        "LEARNING_RATE",
        "NUM_EPOCHS",
        # All required env vars
    ],
    optional_env_vars={
        "DEBUG_MODE": "False"
        # Optional env vars with defaults
    }
    # ...
)
```

### 3. Wrong Container Path Conventions

**Problem**: Using non-standard paths or incorrect path formats.

```python
# WRONG ❌
expected_input_paths={
    "data": "/data/input",  # Non-standard path
    "config": "/etc/config"  # Non-standard path
}
```

**Solution**: Follow SageMaker path conventions.

```python
# CORRECT ✅
expected_input_paths={
    "data": "/opt/ml/processing/input/data",  # Standard processing input path
    "config": "/opt/ml/processing/input/config"  # Standard processing input path
}

# For training scripts
expected_input_paths={
    "training": "/opt/ml/input/data/training",  # Standard training input path
    "validation": "/opt/ml/input/data/validation"  # Standard training input path
}
```

### 4. Overlapping Input/Output Paths

**Problem**: Using the same path for both input and output can cause conflicts.

```python
# WRONG ❌
expected_input_paths={
    "data": "/opt/ml/processing/data"  # Same base path as output
}

expected_output_paths={
    "results": "/opt/ml/processing/data/results"  # Subpath of input path
}
```

**Solution**: Use separate paths for inputs and outputs.

```python
# CORRECT ✅
expected_input_paths={
    "data": "/opt/ml/processing/input/data"  # Standard input path
}

expected_output_paths={
    "results": "/opt/ml/processing/output/results"  # Standard output path
}
```

### 5. File vs. Directory Path Confusion in Contracts

**Problem**: SageMaker creates directories at paths specified in `ProcessingOutput`, which can cause issues when scripts expect to create files.

```python
# WRONG ❌
expected_output_paths={
    "model": "/opt/ml/processing/output/model.tar.gz"  # File path, but SageMaker will create this as a directory
}
```

**Solution**: Use the parent directory for file outputs.

```python
# CORRECT ✅
expected_output_paths={
    "model": "/opt/ml/processing/output/model"  # Directory path
}

# Then in script:
model_dir = contract.expected_output_paths["model"]
model_file = os.path.join(model_dir, "model.tar.gz")
```

## Specification Development Pitfalls

### 1. Incomplete Compatible Sources

**Problem**: Not including all possible upstream steps that could provide a dependency.

```python
# WRONG ❌
"input_data": DependencySpec(
    # ...
    compatible_sources=["TabularPreprocessing"]  # Only one source listed
    # ...
)
```

**Solution**: List all compatible source steps.

```python
# CORRECT ✅
"input_data": DependencySpec(
    # ...
    compatible_sources=[
        "TabularPreprocessing", 
        "FeatureEngineering", 
        "DataLoading"
    ]  # All possible sources
    # ...
)
```

### 2. Incorrect Property Paths

**Problem**: Using incorrect property path formats for outputs.

```python
# WRONG ❌
"model_output": OutputSpec(
    logical_name="model_output",
    property_path="ModelArtifacts.S3Uri"  # Wrong format
    # ...
)
```

**Solution**: Use standard property path formats based on step type.

```python
# CORRECT ✅
# For Processing Steps - use the logical name in the path
"processed_data": OutputSpec(
    logical_name="processed_data",
    property_path="properties.ProcessingOutputConfig.Outputs['processed_data'].S3Output.S3Uri"  # Note: 'processed_data' matches logical_name
    # ...
)

# For Training Steps - model artifacts
"model_output": OutputSpec(
    logical_name="model_output",
    property_path="properties.ModelArtifacts.S3ModelArtifacts"  # Correct format for model artifacts
    # ...
)

# Key Rule: For Processing Steps, the property path must include the logical name:
# properties.ProcessingOutputConfig.Outputs['<logical_name>'].S3Output.S3Uri
```

### 3. Mismatch Between NodeType and Dependencies/Outputs

**Problem**: Using inconsistent NodeType, dependencies, and outputs.

```python
# WRONG ❌
YOUR_STEP_SPEC = StepSpecification(
    step_type=get_spec_step_type("YourStep"),
    node_type=NodeType.SOURCE,  # Source node type
    dependencies={  # But has dependencies
        "input_data": DependencySpec(...)
    },
    outputs={
        "output_data": OutputSpec(...)
    }
)
```

**Solution**: Ensure NodeType matches dependencies and outputs.

```python
# CORRECT ✅
# For source nodes (no dependencies)
SOURCE_STEP_SPEC = StepSpecification(
    step_type=get_spec_step_type("SourceStep"),
    node_type=NodeType.SOURCE,
    dependencies={},  # No dependencies
    outputs={
        "output_data": OutputSpec(...)
    }
)

# For internal nodes (dependencies and outputs)
INTERNAL_STEP_SPEC = StepSpecification(
    step_type=get_spec_step_type("InternalStep"),
    node_type=NodeType.INTERNAL,
    dependencies={
        "input_data": DependencySpec(...)
    },
    outputs={
        "output_data": OutputSpec(...)
    }
)

# For sink nodes (dependencies but no outputs)
SINK_STEP_SPEC = StepSpecification(
    step_type=get_spec_step_type("SinkStep"),
    node_type=NodeType.SINK,
    dependencies={
        "input_data": DependencySpec(...)
    },
    outputs={}  # No outputs
)
```

### 4. Missing Semantic Keywords

**Problem**: Not providing enough semantic keywords for dependency matching.

```python
# WRONG ❌
"input_data": DependencySpec(
    # ...
    semantic_keywords=["data"]  # Too vague
    # ...
)
```

**Solution**: Provide rich semantic keywords.

```python
# CORRECT ✅
"input_data": DependencySpec(
    # ...
    semantic_keywords=[
        "data", 
        "tabular", 
        "processed", 
        "features", 
        "training"
    ]  # Rich semantic context
    # ...
)
```

### 5. Missing Dependency Description

**Problem**: Not providing a clear description for dependencies.

```python
# WRONG ❌
"input_data": DependencySpec(
    # ...
    description=""  # Missing or empty description
    # ...
)
```

**Solution**: Add a clear, comprehensive description.

```python
# CORRECT ✅
"input_data": DependencySpec(
    # ...
    description="Processed tabular data for training, with features and label columns prepared for model training"  # Clear description
    # ...
)
```

## Builder Implementation Pitfalls

### 1. Hardcoded Container Paths

**Problem**: Hardcoding container paths instead of using the script contract.

```python
# WRONG ❌
def _get_inputs(self, inputs):
    return [
        ProcessingInput(
            input_name="data",
            source=inputs["data"],
            destination="/opt/ml/processing/input/data"  # Hardcoded path
        )
    ]
```

**Solution**: Get paths from the script contract.

```python
# CORRECT ✅
def _get_inputs(self, inputs):
    contract = self.spec.script_contract
    return [
        ProcessingInput(
            input_name="data",
            source=inputs["data"],
            destination=contract.expected_input_paths["data"]  # Path from contract
        )
    ]
```

### 2. Missing Environment Variables

**Problem**: Not setting all required environment variables.

```python
# WRONG ❌
def _get_processor_env_vars(self):
    return {
        # Missing required variables
    }
```

**Solution**: Set all required environment variables based on the contract.

```python
# CORRECT ✅
def _get_processor_env_vars(self):
    env_vars = {}
    
    # Add all required variables from contract
    for var_name in self.spec.script_contract.required_env_vars:
        if var_name == "LEARNING_RATE":
            env_vars[var_name] = str(self.config.learning_rate)
        elif var_name == "NUM_EPOCHS":
            env_vars[var_name] = str(self.config.num_epochs)
        # ... other required variables
    
    # Add optional variables
    for var_name, default in self.spec.script_contract.optional_env_vars.items():
        config_value = getattr(self.config, var_name.lower(), None)
        env_vars[var_name] = str(config_value) if config_value is not None else default
    
    return env_vars
```

### 3. Not Using the Specification-Driven Approach

**Problem**: Manually defining inputs/outputs instead of using the specification-driven approach.

```python
# WRONG ❌
def _get_inputs(self, inputs):
    # Manual definition, not using specification
    return [
        ProcessingInput(
            input_name="data",
            source=inputs.get("data", ""),
            destination="/opt/ml/processing/input/data"
        )
    ]
```

**Solution**: Use specification-driven methods. See [Step Builder Implementation](Step%20Builder%20Implementation.md) for details and follow [Standardization Rules](Standardization%20Rules.md) for consistency.

```python
# CORRECT ✅
def _get_inputs(self, inputs):
    # Use specification-driven method
    return self._get_spec_driven_processor_inputs(inputs)
```

### 4. Missing Type Conversion for Environment Variables

**Problem**: Not converting non-string values to strings for environment variables.

```python
# WRONG ❌
def _get_processor_env_vars(self):
    return {
        "LEARNING_RATE": self.config.learning_rate,  # Not converted to string
        "NUM_EPOCHS": self.config.num_epochs  # Not converted to string
    }
```

**Solution**: Convert all values to strings. See [Environment Variable Setting](Best%20Practices.md#environment-variable-setting) for best practices.

```python
# CORRECT ✅
def _get_processor_env_vars(self):
    return {
        "LEARNING_RATE": str(self.config.learning_rate),  # Converted to string
        "NUM_EPOCHS": str(self.config.num_epochs)  # Converted to string
    }
```

### 5. Not Handling Job Type Variants

**Problem**: Not selecting the appropriate specification for different job types.

```python
# WRONG ❌
def __init__(self, config, **kwargs):
    # Always using the same specification regardless of job type
    super().__init__(config=config, spec=YOUR_STEP_SPEC, **kwargs)
```

**Solution**: Select specification based on job type.

```python
# CORRECT ✅
def __init__(self, config, **kwargs):
    # Get job type if available
    job_type = getattr(config, 'job_type', None)
    
    # Select appropriate specification based on job type
    if job_type and job_type.lower() == "calibration":
        spec = YOUR_STEP_CALIBRATION_SPEC
    elif job_type and job_type.lower() == "validation":
        spec = YOUR_STEP_VALIDATION_SPEC
    else:
        spec = YOUR_STEP_TRAINING_SPEC  # Default to training
    
    super().__init__(config=config, spec=spec, **kwargs)
```

## Integration Pitfalls

### 1. Incomplete Step Registration

**Problem**: Not registering the step in all required places.

```python
# WRONG ❌
# Only added to step_names.py but not imported in __init__.py
```

**Solution**: Register the step in all required places.

```python
# CORRECT ✅
# In step_names.py
STEP_NAMES = {
    # ...
    "YourNewStep": {
        "config_class": "YourNewStepConfig",
        "builder_step_name": "YourNewStepBuilder",
        "spec_type": "YourNewStep"
    }
}

# In pipeline_steps/__init__.py
from .builder_your_new_step import YourNewStepBuilder

# In pipeline_step_specs/__init__.py
from .your_new_step_spec import YOUR_NEW_STEP_SPEC
```

### 2. Missing DAG Connections

**Problem**: Adding a node but forgetting to connect it with edges.

```python
# WRONG ❌
def _create_pipeline_dag(self):
    dag = PipelineDAG()
    dag.add_node("data_loading")
    dag.add_node("preprocessing")
    dag.add_node("your_new_step")  # Added node
    dag.add_node("training")
    
    # Missing connections for your_new_step
    dag.add_edge("data_loading", "preprocessing")
    dag.add_edge("preprocessing", "training")  # Direct connection bypassing your step
    
    return dag
```

**Solution**: Ensure proper connections in the DAG.

```python
# CORRECT ✅
def _create_pipeline_dag(self):
    dag = PipelineDAG()
    dag.add_node("data_loading")
    dag.add_node("preprocessing")
    dag.add_node("your_new_step")  # Added node
    dag.add_node("training")
    
    dag.add_edge("data_loading", "preprocessing")
    dag.add_edge("preprocessing", "your_new_step")  # Connect to your step
    dag.add_edge("your_new_step", "training")  # Connect from your step
    
    return dag
```

### 3. Forgetting to Add Configuration to Config Map

**Problem**: Adding a step to the DAG but forgetting to add its configuration to the config map.

```python
# WRONG ❌
def _create_config_map(self):
    config_map = {}
    config_map["data_loading"] = self._get_data_loading_config()
    config_map["preprocessing"] = self._get_preprocessing_config()
    # Missing your_new_step config
    config_map["training"] = self._get_training_config()
    return config_map
```

**Solution**: Add the step's configuration to the config map.

```python
# CORRECT ✅
def _create_config_map(self):
    config_map = {}
    config_map["data_loading"] = self._get_data_loading_config()
    config_map["preprocessing"] = self._get_preprocessing_config()
    config_map["your_new_step"] = self._get_your_new_step_config()  # Add your step's config
    config_map["training"] = self._get_training_config()
    return config_map
```

### 4. Not Adding Builder to Builder Map

**Problem**: Forgetting to add the step builder to the builder map.

```python
# WRONG ❌
def _create_step_builder_map(self):
    return {
        "data_loading": DataLoadingStepBuilder,
        "preprocessing": PreprocessingStepBuilder,
        # Missing your_new_step builder
        "training": TrainingStepBuilder
    }
```

**Solution**: Add the step builder to the builder map.

```python
# CORRECT ✅
def _create_step_builder_map(self):
    return {
        "data_loading": DataLoadingStepBuilder,
        "preprocessing": PreprocessingStepBuilder,
        "your_new_step": YourNewStepBuilder,  # Add your step's builder
        "training": TrainingStepBuilder
    }
```

### 5. Incompatible Dependencies

**Problem**: Connecting steps with incompatible dependencies.

```python
# WRONG ❌
# Step A output
"output_data": OutputSpec(
    logical_name="output_data",
    output_type=DependencyType.PROCESSING_OUTPUT
    # ...
)

# Step B dependency (incompatible type)
"input_model": DependencySpec(
    logical_name="input_model",
    dependency_type=DependencyType.MODEL_ARTIFACTS  # Different type than Step A output
    # ...
)

# Connecting A to B in DAG
dag.add_edge("step_a", "step_b")  # Incompatible connection
```

**Solution**: Ensure dependency compatibility or add intermediate steps.

```python
# CORRECT ✅
# Add intermediate step to convert between types, or
# Ensure output and dependency types match, or
# Modify specifications to be compatible
```

## Testing Pitfalls

### 1. Missing Contract Alignment Tests

**Problem**: Not testing if the specification aligns with the contract.

```python
# WRONG ❌
# No tests for contract alignment
```

**Solution**: Add contract alignment tests. See [Unit Testing Strategy](Best%20Practices.md#unit-testing-strategy) for recommended test patterns and [Standardization Rules](Standardization%20Rules.md#testing-standards) for testing standards.

```python
# CORRECT ✅
def test_contract_alignment(self):
    """Test that specification aligns with contract."""
    result = YOUR_STEP_SPEC.validate_contract_alignment()
    self.assertTrue(result.is_valid, f"Contract alignment failed: {result.errors}")
```

### 2. Missing Property Path Tests

**Problem**: Not testing property path consistency.

```python
# WRONG ❌
# No tests for property path consistency
```

**Solution**: Add property path consistency tests.

```python
# CORRECT ✅
def test_property_path_consistency(self):
    """Test property path consistency in outputs."""
    for output_name, output_spec in YOUR_STEP_SPEC.outputs.items():
        expected = f"properties.ProcessingOutputConfig.Outputs['{output_spec.logical_name}'].S3Output.S3Uri"
        self.assertEqual(output_spec.property_path, expected,
                       f"Property path inconsistency in {output_name}")
```

### 3. Not Testing Environment Variable Generation

**Problem**: Not testing if all required environment variables are correctly set.

```python
# WRONG ❌
# No tests for environment variable generation
```

**Solution**: Add environment variable generation tests.

```python
# CORRECT ✅
def test_environment_variable_generation(self):
    """Test that all required environment variables are set."""
    config = YourStepConfig(
        region="us-west-2",
        pipeline_s3_loc="s3://bucket/prefix",
        param1="value1",
        param2=42
    )
    builder = YourStepBuilder(config)
    
    env_vars = builder._get_processor_env_vars()
    
    # Check that all required variables are present
    for var_name in builder.spec.script_contract.required_env_vars:
        self.assertIn(var_name, env_vars, f"Missing required env var: {var_name}")
        
    # Check specific values
    self.assertEqual(env_vars["REQUIRED_PARAM_1"], "value1")
    self.assertEqual(env_vars["REQUIRED_PARAM_2"], "42")  # Note: converted to string
```

### 4. Not Testing with Job Type Variants

**Problem**: Only testing with default job type.

```python
# WRONG ❌
# Only testing with default job type
def test_step_creation(self):
    config = YourStepConfig(
        region="us-west-2",
        pipeline_s3_loc="s3://bucket/prefix"
    )  # No job_type specified
    builder = YourStepBuilder(config)
    step = builder.create_step()
    # ...
```

**Solution**: Test with all supported job types.

```python
# CORRECT ✅
def test_step_creation_with_training_job_type(self):
    config = YourStepConfig(
        region="us-west-2",
        pipeline_s3_loc="s3://bucket/prefix",
        job_type="training"
    )
    builder = YourStepBuilder(config)
    step = builder.create_step()
    # Test assertions...

def test_step_creation_with_calibration_job_type(self):
    config = YourStepConfig(
        region="us-west-2",
        pipeline_s3_loc="s3://bucket/prefix",
        job_type="calibration"
    )
    builder = YourStepBuilder(config)
    step = builder.create_step()
    # Test assertions...
```

### 5. Not Testing Edge Cases

**Problem**: Only testing the happy path, not edge cases.

```python
# WRONG ❌
# Only testing with valid inputs
```

**Solution**: Test edge cases and error conditions.

```python
# CORRECT ✅
def test_missing_required_dependency(self):
    """Test behavior when a required dependency is missing."""
    # Setup with missing dependency
    inputs = {}  # Missing required dependency
    
    # Act/Assert
    with self.assertRaises(ValueError):
        builder._get_inputs(inputs)
        
def test_empty_dependency_handling(self):
    """Test that empty dependencies are handled gracefully."""
    # Act
    extracted_inputs = builder.extract_inputs_from_dependencies([])
    
    # Assert
    self.assertEqual(extracted_inputs, {})
```

## Conclusion

By being aware of these common pitfalls, you can avoid many of the issues that often arise when implementing new pipeline steps. Remember to:

1. **Follow the Conventions**: Adhere to established path conventions and naming standards
2. **Ensure Alignment**: Maintain alignment between script, contract, and specification
3. **Handle Edge Cases**: Consider and test for edge cases and error conditions
4. **Complete Registration**: Register your step in all required places
5. **Provide Rich Documentation**: Document your step comprehensively
6. **Follow Standardization Rules**: Apply [standardization rules](Standardization%20Rules.md) for consistent implementation

When in doubt, refer to the [validation checklist](Validation%20Checklist.md) to verify your implementation, follow the [standardization rules](Standardization%20Rules.md) for universal patterns, and consult the [best practices](Best%20Practices.md) for guidance on recommended approaches.



-----------
##  Recommended Notes

- [[Pain Points Summary for Template Pipeline Design]]