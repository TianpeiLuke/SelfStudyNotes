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
>The **`PipelineAssembler`** is responsible for *assembling pipeline steps* using 
>- a *DAG structure* and 
>- *specification-based dependency resolution*. 
>  
>It connects steps based on their specifications, instantiates them in topological order, and combines them into a SageMaker pipeline.


## Code

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

- [[Dependency Resolver for Automatic Pipeline]]
- [[Registry Manager for Automatic Pipeline]]
- [[Pipeline DAG for Automatic Pipeline]]
- [[Base Config]]
- [[Base Step Builder]]

## Pipeline Assembly Process

>[!important]
> The **pipeline assembly process** follows these steps:
> 
> 1. **Initialize step builders** for all steps in the DAG
> 2. **Propagate messages** between steps using specification-based dependency resolution
> 3. **Generate output paths** for each step
> 4. **Instantiate steps** in **topological order**, connecting inputs to outputs
> 5. **Create the SageMaker pipeline** with the instantiated steps


## Key Methods

### Step Builder Initialization

```python
def _initialize_step_builders(self) -> None:
    """
    Initialize step builders for all steps in the DAG.
    
    This method creates a step builder instance for each step in the DAG,
    using the corresponding config from config_map and the appropriate
    builder class from step_builder_map.
    """
```

>[!important]
> This method initializes step builders for all steps in the DAG, setting up the necessary components for each step:
> 
> 1. **Gets the configuration** for the step
> 2. **Determines the step type** based on the configuration class name
> 3. **Gets the appropriate builder class** from the step_builder_map
> 4. **Creates an instance of the builder** with the configuration and dependency components

### Specification-Based Message Propagation

```python
def _propagate_messages(self) -> None:
    """
    Initialize step connections using the dependency resolver.
    
    This method analyzes the DAG structure and uses the dependency resolver
    to intelligently match inputs to outputs based on specifications.
    """
```

>[!important]
> This method implements the **core** of the *specification-driven dependency resolution*:
> 
> 1. For each *edge* in the DAG, it gets the **source** and **destination step builders**
> 2. For each *dependency* in the **destination step**, it checks if the **source step** can provide it
> 3. It **calculates compatibility scores** between dependencies and outputs
> 4. It **selects the best match** for *each dependency* based on compatibility score
> 5. It stores the **matches** in the **`step_messages` dictionary** for later use


### Output Generation

```python
def _generate_outputs(self, step_name: str) -> Dict[str, Any]:
    """
    Generate outputs dictionary using step builder's specification.
    
    This implementation leverages the step builder's specification
    to generate appropriate outputs.
    
    Args:
        step_name: Name of the step to generate outputs for
        
    Returns:
        Dictionary with output paths based on specification
    """
```

>[!important]
> This method **generates output paths** for a step based on its specification:
> 
> 1. Gets the step builder and configuration
> 2. Retrieves the *base S3 location* from the configuration
> 3. **Generates output paths** for each output in the step's **specification**
> 4. Returns a *dictionary mapping output names* to S3 paths

### Step Instantiation

```python
def _instantiate_step(self, step_name: str) -> Step:
    """
    Instantiate a pipeline step with appropriate inputs from dependencies.
    
    This method creates a step using the step builder's create_step method,
    delegating input extraction and output generation to the builder.
    
    Args:
        step_name: Name of the step to instantiate
        
    Returns:
        Instantiated SageMaker Pipeline Step
    """
```

>[!important]
> This method **creates a SageMaker pipeline step** with the appropriate inputs:
> 
> 1. Gets the step builder for the step
> 2. Retrieves *dependencies* from the **DAG**
> 3. Extracts inputs from the **`step_messages`** dictionary
> 4. Creates **`PropertyReference`** objects for **runtime property references**
> 5. Generates outputs using the **`_generate_outputs`** method
> 6. Creates the step using the builder's **`create_step`** method
> 7. Stores special metadata for certain step types (e.g., Cradle data loading requests)

### Pipeline Generation

```python
def generate_pipeline(self, pipeline_name: str) -> Pipeline:
    """
    Build and return a SageMaker Pipeline object.
    
    This method builds the pipeline by:
    1. Propagating messages between steps using specification-based matching
    2. Instantiating steps in topological order
    3. Creating the pipeline with the instantiated steps
    
    Args:
        pipeline_name: Name of the pipeline
        
    Returns:
        SageMaker Pipeline object
    """
```

>[!important]
> This method orchestrates the **pipeline generation process**:
> 
> 1. **Propagates messages** between steps using **`_propagate_messages`**
> 2. Determines build order using **topological sort**
> 3. **Instantiates steps** in *topological order*
> 4. Creates a SageMaker pipeline with the instantiated steps

- [[Topological Sorting]]

