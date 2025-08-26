---
tags:
  - thought
  - design
  - aws/sagemaker_pipeline
aliases: 
date of note: 2025-07-03
---
## What is the Purpose of Step Builder?

>[!important]
>Step Builders serve as the **implementation bridge** that translates abstract [[Step Specification Design as Declarative Pipeline Architecture]] into executable SageMaker pipeline steps. 
>- They represent the "how" while [[Step Specification Design as Declarative Pipeline Architecture]]  represent the "what", handling the concrete implementation details of pipeline step execution.

## Core Purpose

>[!important]
> Step Builders provide the **concrete implementation layer** that:
> 
> 1. **Implementation Bridge** - Convert [specifications](step_specification.md) into SageMaker steps
> 2. **Input/Output Transformation** - Map logical names to SageMaker properties
> 3. **Configuration Integration** - Apply step-specific settings from [configs](config.md)
> 4. **Validation and Error Handling** - Runtime validation with meaningful errors
> 5. **SageMaker Integration** - Handle SageMaker-specific complexities
> 6. **Script Contract Alignment** - Ensure alignment between specs, contracts, and implementations

## Key Features

### 1. Implementation Bridge

Step Builders translate abstract [specifications](step_specification.md) into executable SageMaker steps:

```python
class XGBoostTrainingStepBuilder(StepBuilderBase):
    """Converts XGBoost training specification into SageMaker TrainingStep"""
    
    def __init__(self, config: XGBoostTrainingConfig, ...):
        # Initialize with specification
        super().__init__(
            config=config,
            spec=XGBOOST_TRAINING_SPEC,  # Connect to the specification
            sagemaker_session=sagemaker_session,
            ...
        )
        self.config: XGBoostTrainingConfig = config
        
    def build_step(self, inputs: Dict[str, Any]) -> TrainingStep:
        """Transform specification + config + inputs into SageMaker step"""
        
        # Validate inputs against specification
        self.validate_inputs(inputs)
        
        # Get inputs and outputs using specification and contract
        training_inputs = self._get_inputs(inputs)
        output_path = self._get_outputs({})
        
        # Build SageMaker TrainingStep with proper configuration
        estimator = self._create_estimator(output_path)
        return TrainingStep(
            name=self.step_name,
            estimator=estimator,
            inputs=training_inputs,
            **self._get_sagemaker_step_kwargs()
        )
```

### 2. Input/Output Transformation with Specifications

Handle translation between logical names and SageMaker properties using specifications:

```python
def _get_inputs(self, inputs: Dict[str, Any]) -> Dict[str, TrainingInput]:
    """Convert logical input names to SageMaker TrainingInput objects using specifications"""
    if not self.spec:
        raise ValueError("Step specification is required")
        
    if not self.contract:
        raise ValueError("Script contract is required for input mapping")
    
    training_inputs = {}
    
    # Process each dependency in the specification
    for _, dependency_spec in self.spec.dependencies.items():
        logical_name = dependency_spec.logical_name
        
        # Skip if optional and not provided
        if not dependency_spec.required and logical_name not in inputs:
            continue
            
        # Make sure required inputs are present
        if dependency_spec.required and logical_name not in inputs:
            raise ValueError(f"Required input '{logical_name}' not provided")
        
        # Get container path from contract
        container_path = None
        if logical_name in self.contract.expected_input_paths:
            container_path = self.contract.expected_input_paths[logical_name]
            
            # Extract the channel name from the container path
            parts = container_path.split('/')
            if len(parts) > 4 and parts[1] == "opt" and parts[2] == "ml" and parts[3] == "input" and parts[4] == "data":
                channel_name = parts[5]  # Extract channel name from path
                training_inputs[channel_name] = TrainingInput(s3_data=inputs[logical_name])
    
    return training_inputs

def get_output_reference(self, logical_name: str):
    """Convert logical output name to SageMaker property reference using specification"""
    # Find the OutputSpec in the specification
    if not self.spec:
        raise ValueError("Step specification required for output reference")
    
    # Find the matching output spec
    output_spec = None
    for _, out_spec in self.spec.outputs.items():
        if out_spec.logical_name == logical_name:
            output_spec = out_spec
            break
            
    if not output_spec:
        raise ValueError(f"Unknown output name: {logical_name}")
    
    # Use the property path from the output spec
    property_path = output_spec.property_path
    if not property_path:
        raise ValueError(f"No property path defined for output: {logical_name}")
        
    # Convert property path to actual property reference
    return self._resolve_property_path(property_path)
```

