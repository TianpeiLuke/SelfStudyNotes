---
tags:
  - code
  - code_snippet
  - python/aws_python_sdk
keywords: 
topics: 
language: python
date of note: 2025-05-21
---

## Code Snippet Summary

>[!important]
>Step Builders serve as the **implementation bridge** that translates abstract [[Step Specification Design as Declarative Pipeline Architecture]] into executable SageMaker pipeline steps. 
>- They represent the "how" while [[Step Specification Design as Declarative Pipeline Architecture]] represent the "what", handling the concrete implementation details of pipeline step execution.


| Implementation        | Specification / Summary                        |
| --------------------- | ---------------------------------------------- |
| ![[step_script.png]]  | <br><br><br>![[step_spec_script_contract.png]] |
| [[Base Step Builder]] | [[Base Step Specification]]                    |

## Code

```python
from abc import ABC, abstractmethod
from typing import Dict, List, Optional, Any, Union, Callable, Tuple, Set
from pathlib import Path
import logging
from inspect import signature
import importlib
import warnings
```

### SageMaker Workflow

```python
from sagemaker.workflow.pipeline_context import PipelineSession
from sagemaker.workflow.steps import Step
from sagemaker.workflow.steps import CacheConfig
```

### Dependency Resolution

```python
from ..pipeline_deps.dependency_resolver import UnifiedDependencyResolver
from ..pipeline_deps.registry_manager import RegistryManager
from ..pipeline_deps.semantic_matcher import SemanticMatcher
from ..pipeline_deps.factory import create_dependency_resolver, create_pipeline_components
from ..pipeline_deps.property_reference import PropertyReference
```

- [[Dependency Resolver for Automatic Pipeline]]
- [[Registry Manager for Automatic Pipeline]]
- [[Specification Registry for Automatic Pipeline]]
- [[Property Reference Class as Bridge between Definition-time and Runtime]]

### Step Specifications

```python
from ..pipeline_deps.base_specifications import StepSpecification
```

- [[Base Step Specification]]

### Step Names

```python
# Import step names from central source of truth
from ..pipeline_registry.step_names import BUILDER_STEP_NAMES as STEP_NAMES
```

### Base Class

