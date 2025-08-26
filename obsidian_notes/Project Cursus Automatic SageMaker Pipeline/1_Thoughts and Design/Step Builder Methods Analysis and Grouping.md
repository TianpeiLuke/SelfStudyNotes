---
tags:
  - thought
  - aws/sagemaker_pipeline
aliases: 
date of note: 2025-07-01
---

## 1. Core Initialization and Configuration Methods

These methods handle the initialization, validation, and basic configuration of step builders:

### Initialization Methods

- __`__init__`__: Present in all step builders. Initializes the builder with configuration, session, role, and notebook root. Validates the config type and calls the parent class initializer.

### Configuration Validation Methods

- __`validate_configuration`__: Abstract method implemented by all step builders. Validates that all required configuration attributes are present and valid before building the step.

## 2. Step Creation and Pipeline Integration Methods

These methods are responsible for creating the actual SageMaker pipeline steps and integrating them with the pipeline:

### Step Creation Methods

- __`create_step`__: The primary method implemented by all step builders. Creates and configures the specific SageMaker pipeline step with appropriate parameters.
- __`build`__: Inherited from `StepBuilderBase`. Combines `extract_inputs_from_dependencies` and `create_step` to build a pipeline step with inputs from dependencies.

### Helper Methods for Step Creation

- __`_create_transformer`__ (BatchTransformStepBuilder): Creates a SageMaker Transformer object.
- __`_create_pytorch_model`__ (PyTorchModelStepBuilder): Creates a PyTorchModel object.
- __`_create_model`__ (PyTorchModelStepBuilder): Creates a generic SageMaker Model object.
- __`_create_estimator`__ (XGBoostTrainingStepBuilder): Creates an XGBoost estimator for training.
- __`_get_processing_inputs`__ (ModelRegistrationStepBuilder): Creates ProcessingInput objects for the step.

## 3. Input/Output Management Methods

These methods handle the management of inputs and outputs for the step builders:

### Input Requirements and Output Properties Methods

- __`get_input_requirements`__: Implemented by all step builders. Returns a dictionary of input requirements.
- __`get_output_properties`__: Implemented by all step builders. Returns a dictionary of output properties.

### Input Extraction and Validation Methods

- __`_extract_param`__: Inherited from `StepBuilderBase`. Extracts a parameter from kwargs with a default value.
- __`_normalize_inputs`__: Inherited from `StepBuilderBase`. Normalizes inputs to a flat dictionary format.
- __`_validate_inputs`__: Inherited from `StepBuilderBase`. Validates that all required inputs are present.
- __`_validate_outputs`__: Inherited from `StepBuilderBase`. Validates that all required outputs are present.
- __`_check_missing_inputs`__: Inherited from `StepBuilderBase`. Checks for missing required inputs.

### Input/Output Mapping Methods

- __`_get_script_input_name`__: Inherited from `StepBuilderBase`. Maps logical input name to script input name.
- __`_get_output_destination_name`__: Inherited from `StepBuilderBase`. Maps logical output name to output destination name.
- __`_create_standard_processing_input`__: Inherited from `StepBuilderBase`. Creates a standard ProcessingInput.
- __`_create_standard_processing_output`__: Inherited from `StepBuilderBase`. Creates a standard ProcessingOutput.

## 4. Dependency Management Methods

These methods handle the extraction of inputs from dependency steps:
- [[Step Builder Methods Dependency Management Claude 4.0]]

### Dependency Extraction Methods

- __`extract_inputs_from_dependencies`__: Inherited from `StepBuilderBase`. Extracts inputs from dependency steps.
- __`_match_inputs_to_outputs`__: Inherited from `StepBuilderBase`. Matches input requirements with outputs from a dependency step.
- __`_match_model_artifacts`__: Inherited from `StepBuilderBase`. Matches model artifacts from a step to input requirements.
- __`_match_processing_outputs`__: Inherited from `StepBuilderBase`. Matches processing outputs from a step to input requirements.
- __`_match_list_outputs`__: Inherited from `StepBuilderBase`. Matches list-like outputs to input requirements.
- __`_match_dict_outputs`__: Inherited from `StepBuilderBase`. Matches dictionary-like outputs to input requirements.

### Custom Property Matching Methods