### 3. Configuration Integration

Integrate with the [configuration system](config.md) to apply step-specific settings:

```python
def _create_xgboost_estimator(self):
    """Create XGBoost estimator from configuration"""
    return XGBoost(
        entry_point=self.config.training_entry_point,
        framework_version=self.config.framework_version,
        instance_type=self.config.training_instance_type,
        instance_count=self.config.training_instance_count,
        hyperparameters=self.config.hyperparameters.model_dump(),
        role=self.role,
        **self._get_estimator_kwargs()
    )
```

### 4. Validation and Error Handling

Implement runtime validation with meaningful error messages using specifications:

```python
def validate_inputs(self, inputs):
    """Validate inputs against step specification"""
    if not self.spec:
        raise ValueError("Step specification is required for input validation")
    
    # Check required inputs
    for _, dep_spec in self.spec.dependencies.items():
        if dep_spec.required and dep_spec.logical_name not in inputs:
            raise ValueError(
                f"Required input '{dep_spec.logical_name}' missing for {self.step_name}. "
                f"Expected from: {dep_spec.compatible_sources}"
            )
    
    # Validate input types and formats
    for input_name, input_value in inputs.items():
        # Find the dependency spec for this input
        dep_spec = None
        for _, spec in self.spec.dependencies.items():
            if spec.logical_name == input_name:
                dep_spec = spec
                break
                
        if dep_spec and dep_spec.data_type == "S3Uri":
            self._validate_s3_uri(input_value, input_name)
```

### 5. SageMaker Integration

Handle SageMaker-specific complexities:

```python
def _get_sagemaker_step_kwargs(self):
    """Handle SageMaker-specific configuration"""
    kwargs = {}
    
    # Add retry configuration
    if self.config.retry_policies:
        kwargs["retry_policies"] = self.config.retry_policies
    
    # Add caching configuration
    if self.config.enable_caching:
        kwargs["cache_config"] = self._get_cache_config(True)
    
    # Add step dependencies (not data dependencies)
    if self.config.depends_on:
        kwargs["depends_on"] = self.config.depends_on
    
    return kwargs
```

#### Standardized Environment Variables from Script Contract

The base class provides a standardized method for handling environment variables based on script contracts:

```python
def _get_environment_variables(self) -> Dict[str, str]:
    """
    Create environment variables for the processing job based on the script contract.
    
    This base implementation:
    1. Uses required_env_vars from the script contract
    2. Gets values from the config object
    3. Adds optional variables with defaults from the contract
    4. Can be overridden by child classes to add custom logic
    """
    env_vars = {}
    
    if not hasattr(self, 'contract') or self.contract is None:
        self.log_warning("No script contract available for environment variable definition")
        return env_vars
    
    # Process required environment variables
    for env_var in self.contract.required_env_vars:
        # Convert from ENV_VAR_NAME format to config attribute style (env_var_name)
        config_attr = env_var.lower()
        
        # Try to get from config (direct attribute)
        if hasattr(self.config, config_attr):
            env_vars[env_var] = str(getattr(self.config, config_attr))
        # Try to get from config.hyperparameters
        elif hasattr(self.config, 'hyperparameters') and hasattr(self.config.hyperparameters, config_attr):
            env_vars[env_var] = str(getattr(self.config.hyperparameters, config_attr))
        else:
            self.log_warning(f"Required environment variable '{env_var}' not found in config")
    
    # Add optional environment variables with defaults
    for env_var, default_value in self.contract.optional_env_vars.items():
        # Convert from ENV_VAR_NAME format to config attribute style (env_var_name)
        config_attr = env_var.lower()
        
        # Try to get from config, fall back to default
        if hasattr(self.config, config_attr):
            env_vars[env_var] = str(getattr(self.config, config_attr))
        # Try to get from config.hyperparameters
        elif hasattr(self.config, 'hyperparameters') and hasattr(self.config.hyperparameters, config_attr):
            env_vars[env_var] = str(getattr(self.config.hyperparameters, config_attr))
        else:
            env_vars[env_var] = default_value
            self.log_debug(f"Using default value for optional environment variable '{env_var}': {default_value}")
    
    return env_vars
```

This method provides consistent environment variable handling across all step builders by:

1. Examining the script contract's `required_env_vars` and `optional_env_vars`
2. Automatically converting environment variable names (e.g., `LABEL_FIELD`) to config attribute style (`label_field`)
3. Looking for values in both the main config object and its `hyperparameters` attribute
4. Using default values from the contract for optional variables when not found in config
5. Providing helpful warnings for missing required variables

