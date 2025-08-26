---
tags:
  - project
  - design/design_architecture
  - design/design_philosophy
  - aws/sagemaker_pipeline
aliases: 
date of note: 2025-07-16
---
This document outlines recommended best practices for developing and integrating pipeline steps. Following these practices will help ensure your steps are robust, maintainable, and consistent with the overall architecture.

## Script Development

### Script Organization

1. **Modular Design**: Organize your script into well-defined functions with clear responsibilities
2. **Entry Point Pattern**: Use a clear entry point function (e.g., `main()`)
3. **Error Handling**: Implement comprehensive error handling and logging
4. **Contract Integration**: Integrate with the script contract for path resolution
5. **Parameterization**: Use environment variables for all configurable parameters

Example of well-organized script structure:

```python
import os
import logging
import pandas as pd
from typing import Dict, List, Any

# Configure logging
logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)

def get_script_contract():
    """Get the contract for this script."""
    from ..pipeline_script_contracts.your_script_contract import YOUR_SCRIPT_CONTRACT
    return YOUR_SCRIPT_CONTRACT

def read_input_data(input_path: str) -> pd.DataFrame:
    """Read input data from the specified path."""
    try:
        logger.info(f"Reading input data from {input_path}")
        return pd.read_csv(input_path)
    except Exception as e:
        logger.error(f"Error reading input data: {e}")
        raise

def process_data(df: pd.DataFrame, params: Dict[str, Any]) -> pd.DataFrame:
    """Process data according to the specified parameters."""
    try:
        logger.info(f"Processing data with parameters: {params}")
        # Processing logic here
        return df
    except Exception as e:
        logger.error(f"Error processing data: {e}")
        raise

def write_output_data(df: pd.DataFrame, output_path: str) -> None:
    """Write the processed data to the output path."""
    try:
        logger.info(f"Writing output data to {output_path}")
        os.makedirs(os.path.dirname(output_path), exist_ok=True)
        df.to_csv(output_path, index=False)
        logger.info("Output data written successfully")
    except Exception as e:
        logger.error(f"Error writing output data: {e}")
        raise

def main():
    """Main entry point for the script."""
    try:
        # Get and validate contract
        contract = get_script_contract()
        
        # Get paths from contract
        input_path = os.path.join(contract.expected_input_paths["input_data"], "input.csv")
        output_path = os.path.join(contract.expected_output_paths["output_data"], "output.csv")
        
        # Get parameters from environment variables
        params = {
            "param1": os.environ["PARAM_1"],
            "param2": int(os.environ["PARAM_2"]),
            "param3": os.environ.get("PARAM_3", "default_value")
        }
        
        # Execute processing pipeline
        df = read_input_data(input_path)
        processed_df = process_data(df, params)
        write_output_data(processed_df, output_path)
        
        logger.info("Processing completed successfully")
        
    except Exception as e:
        logger.error(f"Processing failed: {e}")
        raise

if __name__ == "__main__":
    main()
```

### Error Handling

1. **Log Before Actions**: Log intent before performing actions
2. **Structured Exceptions**: Use structured exceptions with informative messages
3. **Log Exceptions**: Log exceptions before re-raising
4. **Fail Fast**: Fail fast with clear error messages
5. **Validate Inputs**: Validate inputs before processing

Example of good error handling:

```python
def process_feature(df, feature_name):
    """Process a specific feature in the dataframe."""
    try:
        logger.info(f"Processing feature: {feature_name}")
        
        # Validate inputs
        if feature_name not in df.columns:
            raise ValueError(f"Feature '{feature_name}' not found in dataframe columns: {df.columns}")
        
        # Check for missing values
        missing_count = df[feature_name].isnull().sum()
        if missing_count > 0:
            logger.warning(f"Feature '{feature_name}' has {missing_count} missing values")
        
        # Process feature
        # ...processing logic...
        
        logger.info(f"Successfully processed feature: {feature_name}")
        return processed_feature
        
    except Exception as e:
        logger.error(f"Error processing feature '{feature_name}': {str(e)}")
        raise
```

### Path Handling

1. **Use Contract Paths**: Always use paths from the script contract
2. **Directory vs. File**: Be clear about whether a path refers to a directory or file
3. **Create Directories**: Create output directories before writing files
4. **Path Joining**: Use `os.path.join()` for path construction
5. **Validate Existence**: Validate input paths before reading

Example of good path handling:

```python
def write_output(df, contract):
    """Write output data according to the contract."""
    # Get output directory from contract
    output_dir = contract.expected_output_paths["output_data"]
    
    # Create output directory if it doesn't exist
    os.makedirs(output_dir, exist_ok=True)
    
    # Construct file path within the directory
    output_file = os.path.join(output_dir, "output.csv")
    
    # Write the file
    logger.info(f"Writing output to {output_file}")
    df.to_csv(output_file, index=False)
```