```python
class StepBuilderBase(ABC):
    """
    Base class for all step builders
    
    ## Safe Logging Methods
    
    To handle Pipeline variables safely in logs, use these methods:
    
    ```python
    # Instead of:
    logger.info(f"Using input path: {input_path}")  # May raise TypeError for Pipeline variables
    
    # Use:
    self.log_info("Using input path: %s", input_path)  # Handles Pipeline variables safely
    ```
    
    Standard Pattern for `input_names` and `output_names`:
    
    1. In **config classes**:
       ```python
       output_names = {"logical_name": "DescriptiveValue"}  # VALUE used as key in outputs dict
       input_names = {"logical_name": "ScriptInputName"}    # KEY used as key in inputs dict
       ```
    
    2. In **pipeline code**:
       ```python
       # Get output using VALUE from output_names
       output_value = step_a.config.output_names["logical_name"]
       output_uri = step_a.properties.ProcessingOutputConfig.Outputs[output_value].S3Output.S3Uri
       
       # Set input using KEY from input_names
       inputs = {"logical_name": output_uri}
       ```
    
    3. In **step builders**:
       ```python
       # For outputs - validate using VALUES
       value = self.config.output_names["logical_name"]
       if value not in outputs:
           raise ValueError(f"Must supply an S3 URI for '{value}'")
           
       # For inputs - validate using KEYS
       for logical_name in self.config.input_names.keys():
           if logical_name not in inputs:
               raise ValueError(f"Must supply an S3 URI for '{logical_name}'")
       ```
    
    Developers should follow this standard pattern when creating new step builders.
    The base class provides helper methods to enforce and simplify this pattern:
    
    - `_validate_inputs()`: Validates inputs using KEYS from input_names
    - `_validate_outputs()`: Validates outputs using VALUES from output_names
    - `_get_script_input_name()`: Maps logical name to script input name
    - `_get_output_destination_name()`: Maps logical name to output destination name
    - `_create_standard_processing_input()`: Creates standardized ProcessingInput
    - `_create_standard_processing_output()`: Creates standardized ProcessingOutput
    
    Property Path Registry:
    
    To bridge the gap between definition-time and runtime, step builders can register
    property paths that define how to access their outputs at runtime. This solves the
    issue where outputs are defined statically but only accessible via specific runtime paths.
    
    - `register_property_path()`: Registers a property path for a logical output name
    - `get_property_paths()`: Gets all registered property paths for this step
    """

    REGION_MAPPING: Dict[str, str] = {
        "NA": "us-east-1",
        "EU": "eu-west-1",
        "FE": "us-west-2"
    }

    # Define standard step names
    STEP_NAMES = STEP_NAMES

    # Common properties that all steps might need
    COMMON_PROPERTIES = {
        "dependencies": "Optional list of dependent steps",
        "enable_caching": "Whether to enable caching for this step (default: True)"
    }
    
    # Standard output properties for training steps
    TRAINING_OUTPUT_PROPERTIES = {
        "training_job_name": "Name of the training job",
        "model_data": "S3 path to the model artifacts",
        "model_data_url": "S3 URL to the model artifacts"
    }
    
    # Standard output properties for model steps
    MODEL_OUTPUT_PROPERTIES = {
        "model_artifacts_path": "S3 path to model artifacts",
        "model": "SageMaker model object"
    }
    

    def __init__(
        self,
        config: BasePipelineConfig,
        spec: Optional[StepSpecification] = None,  # New parameter
        sagemaker_session: Optional[PipelineSession] = None,
        role: Optional[str] = None,
        notebook_root: Optional[Path] = None,
        registry_manager: Optional[RegistryManager] = None,
        dependency_resolver: Optional[UnifiedDependencyResolver] = None
    ):
        """
        Initialize base step builder.
        
        Args:
            config: Model configuration
            spec: Optional step specification for specification-driven implementation
            sagemaker_session: SageMaker session
            role: IAM role
            notebook_root: Root directory of notebook
            registry_manager: Optional registry manager for dependency injection
            dependency_resolver: Optional dependency resolver for dependency injection
        """
        self.config = config
        self.spec = spec  # Store the specification
        self.session = sagemaker_session
        self.role = role
        self.notebook_root = notebook_root or Path.cwd()
        self._registry_manager = registry_manager
        self._dependency_resolver = dependency_resolver
        
        # Get contract from specification if available, or directly from config
        self.contract = getattr(spec, 'script_contract', None) if spec else None
        if not self.contract and hasattr(self.config, 'script_contract'):
            self.contract = self.config.script_contract

        # Validate and set AWS region
        self.aws_region = self.REGION_MAPPING.get(self.config.region)
        if not self.aws_region:
            raise ValueError(
                f"Invalid region code: {self.config.region}. "
                f"Must be one of: {', '.join(self.REGION_MAPPING.keys())}"
            )
            
        # Validate specification-contract alignment if both are provided
        if self.spec and self.contract and hasattr(self.spec, 'validate_contract_alignment'):
            result = self.spec.validate_contract_alignment()
            if not result.is_valid:
                raise ValueError(f"Spec-Contract alignment errors: {result.errors}")


        logger.info(f"Initializing {self.__class__.__name__} with region: {self.config.region}")
        self.validate_configuration()

    def _sanitize_name_for_sagemaker(self, name: str, max_length: int = 63) -> str:
        """
        Sanitize a string to be a valid SageMaker resource name component.
        
        Args:
            name: Name to sanitize
            max_length: Maximum length of sanitized name
            
        Returns:
            Sanitized name
        """
        if not name:
            return "default-name"
        sanitized = "".join(c if c.isalnum() else '-' for c in str(name))
        sanitized = '-'.join(filter(None, sanitized.split('-')))
        return sanitized[:max_length].rstrip('-')

    def _get_step_name(self, include_job_type: bool = True) -> str:
        """
        Get standard step name from builder class name, optionally including job_type.
        
        Builder class names follow the pattern: RegistryKey + "StepBuilder"
        (e.g., XGBoostTrainingStepBuilder)
        
        This method extracts the registry key by removing the "StepBuilder" suffix
        and optionally appends the job_type from the config.
        
        Args:
            include_job_type: Whether to include job_type suffix if available in config
        
        Returns:
            The canonical step name, optionally with job_type suffix
        """
        class_name = self.__class__.__name__
        
        # If class name follows the standard pattern, extract the registry key
        if class_name.endswith("StepBuilder"):
            canonical_name = class_name[:-11]  # Remove "StepBuilder" suffix
        else:
            # Fallback for non-standard class names
            self.log_warning(f"Class name '{class_name}' doesn't follow the convention. Using as is.")
            canonical_name = class_name
        
        # Validate that the extracted name exists in the registry
        if canonical_name not in self.STEP_NAMES:
            self.log_warning(f"Unknown step type: {canonical_name}. Using as is.")
        
        # Add job_type suffix if requested and available
        if include_job_type and hasattr(self.config, 'job_type') and self.config.job_type:
            return f"{canonical_name}-{self.config.job_type.capitalize()}"
        
        return canonical_name
        
    def _generate_job_name(self, step_type: str = None) -> str:
        """
        Generate a standardized job name for SageMaker processing/training jobs.
        
        This method automatically determines the step type from the class name
        if not provided, using the _get_step_name method. It adds a timestamp
        to ensure uniqueness across executions.
        
        Args:
            step_type: Optional type of step. If not provided, it will be 
                      determined automatically using _get_step_name.
            
        Returns:
            Sanitized job name suitable for SageMaker
        """
        import time
        
        # If step_type is not provided, use our simplified _get_step_name method
        if step_type is None:
            step_type = self._get_step_name()
        
        # Generate a timestamp for uniqueness (unix timestamp in seconds)
        timestamp = int(time.time())
        
        # Build the job name
        if hasattr(self.config, 'job_type') and self.config.job_type:
            job_name = f"{step_type}-{self.config.job_type.capitalize()}-{timestamp}"
        else:
            job_name = f"{step_type}-{timestamp}"
            
        # Sanitize and return
        return self._sanitize_name_for_sagemaker(job_name)
        
        
    def get_property_path(self, logical_name: str, format_args: Dict[str, Any] = None) -> Optional[str]:
        """
        Get property path for an output using the specification.
        
        This method retrieves the property path for an output from the specification.
        It also supports template formatting if format_args are provided.
        
        Args:
            logical_name: Logical name of the output
            format_args: Optional dictionary of format arguments for template paths
                        (e.g., {'output_descriptor': 'data'} for paths with placeholders)
        
        Returns:
            Property path from specification, formatted with args if provided,
            or None if not found
        """
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
            except Exception as e:
                logger.warning(f"Error formatting property path: {e}")
        
        return property_path
    
    def get_all_property_paths(self) -> Dict[str, str]:
        """
        Get all property paths defined in the specification.
        
        Returns:
            dict: Mapping from logical output names to runtime property paths
        """
        paths = {}
        if self.spec and hasattr(self.spec, 'outputs'):
            for _, output_spec in self.spec.outputs.items():
                if output_spec.property_path:
                    paths[output_spec.logical_name] = output_spec.property_path
        
        return paths
        
    def log_info(self, message, *args, **kwargs):
        """
        Safely log info messages, handling Pipeline variables.
        
        Args:
            message: The log message
            *args, **kwargs: Values to format into the message
        """
        try:
            # Convert args and kwargs to safe strings
            safe_args = [safe_value_for_logging(arg) for arg in args]
            safe_kwargs = {k: safe_value_for_logging(v) for k, v in kwargs.items()}
            
            # Log with safe values
            logger.info(message, *safe_args, **safe_kwargs)
        except Exception as e:
            logger.info(f"Original logging failed ({e}), logging raw message: {message}")
    
    def log_debug(self, message, *args, **kwargs):
        """Debug version of safe logging"""
        try:
            safe_args = [safe_value_for_logging(arg) for arg in args]
            safe_kwargs = {k: safe_value_for_logging(v) for k, v in kwargs.items()}
            logger.debug(message, *safe_args, **safe_kwargs)
        except Exception as e:
            logger.debug(f"Original logging failed ({e}), logging raw message: {message}")
    
    def log_warning(self, message, *args, **kwargs):
        """Warning version of safe logging"""
        try:
            safe_args = [safe_value_for_logging(arg) for arg in args]
            safe_kwargs = {k: safe_value_for_logging(v) for k, v in kwargs.items()}
            logger.warning(message, *safe_args, **safe_kwargs)
        except Exception as e:
            logger.warning(f"Original logging failed ({e}), logging raw message: {message}")
            
    def log_error(self, message, *args, **kwargs):
        """Error version of safe logging"""
        try:
            safe_args = [safe_value_for_logging(arg) for arg in args]
            safe_kwargs = {k: safe_value_for_logging(v) for k, v in kwargs.items()}
            logger.error(message, *safe_args, **safe_kwargs)
        except Exception as e:
            logger.error(f"Original logging failed ({e}), logging raw message: {message}")
            

    def _get_cache_config(self, enable_caching: bool = True) -> Dict[str, Any]:
        """
        Get cache configuration for step.         
        ProcessingStep.to_request() can call .config safely.
        
        Args:
            enable_caching: Whether to enable caching
            
        Returns:
            Cache configuration dictionary
        """
        return CacheConfig(
            enable_caching=enable_caching,
            expire_after="P30D"
        )

    def _get_environment_variables(self) -> Dict[str, str]:
        """
        Create environment variables for the processing job based on the script contract.
        
        This base implementation:
        1. Uses required_env_vars from the script contract
        2. Gets values from the config object
        3. Adds optional variables with defaults from the contract
        4. Can be overridden by child classes to add custom logic
        
        Returns:
            Dict[str, str]: Environment variables for the processing job
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
    
    def _get_job_arguments(self) -> Optional[List[str]]:
        """
        Constructs command-line arguments for the script based on script contract.
        If no arguments are defined in the contract, returns None (not an empty list).
        
        Returns:
            List of string arguments to pass to the script, or None if no arguments
        """
        if not hasattr(self, 'contract') or not self.contract:
            self.log_warning("No contract available for argument generation")
            return None
            
        # If contract has no expected arguments, return None
        if not hasattr(self.contract, 'expected_arguments') or not self.contract.expected_arguments:
            return None
            
        args = []
        
        # Add each expected argument with its value
        for arg_name, arg_value in self.contract.expected_arguments.items():
            args.extend([f"--{arg_name}", arg_value])
        
        # If we have arguments to return
        if args:
            self.log_info("Generated job arguments from contract: %s", args)
            return args
        
        # If we end up with an empty list, return None instead
        return None

    @abstractmethod
    def validate_configuration(self) -> None:
        """
        Validate configuration requirements.
        
        Raises:
            ValueError: If configuration is invalid
        """
        pass

        
    def get_required_dependencies(self) -> List[str]:
        """
        Get list of required dependency logical names from specification.
        
        This method provides direct access to the required dependencies defined in
        the step specification.
        
        Returns:
            List of logical names for required dependencies
            
        Raises:
            ValueError: If specification is not provided
        """
        if not self.spec or not hasattr(self.spec, 'dependencies'):
            raise ValueError("Step specification is required for dependency information")
            
        return [d.logical_name for _, d in self.spec.dependencies.items() if d.required]
    
    def get_optional_dependencies(self) -> List[str]:
        """
        Get list of optional dependency logical names from specification.
        
        This method provides direct access to the optional dependencies defined in
        the step specification.
        
        Returns:
            List of logical names for optional dependencies
            
        Raises:
            ValueError: If specification is not provided
        """
        if not self.spec or not hasattr(self.spec, 'dependencies'):
            raise ValueError("Step specification is required for dependency information")
            
        return [d.logical_name for _, d in self.spec.dependencies.items() if not d.required]
        
    def get_outputs(self) -> Dict[str, Any]:
        """
        Get output specifications directly from the step specification.
        
        This method provides direct access to the outputs defined in the
        step specification, returning the complete OutputSpec objects.
        
        Returns:
            Dictionary mapping output names to their OutputSpec objects
            
        Raises:
            ValueError: If specification is not provided
        """
        if not self.spec or not hasattr(self.spec, 'outputs'):
            raise ValueError("Step specification is required for output information")
            
        return {o.logical_name: o for _, o in self.spec.outputs.items()}
    
    @abstractmethod
    def _get_inputs(self, inputs: Dict[str, Any]) -> Any:
        """
        Get inputs for the step.
        
        This is a unified method that all derived classes must implement.
        Each derived class will return the appropriate input type for its step:
        - ProcessingInput list for ProcessingStep
        - Training channels dict for TrainingStep
        - Model location for ModelStep
        etc.
        
        Args:
            inputs: Dictionary mapping logical names to input sources
            
        Returns:
            Appropriate inputs object for the step type
        """
        pass
        
    @abstractmethod
    def _get_outputs(self, outputs: Dict[str, Any]) -> Any:
        """
        Get outputs for the step.
        
        This is a unified method that all derived classes must implement.
        Each derived class will return the appropriate output type for its step:
        - ProcessingOutput list for ProcessingStep
        - Output path for TrainingStep
        - Model output info for ModelStep
        etc.
        
        Args:
            outputs: Dictionary mapping logical names to output destinations
            
        Returns:
            Appropriate outputs object for the step type
        """
        pass
        
        
    def _get_context_name(self) -> str:
        """
        Get the context name to use for registry operations.
        
        Returns:
            Context name based on pipeline name or default
        """
        if hasattr(self.config, 'pipeline_name') and self.config.pipeline_name:
            return self.config.pipeline_name
        return "default"
        
    def _get_registry_manager(self) -> RegistryManager:
        """
        Get or create a registry manager.
        
        Returns:
            Registry manager instance
        """
        if not hasattr(self, '_registry_manager') or self._registry_manager is None:
            self._registry_manager = RegistryManager()
            self.log_debug("Created new registry manager")
        return self._registry_manager
        
    def _get_registry(self):
        """
        Get the appropriate registry for this step.
        
        Returns:
            Registry instance for the current context
        """
        registry_manager = self._get_registry_manager()
        context_name = self._get_context_name()
        return registry_manager.get_registry(context_name)
        
    def _get_dependency_resolver(self) -> UnifiedDependencyResolver:
        """
        Get or create a dependency resolver.
        
        Returns:
            Dependency resolver instance
        """
        if not hasattr(self, '_dependency_resolver') or self._dependency_resolver is None:
            registry = self._get_registry()
            semantic_matcher = SemanticMatcher()
            self._dependency_resolver = create_dependency_resolver(registry, semantic_matcher)
            self.log_debug(f"Created new dependency resolver for context '{self._get_context_name()}'")
        return self._dependency_resolver

    def extract_inputs_from_dependencies(self, dependency_steps: List[Step]) -> Dict[str, Any]:
        """
        Extract inputs from dependency steps using the UnifiedDependencyResolver.
        
        Args:
            dependency_steps: List of dependency steps
            
        Returns:
            Dictionary of inputs extracted from dependency steps
            
        Raises:
            ValueError: If dependency resolver is not available or specification is not provided
        """
        if not DEPENDENCY_RESOLVER_AVAILABLE:
            raise ValueError(
                "UnifiedDependencyResolver not available. Make sure pipeline_deps module is installed."
            )
            
        if not self.spec:
            raise ValueError(
                "Step specification is required for dependency extraction."
            )
            
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


    def _enhance_dependency_steps_with_specs(self, resolver: Any, 
                                           dependency_steps: List[Step], 
                                           available_steps: List[str]) -> None:
        """
        Enhance dependency steps with specifications and additional metadata.
        
        This method extracts specifications from dependency steps and adds them to the resolver.
        It also extracts additional metadata to help with dependency resolution for steps
        that don't have specifications.
        
        Args:
            resolver: The UnifiedDependencyResolver instance
            dependency_steps: List of dependency steps
            available_steps: List to populate with step names
        """
        from ..pipeline_deps.base_specifications import StepSpecification, OutputSpec
        
        for i, dep_step in enumerate(dependency_steps):
            # Get step name
            dep_name = getattr(dep_step, 'name', f"Step_{i}")
            available_steps.append(dep_name)
            
            # Try to get specification from step
            dep_spec = None
            if hasattr(dep_step, '_spec'):
                dep_spec = getattr(dep_step, '_spec')
            elif hasattr(dep_step, 'spec'):
                dep_spec = getattr(dep_step, 'spec')
                
            if dep_spec:
                resolver.register_specification(dep_name, dep_spec)
                logger.debug(f"Registered specification for dependency step '{dep_name}'")
                continue
            
            # If no specification, try to create a minimal one
            try:
                # For model artifacts from training steps
                if hasattr(dep_step, "properties") and hasattr(dep_step.properties, "ModelArtifacts"):
                    minimal_spec = StepSpecification(
                        step_type=dep_name,
                        description=f"Auto-generated spec for {dep_name}",
                        dependencies={},
                        outputs={
                            "model": OutputSpec(
                                logical_name="model",
                                description="Model artifacts",
                                property_path="properties.ModelArtifacts.S3ModelArtifacts"
                            )
                        }
                    )
                    resolver.register_specification(dep_name, minimal_spec)
                    logger.info(f"Created minimal model spec for {dep_name}")
                
                # For processing outputs
                elif (hasattr(dep_step, "properties") and 
                      hasattr(dep_step.properties, "ProcessingOutputConfig") and
                      hasattr(dep_step.properties.ProcessingOutputConfig, "Outputs")):
                    
                    outputs = {}
                    processing_outputs = dep_step.properties.ProcessingOutputConfig.Outputs
                    
                    # Handle dictionary-like outputs
                    if hasattr(processing_outputs, "items"):
                        try:
                            for key, output in processing_outputs.items():
                                if hasattr(output, "S3Output") and hasattr(output.S3Output, "S3Uri"):
                                    outputs[key] = OutputSpec(
                                        logical_name=key,
                                        description=f"Output {key}",
                                        property_path=f"properties.ProcessingOutputConfig.Outputs['{key}'].S3Output.S3Uri"
                                    )
                        except (AttributeError, TypeError):
                            pass
                    
                    # Handle list-like outputs
                    elif hasattr(processing_outputs, "__getitem__"):
                        try:
                            for i, output in enumerate(processing_outputs):
                                if hasattr(output, "S3Output") and hasattr(output.S3Output, "S3Uri"):
                                    key = f"output_{i}"
                                    outputs[key] = OutputSpec(
                                        logical_name=key,
                                        description=f"Output at index {i}",
                                        property_path=f"properties.ProcessingOutputConfig.Outputs[{i}].S3Output.S3Uri"
                                    )
                        except (IndexError, TypeError, AttributeError):
                            pass
                    
                    if outputs:
                        minimal_spec = StepSpecification(
                            step_type=dep_name,
                            description=f"Auto-generated spec for {dep_name}",
                            dependencies={},
                            outputs=outputs
                        )
                        resolver.register_specification(dep_name, minimal_spec)
                        logger.info(f"Created minimal processing spec for {dep_name} with {len(outputs)} outputs")
            
            except Exception as e:
                logger.debug(f"Error creating minimal specification for {dep_name}: {e}")
    
    @abstractmethod
    def create_step(self, **kwargs) -> Step:
        """
        Create pipeline step.
        
        This method should be implemented by all step builders to create a SageMaker pipeline step.
        It accepts a dictionary of keyword arguments that can be used to configure the step.
        
        Common parameters that all step builders should handle:
        - dependencies: Optional list of steps that this step depends on
        - enable_caching: Whether to enable caching for this step (default: True)
        
        Step-specific parameters should be extracted from kwargs as needed.
        
        Args:
            **kwargs: Keyword arguments for configuring the step
            
        Returns:
            SageMaker pipeline step
        """
        pass
```




## Derived Classes

- [[Builder MODS Cradle Data Loading Step]]
- [[Builder Tabular Preprocessing Step]]
- [[Builder Pytorch Model Step]]
- [[Builder Pytorch Training Step]]
- [[Builder XGBoost Model Step]]
- [[Builder XGBoost Training Step]]
- [[Builder XGBoost Model Evaluation Step]]
- [[Builder Packaging Step]]
- [[Builder Payload Generation Step]]
- [[Builder MODS Model Registration Step]]
- [[Builder Batch Transform Step]]



-----------
##  Recommended Notes

- [[Design Pattern Builder Pattern]]
- [[Design Pattern Abstract Factory Pattern]]

- [[MLOps]]
- [[Continuous Delivery or CD in DevOps and MLOps]]
- [[Continuous Integration or CI in DevOps and MLOps]]
