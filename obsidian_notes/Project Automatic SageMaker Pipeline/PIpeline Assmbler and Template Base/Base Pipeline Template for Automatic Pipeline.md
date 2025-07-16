---
tags:
  - code
  - code_snippet
  - aws/sagemaker_pipeline
  - amazon/mods_pipeline
keywords: 
topics: 
language: python
date of note: 2025-07-16
---

## Code Snippet Summary

>[!important]
>The **Pipeline Builder Template** is a powerful abstraction that simplifies the creation of complex SageMaker pipelines. 
>- It uses a *declarative approach* with *specification-driven dependency resolution* to 
>	- define pipeline structure and 
>	- automatically handles the connections between steps, eliminating the need for manual wiring of inputs and outputs.


>[!important]
> The implementation consists of two key classes:
> 1. `PipelineTemplateBase`: An abstract base class that provides a consistent structure for all pipeline templates
> 2. `PipelineAssembler`: A concrete class that assembles pipeline steps using a DAG structure and specification-based dependency resolution

- [[Pipeline Assembler for Automatic Pipeline]]
## Code

The `PipelineTemplateBase` provides a standardized approach for creating pipeline templates, reducing code duplication and enforcing best practices.

```python
class PipelineTemplateBase(ABC):
    """Base class for all pipeline templates."""
    
    # This should be overridden by subclasses to specify the config classes
    # that are expected in the configuration file
    CONFIG_CLASSES: Dict[str, Type[BasePipelineConfig]] = {}
    
    def __init__(
        self,
        config_path: str,
        sagemaker_session: Optional[PipelineSession] = None,
        role: Optional[str] = None,
        notebook_root: Optional[Path] = None,
        registry_manager: Optional[RegistryManager] = None,
        dependency_resolver: Optional[UnifiedDependencyResolver] = None
    ):
        """Initialize base template."""
```

### Key Methods

#### Configuration Loading
```python
def _load_configs(self, config_path: str) -> Dict[str, BasePipelineConfig]:
    """Load configurations from file."""
    
def _get_base_config(self) -> BasePipelineConfig:
    """Get base configuration."""
```

#### Component Management
```python
def _initialize_components(self) -> None:
    """Initialize dependency resolution components."""
```

#### Abstract Methods
```python
@abstractmethod
def _validate_configuration(self) -> None:
    """Perform lightweight validation of configuration structure and essential parameters."""
    
@abstractmethod
def _create_pipeline_dag(self) -> PipelineDAG:
    """Create the DAG structure for the pipeline."""
    
@abstractmethod
def _create_config_map(self) -> Dict[str, BasePipelineConfig]:
    """Create a mapping from step names to config instances."""
    
@abstractmethod
def _create_step_builder_map(self) -> Dict[str, Type[StepBuilderBase]]:
    """Create a mapping from step types to builder classes."""
```

#### Pipeline Generation
```python
def generate_pipeline(self) -> Pipeline:
    """Generate the SageMaker Pipeline."""
```

#### Factory Methods
```python
@classmethod
def create_with_components(cls, config_path: str, context_name: Optional[str] = None, **kwargs):
    """Create template with managed dependency components."""
    
@classmethod
def build_with_context(cls, config_path: str, **kwargs) -> Pipeline:
    """Build pipeline with scoped dependency resolution context."""
    
@classmethod
def build_in_thread(cls, config_path: str, **kwargs) -> Pipeline:
    """Build pipeline using thread-local component instances."""
```

## PipelineAssembler

The `PipelineAssembler` is responsible for assembling pipeline steps using a DAG structure and specification-based dependency resolution.

```python
class PipelineAssembler:
    """
    Assembles pipeline steps using a DAG and step builders with specification-based dependency resolution.
    """
    def __init__(
        self,
        dag: PipelineDAG,
        config_map: Dict[str, BasePipelineConfig],
        step_builder_map: Dict[str, Type[StepBuilderBase]],
        sagemaker_session: Optional[PipelineSession] = None,
        role: Optional[str] = None,
        pipeline_parameters: Optional[List[ParameterString]] = None,
        notebook_root: Optional[Path] = None,
        registry_manager: Optional[RegistryManager] = None,
        dependency_resolver: Optional[UnifiedDependencyResolver] = None
    ):
        """Initialize the pipeline assembler."""
```