- __`_match_custom_properties`__: Overridden by all step builders. Matches custom properties specific to each step type.

  - __BatchTransformStepBuilder__: Looks for model_name from a ModelStep.
  - __PyTorchModelStepBuilder__: Looks for model artifacts from a TrainingStep.
  - __XGBoostTrainingStepBuilder__: Dispatches to specialized handlers for different step types.
  - __ModelRegistrationStepBuilder__: Handles complex matching for packaged models and payload samples.

## 5. Utility and Helper Methods

These methods provide utility functions for the step builders:

### Environment and Configuration Methods

- __`_get_environment_variables`__: Implemented by multiple step builders. Constructs environment variables for the step.
- __`_get_cache_config`__: Inherited from `StepBuilderBase`. Gets cache configuration for the step.
- __`_sanitize_name_for_sagemaker`__: Inherited from `StepBuilderBase`. Sanitizes a string to be a valid SageMaker resource name.
- __`_get_step_name`__: Inherited from `StepBuilderBase`. Gets a standard step name.

### Logging Methods

- __`log_info`__, __`log_debug`__, __`log_warning`__: Inherited from `StepBuilderBase`. Safely log messages, handling Pipeline variables.

### S3 Path Handling Methods (XGBoostTrainingStepBuilder)

- __`_normalize_s3_uri`__: Normalizes an S3 URI.
- __`_get_s3_directory_path`__: Gets the directory part of an S3 URI.
- __`_validate_s3_uri`__: Validates that a string is a properly formatted S3 URI.

### Property Path Registration Methods

- __`register_property_path`__: Class method in `StepBuilderBase`. Registers a runtime property path for a step type and logical name.
- __`register_instance_property_path`__: Instance method in `StepBuilderBase`. Registers a property path specific to an instance.
- __`get_property_paths`__: Method in `StepBuilderBase`. Gets the runtime property paths registered for a step type.
- __`get_all_property_paths`__: Method in `StepBuilderBase`. Gets all property paths for a step.

## 6. Specialized Methods

These methods are specific to certain step builders and handle specialized functionality:

### XGBoostTrainingStepBuilder Specialized Methods

- __`_prepare_hyperparameters_file`__: Serializes hyperparameters to JSON and uploads to S3.
- __`_get_training_inputs`__: Constructs TrainingInput objects for the training job.
- __`_match_tabular_preprocessing_outputs`__: Matches outputs from a TabularPreprocessingStep.
- __`_match_hyperparameter_outputs`__: Matches outputs from a HyperparameterPrepStep.
- __`_match_generic_outputs`__: Matches generic outputs from any step.

- [[Builder XGBoost Training Step]]

### ModelRegistrationStepBuilder Specialized Methods

- __`_try_fallback_s3_config`__: Fallback to constructing a path using pipeline_s3_loc from config.
- __`_handle_properties_list`__: Special handler for PropertiesList objects to safely extract S3Uri.

- [[Builder MODS Model Registration Step]]

## Key Patterns and Best Practices

1. __Standard Input/Output Naming Pattern__:

   - In config classes: `output_names = {"logical_name": "DescriptiveValue"}` (VALUE used as key in outputs dict)
   - In config classes: `input_names = {"logical_name": "ScriptInputName"}` (KEY used as key in inputs dict)

2. __Property Path Registration__:

   - Step builders register property paths to define how to access outputs at runtime.
   - Example: `StepBuilderBase.register_property_path("XGBoostTrainingStep", "model_output", "properties.ModelArtifacts.S3ModelArtifacts")`

3. __Input Extraction from Dependencies__:

   - Step builders implement custom property matching to extract inputs from dependency steps.
   - The base class provides generic matching methods, while step builders override `_match_custom_properties` for specialized matching.

4. __Safe Handling of Pipeline Variables__:

   - Step builders use safe logging methods to handle Pipeline variables.
   - Example: `self.log_info("Using input path: %s", input_path)` instead of direct string interpolation.





-----------
##  Recommended Notes

- [[Step Builder Methods Dependency Management Claude 4.0]]
- [[Step Builder Methods Analysis Average Code lines Statistics]]


- [[Base Step Builder]]
- [[Builder XGBoost Training Step]]
- [[Builder XGBoost Model Step]]
- [[Builder Tabular Preprocessing Step]]
- [[Builder Pytorch Training Step]]
- [[Builder Pytorch Model Step]]
- [[Builder Packaging Step]]
- [[Builder Batch Transform Step]]
- [[Builder MODS Model Registration Step]]
- [[Builder Payload Generation Step]]
- [[Builder MODS Cradle Data Loading Step]]
- 