## Contract Development

### Logical Name Clarity

1. **Descriptive Names**: Use descriptive logical names for inputs and outputs
2. **Consistent Names**: Use consistent naming conventions
3. **Matching Paths**: Ensure logical names match the paths used in the script
4. **Name Alignment**: Align names with step specifications
5. **Avoid Abbreviations**: Use full words rather than abbreviations

Examples of good logical names:

```python
# Clear, descriptive logical names
expected_input_paths={
    "training_data": "/opt/ml/processing/input/training",
    "validation_data": "/opt/ml/processing/input/validation",
    "hyperparameters": "/opt/ml/processing/input/hyperparameters"
}

# Clear, descriptive output names
expected_output_paths={
    "trained_model": "/opt/ml/processing/output/model",
    "evaluation_metrics": "/opt/ml/processing/output/metrics",
    "prediction_results": "/opt/ml/processing/output/predictions"
}
```

### Environment Variable Documentation

1. **Document All Variables**: Document all environment variables in the contract
2. **Required vs. Optional**: Clearly distinguish between required and optional variables
3. **Default Values**: Provide sensible default values for optional variables
4. **Type Hints**: Include type hints in documentation
5. **Valid Values**: Document valid values or ranges for variables

Example of good environment variable documentation:

```python
required_env_vars=[
    # MODEL_TYPE: Type of model to train (options: "classification", "regression")
    "MODEL_TYPE",
    
    # NUM_EPOCHS: Number of training epochs (integer > 0)
    "NUM_EPOCHS",
    
    # LEARNING_RATE: Learning rate for optimizer (float, typically 1e-5 to 1e-1)
    "LEARNING_RATE"
],
optional_env_vars={
    # DEBUG_MODE: Enable debug logging (boolean, "True" or "False")
    "DEBUG_MODE": "False",
    
    # RANDOM_SEED: Random seed for reproducibility (integer)
    "RANDOM_SEED": "42",
    
    # BATCH_SIZE: Training batch size (integer > 0)
    "BATCH_SIZE": "32"
}
```

## Specification Development

### Dependency Clarity

1. **Required vs. Optional**: Clearly mark dependencies as required or optional
2. **Comprehensive Compatibility**: List all compatible source steps
3. **Rich Semantics**: Provide rich semantic keywords
4. **Data Type Documentation**: Document expected data types
5. **Descriptive Documentation**: Write clear descriptions

Example of a well-specified dependency:

```python
"training_data": DependencySpec(
    logical_name="training_data",
    dependency_type=DependencyType.PROCESSING_OUTPUT,
    required=True,  # Explicitly mark as required
    compatible_sources=[
        "DataLoading",
        "TabularPreprocessing",
        "FeatureEngineering"
    ],  # List all compatible sources
    semantic_keywords=[
        "data", "tabular", "training", "features", "processed"
    ],  # Rich semantic keywords
    data_type="S3Uri",  # Clear data type
    description="Processed tabular data for model training, with features and labels"
)
```

### Output Clarity

1. **Standard Property Paths**: Use standard property path formats
2. **Useful Aliases**: Provide aliases for backward compatibility
3. **Clear Descriptions**: Write clear descriptions of output content
4. **Data Format Documentation**: Document output data formats
5. **Consistent Naming**: Use consistent naming patterns

Example of a well-specified output:

```python
"model_artifacts": OutputSpec(
    logical_name="model_artifacts",
    output_type=DependencyType.MODEL_ARTIFACTS,
    property_path="properties.ModelArtifacts.S3ModelArtifacts",  # Standard format
    aliases=["model", "trained_model"],  # Useful aliases
    data_type="S3Uri",  # Clear data type
    description="Trained XGBoost model artifacts in tar.gz format, including model.json and metadata"
)
```

## Builder Development

### Configuration Handling

1. **Type Validation**: Validate configuration parameter types
2. **Required Parameters**: Check for required parameters
3. **Sensible Defaults**: Provide sensible defaults for optional parameters
4. **Parameter Documentation**: Document all parameters
5. **Consistent Parameter Names**: Use consistent parameter naming patterns

Example of good configuration handling:

```python
def __init__(
    self,
    region: str,
    pipeline_s3_loc: str,
    instance_type: str = "ml.m5.xlarge",  # Sensible default
    instance_count: int = 1,  # Sensible default
    volume_size_gb: int = 30,  # Sensible default
    max_runtime_seconds: int = 3600,  # Sensible default
    # Step-specific parameters
    feature_columns: List[str] = None,  # Optional parameter
    label_column: str = None,  # Optional parameter
):
    """Initialize configuration with validation.
    
    Args:
        region: AWS region
        pipeline_s3_loc: S3 location for pipeline artifacts
        instance_type: SageMaker instance type
        instance_count: Number of instances
        volume_size_gb: EBS volume size in GB
        max_runtime_seconds: Maximum runtime in seconds
        feature_columns: List of feature column names (optional)
        label_column: Name of the label column (optional)
    """
    super().__init__(region, pipeline_s3_loc)
    
    # Validate required parameters
    if not region:
        raise ValueError("Region must be provided")
    if not pipeline_s3_loc:
        raise ValueError("Pipeline S3 location must be provided")
    
    # Store parameters
    self.instance_type = instance_type
    self.instance_count = instance_count
    self.volume_size_gb = volume_size_gb
    self.max_runtime_seconds = max_runtime_seconds
    self.feature_columns = feature_columns or []
    self.label_column = label_column
    
    # Validate parameter types
    if not isinstance(self.instance_count, int):
        raise TypeError("instance_count must be an integer")
    if not isinstance(self.volume_size_gb, int):
        raise TypeError("volume_size_gb must be an integer")
    if not isinstance(self.max_runtime_seconds, int):
        raise TypeError("max_runtime_seconds must be an integer")
    if not isinstance(self.feature_columns, list):
        raise TypeError("feature_columns must be a list")
```

### Environment Variable Setting

1. **Contract Alignment**: Set environment variables based on the script contract
2. **Type Conversion**: Convert non-string values to strings
3. **Conditional Setting**: Only set variables that are needed
4. **Default Handling**: Handle defaults for optional variables
5. **Complex Value Serialization**: Serialize complex values (e.g., lists)

Example of good environment variable setting:

```python
def _get_processor_env_vars(self) -> Dict[str, str]:
    """Get environment variables for the processor based on contract."""
    # Get contract
    contract = self.spec.script_contract
    
    # Initialize environment variables
    env_vars = {}
    
    # Set required variables from contract
    if "MODEL_TYPE" in contract.required_env_vars:
        env_vars["MODEL_TYPE"] = self.config.model_type
    
    if "NUM_EPOCHS" in contract.required_env_vars:
        env_vars["NUM_EPOCHS"] = str(self.config.num_epochs)  # Convert to string
    
    if "LEARNING_RATE" in contract.required_env_vars:
        env_vars["LEARNING_RATE"] = str(self.config.learning_rate)  # Convert to string
    
    # Set feature columns if available
    if "FEATURE_COLUMNS" in contract.required_env_vars and self.config.feature_columns:
        # Serialize list to comma-separated string
        env_vars["FEATURE_COLUMNS"] = ",".join(self.config.feature_columns)
    
    # Set optional variables with defaults from contract
    for var_name, default_value in contract.optional_env_vars.items():
        # Use config value if available, otherwise use contract default
        config_value = getattr(self.config, var_name.lower(), None)
        if config_value is not None:
            # Convert to string
            if isinstance(config_value, bool):
                env_vars[var_name] = str(config_value).lower()
            else:
                env_vars[var_name] = str(config_value)
        else:
            env_vars[var_name] = default_value
    
    return env_vars
```

## Testing and Validation

### Unit Testing Strategy

1. **Test Specifications**: Validate specifications against contracts
2. **Test Property Paths**: Validate property path consistency
3. **Test Builders**: Test input/output generation and environment variables
4. **Mock Dependencies**: Use mocks for SageMaker and AWS dependencies
5. **Test Edge Cases**: Test with various configuration scenarios

Example of a good specification test:

```python
def test_contract_alignment(self):
    """Test that the specification aligns with its contract."""
    # Arrange
    spec = YOUR_STEP_SPEC
    
    # Act
    result = spec.validate_contract_alignment()
    
    # Assert
    self.assertTrue(result.is_valid, f"Contract alignment failed: {result.errors}")
```

Example of a good builder test:

```python
def test_environment_variable_generation(self):
    """Test that environment variables are correctly generated."""
    # Arrange
    config = YourStepConfig(
        region="us-west-2",
        pipeline_s3_loc="s3://bucket/prefix",
        model_type="classification",
        num_epochs=10,
        learning_rate=0.01
    )
    builder = YourStepBuilder(config)
    
    # Act
    env_vars = builder._get_processor_env_vars()
    
    # Assert
    self.assertEqual(env_vars["MODEL_TYPE"], "classification")
    self.assertEqual(env_vars["NUM_EPOCHS"], "10")  # Check string conversion
    self.assertEqual(env_vars["LEARNING_RATE"], "0.01")  # Check string conversion
```

