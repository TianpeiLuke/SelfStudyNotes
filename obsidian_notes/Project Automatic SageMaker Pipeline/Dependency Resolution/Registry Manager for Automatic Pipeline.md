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
>The **Registry Manager** provides centralized management of multiple isolated *specification registries*, ensuring complete *isolation* between different contexts (pipelines, environments, etc.). 
>- Each **context** gets its own dedicated **SpecificationRegistry** instance, preventing *cross-contamination* of specifications between different pipelines or environments.

- [[Base Step Specification]]
- [[Specification Registry for Automatic Pipeline]]

## Code

### RegistryManager

>[!important]
>Main manager class that coordinates multiple registry instances.

```python
class RegistryManager:
    def __init__(self):
        """Initialize the registry manager."""
        
    def get_registry(self, context_name: str = "default", 
                    create_if_missing: bool = True) -> Optional[SpecificationRegistry]:
        """
        Get the registry for a specific context.
        
        Args:
            context_name: Name of the context (e.g., pipeline name, environment)
            create_if_missing: Whether to create a new registry if one doesn't exist
            
        Returns:
            Context-specific registry or None if not found and create_if_missing is False
        """
        
    def list_contexts(self) -> List[str]:
        """
        Get list of all registered context names.
        
        Returns:
            List of context names with registries
        """
        
    def clear_context(self, context_name: str) -> bool:
        """
        Clear the registry for a specific context.
        
        Args:
            context_name: Name of the context to clear
            
        Returns:
            True if the registry was cleared, False if it didn't exist
        """
        
    def clear_all_contexts(self):
        """Clear all registries."""
        
    def get_context_stats(self) -> Dict[str, Dict[str, int]]:
        """
        Get statistics for all contexts.
        
        Returns:
            Dictionary mapping context names to their statistics
        """
```

### Helper Functions

Convenience functions for common operations:

```python
def get_registry(manager: RegistryManager, context_name: str = "default") -> SpecificationRegistry:
    """Get the registry for a specific context."""
    
def list_contexts(manager: RegistryManager) -> List[str]:
    """Get list of all registered context names."""
    
def clear_context(manager: RegistryManager, context_name: str) -> bool:
    """Clear the registry for a specific context."""
    
def get_context_stats(manager: RegistryManager) -> Dict[str, Dict[str, int]]:
    """Get statistics for all contexts."""
```

## Core Functionality

### Key Features

>[!important]
> - **Context-Specific Registries**: Maintains separate registry instances for different contexts
> - **Complete Isolation**: Ensures specifications from one context don't affect others
> - **Dynamic Creation**: Creates registries on-demand for new contexts
> - **Context Statistics**: Provides usage statistics for each context
> - **Cleanup Management**: Supports individual or bulk context cleanup

## Usage Examples

### Basic Registry Management
```python
from src.pipeline_deps.registry_manager import RegistryManager

# Create registry manager
manager = RegistryManager()

# Get registry for specific context
training_registry = manager.get_registry("training_pipeline")
validation_registry = manager.get_registry("validation_pipeline")

# Register specifications in different contexts
training_registry.register("data_loading", training_data_spec)
validation_registry.register("data_loading", validation_data_spec)

# List all contexts
contexts = manager.list_contexts()
print(f"Active contexts: {contexts}")
# Output: ['training_pipeline', 'validation_pipeline']

# Get statistics about contexts
stats = manager.get_context_stats()
for context, context_stats in stats.items():
    print(f"Context '{context}': {context_stats['step_count']} steps")
```

### Using Helper Functions

```python
from src.pipeline_deps.registry_manager import (
    RegistryManager, get_registry, list_contexts, clear_context, get_context_stats
)

# Create registry manager
manager = RegistryManager()

# Get registry using helper function
registry = get_registry(manager, "my_pipeline")

# Register specifications
registry.register("preprocessing", preprocess_spec)
registry.register("training", training_spec)

# List all contexts
all_contexts = list_contexts(manager)
print(f"All contexts: {all_contexts}")

# Clear specific context
success = clear_context(manager, "old_pipeline")
if success:
    print("Context cleared successfully")

# Get context statistics
stats = get_context_stats(manager)
print(f"Context statistics: {stats}")
```

### Context Cleanup

```python
from src.pipeline_deps.registry_manager import RegistryManager

# Create registry manager
manager = RegistryManager()

# Create some registries
registry1 = manager.get_registry("context1")
registry2 = manager.get_registry("context2")

# Clear specific context
success = manager.clear_context("context1")
print(f"Context1 cleared: {success}")

# Clear all contexts
manager.clear_all_contexts()
print("All contexts cleared")
```

## Integration with Pipeline Builder

>[!important]
>The registry manager provides a *decorator* for **automatic integration** with pipeline builders:

```python
from src.pipeline_deps.registry_manager import integrate_with_pipeline_builder, RegistryManager

# Create a registry manager
manager = RegistryManager()

@integrate_with_pipeline_builder(manager)
class MyPipelineBuilder:
    def __init__(self, base_config):
        self.base_config = base_config
        # self.registry is automatically created based on pipeline_name
        
    def build_pipeline(self):
        # Use self.registry for context-specific specifications
        data_spec = self.registry.get_specification("data_loading")
        return self._build_with_spec(data_spec)

# Usage with configuration
class PipelineConfig:
    def __init__(self, pipeline_name: str):
        self.pipeline_name = pipeline_name

config = PipelineConfig("production_training")
builder = MyPipelineBuilder(config)
# builder.registry is automatically scoped to "production_training"
```

## Context Patterns

### Environment-Based Contexts

```python
# Create registry manager
manager = RegistryManager()

# Different registries for different environments
dev_registry = manager.get_registry("development")
staging_registry = manager.get_registry("staging")
prod_registry = manager.get_registry("production")

# Each environment can have different specifications
dev_registry.register("data_loading", dev_data_spec)
prod_registry.register("data_loading", prod_data_spec)
```

### Pipeline-Based Contexts

```python
# Create registry manager
manager = RegistryManager()

# Different registries for different pipeline types
training_registry = manager.get_registry("training_pipeline")
inference_registry = manager.get_registry("inference_pipeline")
batch_registry = manager.get_registry("batch_processing")

# Each pipeline type has its own specifications
training_registry.register("model_training", training_spec)
inference_registry.register("model_inference", inference_spec)
```

### Multi-Tenant Contexts

```python
# Create registry manager
manager = RegistryManager()

# Different registries for different tenants/customers
customer_a_registry = manager.get_registry("customer_a")
customer_b_registry = manager.get_registry("customer_b")

# Each customer can have customized specifications
customer_a_registry.register("preprocessing", custom_preprocess_a)
customer_b_registry.register("preprocessing", custom_preprocess_b)
```

## Backward Compatibility

### Legacy Functions
The module provides backward compatibility functions for existing code:

```python
from src.pipeline_deps.registry_manager import (
    get_pipeline_registry,
    get_default_registry
)

# Create registry manager
manager = RegistryManager()

# Legacy pipeline registry access
pipeline_registry = get_pipeline_registry(manager, "my_pipeline")

# Legacy default registry access
default_registry = get_default_registry(manager)
```

## Integration with Dependency Resolver

```python
from src.pipeline_deps.registry_manager import RegistryManager
from src.pipeline_deps.dependency_resolver import UnifiedDependencyResolver
from src.pipeline_deps.semantic_matcher import SemanticMatcher

# Create components
manager = RegistryManager()
registry = manager.get_registry("my_pipeline")
semantic_matcher = SemanticMatcher()

# Create dependency resolver with registry
resolver = UnifiedDependencyResolver(registry, semantic_matcher)

# Register specifications
registry.register("data_load", data_loading_spec)
registry.register("preprocess", preprocessing_spec)
registry.register("train", training_spec)

# Resolve dependencies
dependencies = resolver.resolve_all_dependencies(["data_load", "preprocess", "train"])
```

## Best Practices

### 1. Context Naming

>[!important]
> - Use descriptive context names: `training_pipeline`, `production_env`
> - Follow consistent naming conventions across your organization
> - Consider including environment and pipeline type in context names

### 2. Context Lifecycle

>[!important]
> - Create contexts when needed, don't pre-create all possible contexts
> - Clean up contexts when pipelines are decommissioned
> - Monitor context statistics to identify unused contexts

### 3. Registry Isolation

>[!important]
> - Keep contexts completely isolated - don't share specifications across contexts
> - Use context-specific specifications even if they're similar
> - Document the purpose and scope of each context

### 4. Integration Patterns

>[!important]
> - Use the decorator pattern for automatic pipeline builder integration
> - Leverage context detection from configuration objects
> - Implement consistent context naming across your pipeline ecosystem

## Error Handling

### Context Not Found
```python
# Create registry manager
manager = RegistryManager()

# Handle missing context
registry = manager.get_registry("nonexistent_context", create_if_missing=False)
if registry is None:
    print("Context not found")
    # Create context or use default
    registry = manager.get_registry("default")
else:
    # Use registry
    pass
```

### Registry Cleanup Errors
```python
# Create registry manager
manager = RegistryManager()

# Handle cleanup failures
success = manager.clear_context("context_to_clear")
if not success:
    print("Context was already cleared or didn't exist")
    # Proceed with alternative logic
```

## Performance Considerations

### Memory Management

>[!important]
> - Each context maintains its own separate registry in memory
> - Clear unused contexts to free memory
> - Registry manager has minimal overhead compared to individual registries

### Concurrent Access

>[!important]
> - Registry manager operations are thread-safe for basic access patterns
> - Each context is isolated, preventing cross-contamination
> - Consider using dedicated registry managers for high-concurrency scenarios

### Scalability

>[!important]
> - The registry manager scales to hundreds of contexts
> - Context creation is a lightweight operation
> - Statistics collection is optimized for frequent access


-----------
##  Recommended Notes


- [[Step Specification Design as Declarative Pipeline Architecture]]
- [[Registry Manager Design]]

- [[Comparison between Registry Manager and Spec Registry]]