Child classes can:
- Use this implementation as-is if they follow the naming conventions
- Override it while still calling `super()._get_environment_variables()` to extend the base implementation
- Completely replace it with custom logic when needed

Usage example:

```python
# In a processor creation method
def _create_processor(self):
    """Create the processor for the processing job"""
    return SKLearnProcessor(
        framework_version=self.config.processing_framework_version,
        role=self.role,
        instance_type=self.config.processing_instance_type,
        instance_count=self.config.processing_instance_count,
        volume_size_in_gb=self.config.processing_volume_size,
        env=self._get_environment_variables(),  # Gets variables from script contract
        sagemaker_session=self.session
    )
```

#### Standardized Step Name Generation

The base class provides a method for getting standard step names with automatic step type detection:

```python
def _get_step_name(self) -> str:
    """
    Get standard step name, automatically determining the step type from class name.
    
    Returns:
        Standard step name based on the builder class
    """
    class_name = self.__class__.__name__
    determined_step_type = None
    
    # Try to find a matching entry in the STEP_NAMES registry
    for canonical_name, info in self.STEP_NAMES.items():
        if info["builder_step_name"] == class_name or class_name.startswith(info["builder_step_name"]):
            determined_step_type = canonical_name
            break
    
    # If no match found, fall back to class name with "StepBuilder" removed
    if determined_step_type is None:
        if class_name.endswith("StepBuilder"):
            determined_step_type = class_name[:-11]  # Remove "StepBuilder"
        else:
            determined_step_type = class_name
    
    # Get the step name from the registry or use default
    if determined_step_type not in self.STEP_NAMES:
        self.log_warning(f"Unknown step type: {determined_step_type}. Using default name.")
        return f"Default{determined_step_type}Step"
    
    return self.STEP_NAMES[determined_step_type]
```

This method provides consistent step naming across all pipeline steps by:

1. **Auto-detecting step type** from the class name using the centralized registry
2. **Looking up standardized names** from the registry to ensure consistency
3. **Handling fallback scenarios** when a step type isn't found in the registry

Usage example:

```python
# In a step builder's create_step method
step = TrainingStep(
    name=self._get_step_name(),  # No parameter needed - automatically detects from class name
    estimator=estimator,
    inputs=inputs,
    depends_on=dependencies
)
```

#### Standardized Job Name Generation

The base class provides a standardized method for generating SageMaker job names across all step builders:

```python
def _generate_job_name(self) -> str:
    """
    Generate a standardized job name for SageMaker processing/training jobs.
    
    This method automatically determines the step type from the class name
    using the centralized step name registry. It also adds a timestamp to 
    ensure uniqueness across executions.
        
    Returns:
        Sanitized job name suitable for SageMaker
    """
    import time
    
    # Determine step type from the class name
    class_name = self.__class__.__name__
    determined_step_type = None
    
    # Try to find a matching entry in the STEP_NAMES registry
    for canonical_name, info in self.STEP_NAMES.items():
        if info["builder_step_name"] == class_name or class_name.startswith(info["builder_step_name"]):
            determined_step_type = canonical_name
            break
    
    # If no match found, fall back to class name with "StepBuilder" removed
    if determined_step_type is None:
        if class_name.endswith("StepBuilder"):
            determined_step_type = class_name[:-11]  # Remove "StepBuilder"
        else:
            determined_step_type = class_name
            
    # Generate a timestamp for uniqueness (unix timestamp in seconds)
    timestamp = int(time.time())
    
    # Build the job name
    if hasattr(self.config, 'job_type') and self.config.job_type:
        job_name = f"{determined_step_type}-{self.config.job_type.capitalize()}-{timestamp}"
    else:
        job_name = f"{determined_step_type}-{timestamp}"
        
    # Sanitize and return
    return self._sanitize_name_for_sagemaker(job_name)
```

This ensures consistent job naming across all processing and training steps, making it easier to identify jobs in the SageMaker console. The method:

1. **Auto-detects step type** from the class name using the centralized step name registry
2. **Adds a timestamp** to ensure unique job names across multiple executions
3. **Handles job types** for multi-purpose step builders
4. **Sanitizes** the name to be compatible with SageMaker naming constraints

Job naming follows these patterns:

1. For multi-purpose step builders with job types:
   - `{step_type}-{job_type}-{timestamp}` (e.g., "TabularPreprocessing-Training-1721606523")