### Factory Method

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
    
    This factory method creates a pipeline assembler with properly configured
    dependency components from the factory module.
    
    Args:
        dag: PipelineDAG instance defining the pipeline structure
        config_map: Mapping from step name to config instance
        step_builder_map: Mapping from step type to StepBuilderBase subclass
        context_name: Optional context name for registry
        **kwargs: Additional arguments to pass to the constructor
        
    Returns:
        Configured PipelineAssembler instance
    """
```

>[!info]
>This factory method creates a pipeline assembler with properly configured dependency components using the factory module.

- [[Design Pattern Factory Method Pattern]]

## Property Reference Resolution

>[!important]
>The `PipelineAssembler` uses `PropertyReference` objects to *bridge* **definition-time** and **runtime property references**:

```python
# In _instantiate_step:
prop_ref = PropertyReference(
    step_name=src_step,
    output_spec=output_spec
)

# Use the enhanced to_runtime_property method to get a SageMaker Properties object
runtime_prop = prop_ref.to_runtime_property(self.step_instances)
inputs[input_name] = runtime_prop
```

>[!info]
>This approach allows for robust handling of SageMaker property references, with fallbacks for error cases.

- [[Property Reference Class as Bridge between Definition-time and Runtime]]

## Input Validation

>[!important]
> The `PipelineAssembler` performs **extensive input validation** during initialization:
> 
> 1. Checks that all **nodes** in the DAG have a corresponding config
> 2. Checks that all **configs** have a corresponding step builder
> 3. Checks that all **edges** in the DAG connect nodes that exist in the DAG
> 
> This ensures that the pipeline definition is consistent and valid before proceeding with assembly.

- [[Pipeline DAG Validation]]

## Usage Examples

### Direct Instantiation

```python
from src.pipeline_builder.pipeline_assembler import PipelineAssembler
from src.pipeline_dag.base_dag import PipelineDAG

# Create DAG
dag = PipelineDAG()
dag.add_node("data_loading")
dag.add_node("preprocessing")
dag.add_edge("data_loading", "preprocessing")

# Create config map
config_map = {
    "data_loading": data_loading_config,
    "preprocessing": preprocessing_config,
}

# Create step builder map
step_builder_map = {
    "CradleDataLoading": CradleDataLoadingStepBuilder,
    "TabularPreprocessingStep": TabularPreprocessingStepBuilder,
}

# Create the assembler
assembler = PipelineAssembler(
    dag=dag,
    config_map=config_map,
    step_builder_map=step_builder_map,
    sagemaker_session=sagemaker_session,
    role=execution_role,
)

# Generate the pipeline
pipeline = assembler.generate_pipeline("my-pipeline")
```

- [[Pipeline DAG for Automatic Pipeline]]

### Using Factory Method

```python
from src.pipeline_builder.pipeline_assembler import PipelineAssembler

# Create the assembler with managed components
assembler = PipelineAssembler.create_with_components(
    dag=dag,
    config_map=config_map,
    step_builder_map=step_builder_map,
    context_name="my_pipeline",
    sagemaker_session=sagemaker_session,
    role=execution_role,
)

# Generate the pipeline
pipeline = assembler.generate_pipeline("my-pipeline")
```

- [[Design Pattern Factory Method Pattern]]

### Integration with PipelineTemplateBase

```python
from src.pipeline_builder.pipeline_template_base import PipelineTemplateBase

class MyPipelineTemplate(PipelineTemplateBase):
    # ...implementation...
    
    def generate_pipeline(self) -> Pipeline:
        # Create the DAG, config_map, and step builder map
        dag = self._create_pipeline_dag()
        config_map = self._create_config_map()
        step_builder_map = self._create_step_builder_map()
        
        # Create the assembler
        assembler = PipelineAssembler(
            dag=dag,
            config_map=config_map,
            step_builder_map=step_builder_map,
            sagemaker_session=self.session,
            role=self.role,
            notebook_root=self.notebook_root,
            registry_manager=self._registry_manager,
            dependency_resolver=self._dependency_resolver
        )
        
        # Generate the pipeline
        pipeline = assembler.generate_pipeline(self._get_pipeline_name())
        
        return pipeline
```

- [[Base Pipeline Template for Automatic Pipeline]]

## Advantages of the Assembler-Based Approach

>[!important]
> 1. **Clear Separation of Concerns**: The assembler is responsible only for pipeline assembly, while the template handles configuration loading and DAG definition.
> 2. **Reusable Components**: The assembler can be used independently of the template for more complex pipeline generation scenarios.
> 3. **Specification-Driven Connections**: Step connections are determined automatically based on specifications, reducing the risk of errors.
> 4. **Modular Design**: The assembler can be extended or modified without changing the template base class.
> 5. **Consistent Pipeline Structure**: The assembly process ensures that all pipelines follow the same structure and conventions.

- [[Specification-Driven Design Architecture for Pipeline Automation]]

-----------
##  Recommended Notes

- [[Base Pipeline Template for Automatic Pipeline]]


- [[Pipeline DAG and Declarative Spec and Reference Property for Step Builder]]
- [[Pipeline DAG Design]]