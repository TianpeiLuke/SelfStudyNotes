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
>The **Specification Registry** provides *context-aware storage* and *retrieval* of step specifications with complete isolation between contexts. 
>- It serves as the *central repository* for pipeline step specifications, enabling *efficient lookup*, *compatibility checking*, and *dependency resolution*.

- [[Base Step Specification]]

>[!important]
>The specification registry is a __context-aware dependency management system__ that enables declarative, intelligent pipeline construction. It consists of several interconnected components:

- [[Dependency Resolver for Automatic Pipeline]]
- [[Registry Manager for Automatic Pipeline]]

## Code

### SpecificationRegistry
Main registry class that manages step specifications within a context.

```python
class SpecificationRegistry:
    def __init__(self, context_name: str = "default"):
        """
        Initialize a context-scoped registry.
        
        Args:
            context_name: Name of the context this registry belongs to (e.g., pipeline name)
        """
        
    def register(self, step_name: str, specification: StepSpecification):
        """
        Register a step specification.
        
        Args:
            step_name: Logical name for the step
            specification: StepSpecification instance to register
            
        Raises:
            ValueError: If specification is invalid or not a StepSpecification
        """
        
    def get_specification(self, step_name: str) -> Optional[StepSpecification]:
        """
        Get specification by step name.
        
        Args:
            step_name: Name of the step to retrieve
            
        Returns:
            StepSpecification if found, None otherwise
        """
        
    def get_specifications_by_type(self, step_type: str) -> List[StepSpecification]:
        """
        Get all specifications of a given step type.
        
        Args:
            step_type: Type of steps to retrieve
            
        Returns:
            List of specifications matching the step type
        """
        
    def list_step_names(self) -> List[str]:
        """
        Get list of all registered step names.
        
        Returns:
            List of step names in the registry
        """
        
    def list_step_types(self) -> List[str]:
        """
        Get list of all registered step types.
        
        Returns:
            List of unique step types in the registry
        """
        
    def find_compatible_outputs(self, dependency_spec: DependencySpec) -> List[tuple]:
        """
        Find outputs compatible with a dependency specification.
        
        Args:
            dependency_spec: Dependency specification to match against
            
        Returns:
            List of (step_name, output_name, output_spec, score) tuples sorted by score
        """
``````

## Core Functionality

### Key Features

>[!important]
> - **Context-Scoped Storage**: Each registry instance is tied to a specific context (e.g., pipeline name)
> - **Specification Management**: Registration, retrieval, and validation of step specifications
> - **Type-Based Organization**: Efficient lookup by step type for similar components
> - **Compatibility Checking**: Find outputs that match dependency requirements
> - **Context Isolation**: No cross-contamination between different contexts

## Usage Examples

### Basic Registry Operations

```python
from src.pipeline_deps.specification_registry import SpecificationRegistry
from src.pipeline_deps.base_specifications import StepSpecification, NodeType

# Create context-specific registry
registry = SpecificationRegistry("training_pipeline")

# Create and register a specification
data_loading_spec = StepSpecification(
    step_type="DataLoadingStep",
    node_type=NodeType.SOURCE,
    outputs={
        "processed_data": output_spec
    },
    dependencies={}
)

# Register the specification
registry.register("data_loading", data_loading_spec)

# Retrieve specification
spec = registry.get_specification("data_loading")
print(f"Retrieved specification: {spec.step_type}")

# List all registered steps
step_names = registry.list_step_names()
print(f"Registered steps: {step_names}")
```

### Working with Step Types

```python
# Register multiple specifications of the same type
registry.register("training_data_loading", training_data_spec)
registry.register("validation_data_loading", validation_data_spec)
registry.register("test_data_loading", test_data_spec)

# Get all data loading specifications
data_loading_specs = registry.get_specifications_by_type("DataLoadingStep")
print(f"Found {len(data_loading_specs)} data loading specifications")

# List all unique step types
step_types = registry.list_step_types()
print(f"Available step types: {step_types}")
```

### Finding Compatible Outputs

```python
from src.pipeline_deps.base_specifications import DependencySpec, DependencyType

# Define a dependency requirement
training_data_dep = DependencySpec(
    logical_name="training_data",
    dependency_type=DependencyType.PROCESSING_OUTPUT,
    required=True,
    compatible_sources=["DataLoadingStep", "PreprocessingStep"],
    semantic_keywords=["data", "training"],
    data_type="S3Uri"
)