2. For single-purpose step builders:
   - `{step_type}-{timestamp}` (e.g., "XGBoostTraining-1721606523")

Usage example:

```python
# In a processing step builder
step = processor.run(
    code=self.config.get_script_path(),
    inputs=processing_inputs,
    outputs=processing_outputs,
    arguments=script_args,
    job_name=self._generate_job_name(),  # No parameter needed
    wait=False,
    cache_config=cache_config
)
```

### 6. Script Contract Alignment

Ensure alignment between specifications, contracts, and implementations:

```python
def __init__(self, config, spec=None, ...):
    """Initialize with both configuration and specification"""
    self.config = config
    self.spec = spec
    
    # Get contract from specification if available
    self.contract = getattr(spec, 'script_contract', None) if spec else None
    if not self.contract and hasattr(self.config, 'script_contract'):
        self.contract = self.config.script_contract
        
    # Validate specification-contract alignment
    if self.spec and self.contract and hasattr(self.spec, 'validate_contract_alignment'):
        result = self.spec.validate_contract_alignment()
        if not result.is_valid:
            raise ValueError(f"Spec-Contract alignment errors: {result.errors}")
```

## Integration with Other Components

### With Step Specifications

Step Builders now fully implement the behavior defined by [specifications](step_specification.md):

```python
class XGBoostTrainingStepBuilder(StepBuilderBase):
    def __init__(self, config: XGBoostTrainingConfig, ...):
        # Initialize with specification during construction
        super().__init__(
            config=config,
            spec=XGBOOST_TRAINING_SPEC,
            sagemaker_session=sagemaker_session,
            ...
        )
    
    def create_step(self, **kwargs):
        """Create step using specification-driven dependency resolution"""
        # Extract common parameters
        inputs_raw = kwargs.get('inputs', {})
        dependencies = kwargs.get('dependencies', [])
        
        # If dependencies are provided, extract inputs using the resolver
        if dependencies:
            try:
                extracted_inputs = self.extract_inputs_from_dependencies(dependencies)
                inputs.update(extracted_inputs)
            except Exception as e:
                self.log_warning("Failed to extract inputs from dependencies: %s", e)
        
        # Generate step with specification-validated inputs
        training_inputs = self._get_inputs(inputs)
        output_path = self._get_outputs({})
        estimator = self._create_estimator(output_path)
        
        # Create the training step
        step = TrainingStep(
            name=self._get_step_name(),  # Automatic step type detection
            estimator=estimator,
            inputs=training_inputs,
            depends_on=dependencies,
            cache_config=self._get_cache_config(enable_caching)
        )
        
        # Attach specification to the step for future reference
        setattr(step, '_spec', self.spec)
        
        return step
```

### With Configs

Step Builders use dependency injection pattern with [configs](config.md) and link them with script contracts:

```python
class XGBoostTrainingStepBuilder(StepBuilderBase):
    def __init__(self, config: XGBoostTrainingConfig, ...):
        """Initialize with configuration and link to script contract"""
        super().__init__(config=config, spec=XGBOOST_TRAINING_SPEC, ...)
        self.config = config
        
        # Ensure we have a script contract
        if not self.contract:
            raise ValueError("Script contract is required for proper operation")
    
    def _create_estimator(self, output_path=None):
        """Create estimator using configuration and contract"""
        # Get entry point from contract if possible
        entry_point = self.contract.entry_point if self.contract else self.config.training_entry_point
        
        return XGBoost(
            entry_point=entry_point,
            source_dir=self.config.source_dir,
            framework_version=self.config.framework_version,
            instance_type=self.config.training_instance_type,
            instance_count=self.config.training_instance_count,
            role=self.role,
            output_path=output_path,
            environment=self._get_environment_variables(),
        )
```

### With Dependency Resolver

Step Builders now work with the [UnifiedDependencyResolver](dependency_resolver.md) for automated input resolution:

```python
def extract_inputs_from_dependencies(self, dependency_steps: List[Step]) -> Dict[str, Any]:
    """Extract inputs from dependency steps using the UnifiedDependencyResolver."""
    if not self.spec:
        raise ValueError("Step specification is required for dependency extraction.")
        
    # Get step name
    step_name = self.__class__.__name__.replace("Builder", "Step")
    
    # Use the injected resolver or create one
    resolver = self._get_dependency_resolver()
    resolver.register_specification(step_name, self.spec)
    
    # Register dependencies and enhance them with metadata
    available_steps = []
    self._enhance_dependency_steps_with_specs(resolver, dependency_steps, available_steps)
    
    # One method call handles what used to require multiple matching methods
    resolved = resolver.resolve_step_dependencies(step_name, available_steps)
    
    # Convert results to SageMaker properties
    return {name: prop_ref.to_sagemaker_property() for name, prop_ref in resolved.items()}
```