### Manual Validation Checklist

Before integration, validate your step implementation:

1. **Script Contract Alignment**: Ensure script uses paths from contract
2. **Specification-Contract Alignment**: Ensure logical names match
3. **Property Path Consistency**: Validate property paths follow standard format
4. **Environment Variable Setting**: Ensure all required variables are set
5. **Edge Case Handling**: Test with missing optional dependencies

Use the [validation checklist](Validation%20Checklist.md) for a comprehensive validation process.

## Integration and Deployment

### Step Registration

1. **Registry Update**: Update the step name registry
2. **Import Update**: Update `__init__.py` files
3. **Documentation**: Update documentation with new step
4. **Example Update**: Update examples with new step
5. **Pipeline Template**: Update pipeline templates

Example of proper step registration:

```python
# In step_names.py
STEP_NAMES = {
    # ... existing steps ...
    
    "YourNewStep": {
        "config_class": "YourNewStepConfig",
        "builder_step_name": "YourNewStepBuilder",
        "spec_type": "YourNewStep",
        "description": "Your step's description"
    },
}

# In pipeline_steps/__init__.py
from .builder_your_new_step import YourNewStepBuilder

# In pipeline_step_specs/__init__.py
from .your_new_step_spec import YOUR_NEW_STEP_SPEC
```

### Pipeline Integration

1. **Template Update**: Update pipeline templates to include your step
2. **DAG Update**: Update the DAG definition
3. **Config Map Update**: Update the config map
4. **Builder Map Update**: Update the builder map
5. **Documentation**: Document the integration

Example of pipeline template integration:

```python
def _create_pipeline_dag(self) -> PipelineDAG:
    dag = PipelineDAG()
    
    # Add nodes
    dag.add_node("data_loading")
    dag.add_node("preprocessing")
    dag.add_node("your_new_step")  # Add your new step
    dag.add_node("training")
    
    # Add edges
    dag.add_edge("data_loading", "preprocessing")
    dag.add_edge("preprocessing", "your_new_step")  # Connect to your step
    dag.add_edge("your_new_step", "training")  # Connect from your step
    
    return dag

def _create_config_map(self) -> Dict[str, BasePipelineConfig]:
    config_map = {}
    
    # Add your config
    your_new_step_config = self._get_config_by_type(YourNewStepConfig)
    if your_new_step_config:
        config_map["your_new_step"] = your_new_step_config
    
    # ... other configs ...
    return config_map
```

## Documentation

### Code Documentation

1. **Docstrings**: Add comprehensive docstrings to all classes and methods
2. **Type Hints**: Use type hints for parameters and return values
3. **Examples**: Include examples in docstrings
4. **Parameter Documentation**: Document all parameters
5. **Return Value Documentation**: Document return values

Example of good code documentation:

```python
def extract_inputs_from_dependencies(self, dependencies: List[Any]) -> Dict[str, str]:
    """Extract inputs from the given dependencies using the specification.
    
    This method uses the step specification to identify required inputs and
    extracts the corresponding S3 URIs from the provided dependency steps.
    It leverages the dependency resolver for semantic matching between outputs
    and dependencies.
    
    Args:
        dependencies: List of dependency step objects from the pipeline
    
    Returns:
        Dict mapping logical input names to S3 URIs
    
    Raises:
        ValueError: If a required dependency cannot be resolved
        TypeError: If dependencies is not a list
    """
    if not isinstance(dependencies, list):
        raise TypeError("Dependencies must be a list")
        
    if not dependencies or not self.dependency_resolver:
        return {}
    
    return self.dependency_resolver.resolve_dependencies(self.spec, dependencies)
```

### Comprehensive Examples

1. **End-to-End Examples**: Create end-to-end examples of using your step
2. **Configuration Examples**: Show how to configure your step
3. **Integration Examples**: Demonstrate integration with other steps
4. **Customization Examples**: Show how to customize your step
5. **Testing Examples**: Show how to test your step

For a comprehensive example of adding a new step, see the [Example](Example%20Adding%20a%20Feature%20Selection%20Step.md) document.

## Conclusion

By following these best practices, you'll create pipeline steps that are:

1. **Robust**: Resistant to errors and edge cases
2. **Maintainable**: Easy to understand and update
3. **Consistent**: Aligned with overall architecture
4. **Well-documented**: Clear and comprehensive documentation
5. **Tested**: Comprehensive unit and integration tests

This results in a pipeline that is both flexible and reliable, capable of handling complex machine learning workflows while maintaining stability and consistency.



-----------
##  Recommended Notes