### Key Methods

#### Step Builder Initialization
```python
def _initialize_step_builders(self) -> None:
    """Initialize step builders for all steps in the DAG."""
```

#### Specification-Based Dependency Resolution
```python
def _propagate_messages(self) -> None:
    """
    Initialize step connections using the dependency resolver.
    
    This method analyzes the DAG structure and uses the dependency resolver
    to intelligently match inputs to outputs based on specifications.
    """
```

#### Output Generation
```python
def _generate_outputs(self, step_name: str) -> Dict[str, Any]:
    """
    Generate outputs dictionary using step builder's specification.
    """
```

#### Step Instantiation
```python
def _instantiate_step(self, step_name: str) -> Step:
    """
    Instantiate a pipeline step with appropriate inputs from dependencies.
    """
```

#### Pipeline Generation
```python
def generate_pipeline(self, pipeline_name: str) -> Pipeline:
    """
    Build and return a SageMaker Pipeline object.
    """
```

#### Factory Method
```python
@classmethod
def create_with_components(cls, 
                         dag: PipelineDAG,
                         config_map: Dict[str, BasePipelineConfig],
                         step_builder_map: Dict[str, Type[StepBuilderBase]],
                         context_name: Optional[str] = None,
                         **kwargs) -> "PipelineAssembler":
    """
    Create pipeline assembler with managed components.
    """
```

## Specification-Driven Dependency Resolution

The Pipeline Builder Template now uses specification-driven dependency resolution to automatically connect steps:

### Key Components

>[!important]
> 1. **Registry Manager**: Manages multiple isolated specification registries
> 2. **Dependency Resolver**: Resolves dependencies between steps using specifications
> 3. **Semantic Matcher**: Calculates similarity between dependency names and output names
> 4. **Property Reference**: Bridges definition-time and runtime property references

- [[Dependency Resolver for Automatic Pipeline]]
- [[Registry Manager for Automatic Pipeline]]
- [[Semantic Matcher for Dependency Resolution of Auto-Pipeline]]
- [[Property Reference Class as Bridge between Definition-time and Runtime]]

### How Dependency Resolution Works

>[!important]
> 1. **Step Specification Registration**: Each step builder registers its specification with the registry
> 2. **Dependency Analysis**: The dependency resolver analyzes the specifications of all steps
> 3. **Compatibility Scoring**: The resolver calculates compatibility scores between dependencies and outputs
> 4. **Property Reference Creation**: The resolver creates property references for each resolved dependency
> 5. **Runtime Property Resolution**: Property references are converted to SageMaker property references at runtime

- [[Dependency Resolver for Automatic Pipeline]]
- [[Property Reference Class as Bridge between Definition-time and Runtime]]

### Advantages of Specification-Driven Dependency Resolution

>[!important]
> 1. **Declarative Dependency Definition**: Dependencies are defined declaratively in specifications
> 2. **Semantic Matching**: Dependencies can be matched based on semantic similarity, not just exact names
> 3. **Type Compatibility**: Dependencies can be matched based on type compatibility
> 4. **Intelligent Matching**: Multiple factors are considered when matching dependencies
> 5. **Contextual Isolation**: Multiple pipelines can have isolated dependency resolution contexts

- [[Comparison of Design Philosophy Developer Perspective]]
- [[Comparison of Design Philosophy Lean Product Perspective]]
- [[Step Specification Design as Declarative Pipeline Architecture]]

## Context Management and Thread Safety

The Pipeline Builder Template now supports context management and thread safety:

### Context Management

```python
# Build a pipeline with scoped context
pipeline = MyPipelineTemplate.build_with_context(config_path)

# Or use the context manager directly
with dependency_resolution_context() as components:
    template = MyPipelineTemplate(
        config_path=config_path,
        registry_manager=components["registry_manager"],
        dependency_resolver=components["resolver"],
    )
    pipeline = template.generate_pipeline()
```