## Extended Base Builder Class with Specification Support

```python
class StepBuilderBase:
    """Base class for all step builders with specification support"""
    
    def __init__(self, config, spec=None, sagemaker_session=None, ...):
        """Initialize base step builder with specification"""
        self.config = config
        self.spec = spec  # Store the specification
        self.session = sagemaker_session
        
        # Get contract from specification or config
        self.contract = getattr(spec, 'script_contract', None) if spec else None
        if not self.contract and hasattr(self.config, 'script_contract'):
            self.contract = self.config.script_contract
        
        # Validate specification-contract alignment
        if self.spec and self.contract and hasattr(self.spec, 'validate_contract_alignment'):
            result = self.spec.validate_contract_alignment()
            if not result.is_valid:
                raise ValueError(f"Spec-Contract alignment errors: {result.errors}")
                
    def get_property_path(self, logical_name: str, format_args: Dict[str, Any] = None) -> Optional[str]:
        """Get property path for an output using the specification."""
        property_path = None
        
        # Get property path from specification outputs
        if self.spec and hasattr(self.spec, 'outputs'):
            for _, output_spec in self.spec.outputs.items():
                if output_spec.logical_name == logical_name and output_spec.property_path:
                    property_path = output_spec.property_path
                    break
        
        if not property_path:
            return None
            
        # If found and format args are provided, format the path
        if format_args:
            try:
                property_path = property_path.format(**format_args)
            except KeyError as e:
                logger.warning(f"Missing format key {e} for property path template: {property_path}")
        
        return property_path
    
    def get_required_dependencies(self) -> List[str]:
        """Get list of required dependency logical names from specification."""
        if not self.spec or not hasattr(self.spec, 'dependencies'):
            raise ValueError("Step specification is required for dependency information")
            
        return [d.logical_name for _, d in self.spec.dependencies.items() if d.required]
```

## Strategic Value of Spec-Driven Step Builders

Spec-driven Step Builders provide:

1. **Implementation Abstraction**: Hide SageMaker complexity from users
2. **Specification Compliance**: Ensure implementations match [specifications](step_specification.md)
3. **Contract Enforcement**: Validate alignment between specification and script contracts
4. **Automatic Dependency Resolution**: Enable automatic connections between steps
5. **Runtime Validation**: Comprehensive error handling with specification-based messages
6. **Integration Points**: Bridge between declarative specifications and SageMaker steps
7. **Reusability**: Common patterns can be shared across different step types
8. **Maintainability**: Changes to SageMaker APIs isolated to builders
9. **Clarity of Intent**: Clear separation between "what" (specs) and "how" (implementation)

## Example Usage with Specifications

```python
# Create a step builder with configuration and specification
config = XGBoostTrainingConfig(
    training_instance_type="ml.m5.xlarge",
    hyperparameters=XGBoostModelHyperparameters(max_depth=6, eta=0.3)
)
builder = XGBoostTrainingStepBuilder(config=config)  # Specification loaded internally

# Connect from previous steps using specification-based dependency resolution
preprocessing_step = preprocess_builder.create_step()
training_step = builder.create_step(dependencies=[preprocessing_step])  # Automatic input extraction

# Get output references using specification
model_artifacts = builder.get_output_reference("model_output")  # Uses property path from specification
evaluation_output = builder.get_output_reference("evaluation_output")
```

## Usage in Pipeline Templates

```python
class XGBoostTrainingPipeline(PipelineTemplateBase):
    """Pipeline template that uses specification-driven dependency resolution"""
    
    def _create_pipeline_dag(self) -> PipelineDAG:
        # Create the DAG structure
        dag = PipelineDAG()
        dag.add_node("data_loading")
        dag.add_node("preprocessing") 
        dag.add_node("training")
        
        # Define logical connections, implementations handled by specifications
        dag.add_edge("data_loading", "preprocessing")
        dag.add_edge("preprocessing", "training")
        
        return dag
```

Step Builders form the **implementation foundation** that makes the spec-driven design practical and usable in real-world ML pipeline development, handling all the complex details of SageMaker integration while enabling declarative, specification-driven pipeline composition.