# Find compatible outputs for this dependency
compatible_outputs = registry.find_compatible_outputs(training_data_dep)
for step_name, output_name, output_spec, score in compatible_outputs:
    print(f"{step_name}.{output_name}: {score:.3f}")

# Example output:
# data_loading.processed_data: 0.800
# preprocessing.training_output: 0.750
```

## Compatibility Scoring

>[!important]
>The registry uses a **multi-factor scoring algorithm** to evaluate *compatibility* between *dependencies* and *outputs*:

### Basic Compatibility Check
```python
def _are_compatible(self, dep_spec: DependencySpec, out_spec: OutputSpec) -> bool:
    """Check basic compatibility between dependency and output."""
    # Type compatibility
    if dep_spec.dependency_type != out_spec.output_type:
        return False
    
    # Data type compatibility
    if dep_spec.data_type != out_spec.data_type:
        return False
    
    return True
```

### Scoring Algorithm
```python
def _calculate_compatibility_score(self, dep_spec: DependencySpec, 
                                out_spec: OutputSpec, step_type: str) -> float:
    """Calculate compatibility score between dependency and output."""
    score = 0.5  # Base compatibility score
    
    # Compatible source bonus
    if dep_spec.compatible_sources and step_type in dep_spec.compatible_sources:
        score += 0.3
    
    # Semantic keyword matching
    if dep_spec.semantic_keywords:
        keyword_matches = sum(
            1 for keyword in dep_spec.semantic_keywords
            if keyword.lower() in out_spec.logical_name.lower()
        )
        score += (keyword_matches / len(dep_spec.semantic_keywords)) * 0.2
    
    return min(score, 1.0)  # Cap at 1.0
```

### Scoring Factors
1. **Basic Compatibility (0.5)**: Types and data types match exactly
2. **Source Type Compatibility (0.3)**: Step type is in the compatible sources list
3. **Semantic Keyword Matching (0.2)**: Keywords from dependency spec appear in output name

## Integration with Registry Manager

The SpecificationRegistry is typically managed by a RegistryManager for context isolation:

```python
from src.pipeline_deps.registry_manager import RegistryManager

# Create registry manager
manager = RegistryManager()

# Get context-specific registry
training_registry = manager.get_registry("training_pipeline")
validation_registry = manager.get_registry("validation_pipeline")

# Each registry maintains its own isolated specifications
training_registry.register("data_loading", training_data_spec)
validation_registry.register("data_loading", validation_data_spec)

# No cross-contamination between contexts
assert training_registry.get_specification("data_loading") != validation_registry.get_specification("data_loading")
```

## Integration with Dependency Resolver

The registry provides specifications and compatibility information to the dependency resolver:

```python
from src.pipeline_deps.dependency_resolver import UnifiedDependencyResolver
from src.pipeline_deps.semantic_matcher import SemanticMatcher

# Create components
registry = SpecificationRegistry("my_pipeline")
semantic_matcher = SemanticMatcher()
resolver = UnifiedDependencyResolver(registry, semantic_matcher)

# Register specifications
registry.register("data_load", data_load_spec)
registry.register("preprocess", preprocess_spec)
registry.register("train", train_spec)

# Resolver uses registry to access specifications
dependencies = resolver.resolve_step_dependencies("train", ["data_load", "preprocess", "train"])
```
## Best Practices

### 1. Context Naming

>[!important]
> - Use consistent, descriptive names for registry contexts
> - Include environment, pipeline type, or purpose in context names
> - Document the scope and purpose of each context

### 2. Specification Management

>[!important]
> - Register specifications early in the pipeline lifecycle
> - Validate specifications thoroughly before registration
> - Keep specifications up-to-date with code changes

### 3. Step Naming

>[!important]
> - Use consistent naming patterns for steps within a context
> - Choose descriptive names that reflect step functionality
> - Include purpose or data type in step names for clarity

### 4. Error Handling

>[!important]
> - Always check if specifications exist before using them
> - Handle missing specifications gracefully
> - Provide clear error messages for invalid specifications


-----------
##  Recommended Notes

- [[Specification Registry Design]]
- [[Registry Manager for Automatic Pipeline]]
- [[Step Specification Design as Declarative Pipeline Architecture]]
- [[Registry Manager Design]]

- [[Spec Registry as Brain of Dependency Resolution]]
- [[Comparison between Registry Manager and Spec Registry]]