### Thread Safety

```python
# Build a pipeline in a thread-safe manner
pipeline = MyPipelineTemplate.build_in_thread(config_path)

# Or get thread-local components directly
components = get_thread_components()
template = MyPipelineTemplate(
    config_path=config_path,
    registry_manager=components["registry_manager"],
    dependency_resolver=components["resolver"],
)
```

## Creating a Custom Pipeline Template

To create a custom pipeline template, you should extend the `PipelineTemplateBase` class:

```python
class MyPipelineTemplate(PipelineTemplateBase):
    # Define the configuration classes expected in the config file
    CONFIG_CLASSES = {
        'Base': BasePipelineConfig,
        'DataLoading': DataLoadingConfig,
        'Preprocessing': PreprocessingConfig,
        'Training': TrainingConfig,
    }
    
    def _validate_configuration(self) -> None:
        # Validate configuration structure
        if 'DataLoading' not in self.configs:
            raise ValueError("DataLoading configuration is required")
        
        if 'Training' not in self.configs:
            raise ValueError("Training configuration is required")
    
    def _create_pipeline_dag(self) -> PipelineDAG:
        # Create the DAG structure
        dag = PipelineDAG()
        
        # Add nodes
        dag.add_node("data_loading")
        dag.add_node("preprocessing")
        dag.add_node("training")
        
        # Add edges
        dag.add_edge("data_loading", "preprocessing")
        dag.add_edge("preprocessing", "training")
        
        return dag
    
    def _create_config_map(self) -> Dict[str, BasePipelineConfig]:
        # Map step names to configuration instances
        return {
            "data_loading": self.configs['DataLoading'],
            "preprocessing": self.configs['Preprocessing'],
            "training": self.configs['Training'],
        }
    
    def _create_step_builder_map(self) -> Dict[str, Type[StepBuilderBase]]:
        # Map step types to builder classes
        return {
            "DataLoadingStep": DataLoadingStepBuilder,
            "PreprocessingStep": PreprocessingStepBuilder,
            "TrainingStep": TrainingStepBuilder,
        }
```

## Usage Example

### Using a Pipeline Template

```python
# Create the template
template = MyPipelineTemplate(
    config_path="config.json",
    sagemaker_session=sagemaker_session,
    role=role,
)

# Generate the pipeline
pipeline = template.generate_pipeline()
```

### Using Factory Methods

```python
# Create with managed components
template = MyPipelineTemplate.create_with_components(
    config_path="config.json",
    context_name="my_pipeline",
    sagemaker_session=sagemaker_session,
    role=role,
)

# Build with context
pipeline = MyPipelineTemplate.build_with_context(
    config_path="config.json",
    sagemaker_session=sagemaker_session,
    role=role,
)

# Build in thread
pipeline = MyPipelineTemplate.build_in_thread(
    config_path="config.json",
    sagemaker_session=sagemaker_session,
    role=role,
)
```

- [[Design Pattern Factory Method Pattern]]

## Advanced Features

### Execution Document Support

```python
def fill_execution_document(self, execution_document: Dict[str, Any]) -> Dict[str, Any]:
    """Fill in the execution document with pipeline metadata."""
```

This method can be overridden by template subclasses to fill execution documents with step-specific metadata from the pipeline.

- [[Execution Document Helper from MODS Workflow Helper]]
- [[MODS Execution Document]]

### Cradle Data Loading Integration

The `PipelineAssembler` automatically captures Cradle data loading requests from steps and stores them for later use:

```python
# Inside PipelineAssembler._instantiate_step:
if step_type == "CradleDataLoading" and hasattr(builder, "get_request_dict"):
    self.cradle_loading_requests[step.name] = builder.get_request_dict()
```

This allows templates to include these requests in execution documents or other metadata.



-----------
##  Recommended Notes

- [[Pipeline DAG for Automatic Pipeline]]
- [[Step Specification Design as Declarative Pipeline Architecture]]
- [[Comparison of Design Philosophy Developer Perspective]]
- [[Comparison of Design Philosophy Lean Product Perspective]]
- [[Comparison of Design Philosophy User Perspective]]