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
>The **Dependency Resolver** is a key component of the specification-driven pipeline building system. 
>- It *automatically resolves dependencies* between pipeline steps based on their *declared input and output specifications*, eliminating the need for manual wiring of step connections.

![[step_pipeline.png]]

## Code

```python
class UnifiedDependencyResolver:
    """Intelligent dependency resolver using declarative specifications."""
    
    def __init__(self, registry: SpecificationRegistry, semantic_matcher: SemanticMatcher):
        """Initialize the dependency resolver."""
```

- [[Semantic Matcher for Dependency Resolution of Auto-Pipeline]]
- [[Specification Registry for Automatic Pipeline]]

## Key Design Choices

### 1. Specification-Driven Architecture

>[!important]
> The dependency resolver takes a **fundamentally declarative approach**, where steps define their input requirements (dependencies) and output capabilities (outputs) using formal specifications. This design choice enables:
> 
> - **Loose Coupling**: Steps *don't need direct knowledge* of their upstream or downstream components
> - **Automated Wiring**: Connections between steps can be determined *automatically*
> - **Self-Documenting**: Specifications serve as both *configuration* and *documentation*
> - **Validation**: Requirements can be *validated before pipeline execution*

- [[Base Step Specification]]


### 2. Multi-Factor Compatibility Scoring

>[!important]
> Rather than using simple name matching, the resolver uses a sophisticated multi-factor scoring system that considers:
> 
> - **Dependency Type Compatibility (40% weight)**: Ensures the type of output matches the dependency
> - **Data Type Compatibility (20% weight)**: Ensures the data formats are compatible
> - **Semantic Name Matching (25% weight)**: Uses semantic matching to find similar names
> - **Compatible Source Check (10% weight)**: Considers explicitly declared compatible sources
> - **Keyword Matching (5% weight)**: Checks for semantic keywords in names

- [[Semantic Matcher for Dependency Resolution of Auto-Pipeline]]

>[!info]
>This weighted approach allows for robust matching even when names aren't identical:

```python
def _calculate_compatibility(self, dep_spec: DependencySpec, output_spec: OutputSpec,
                           provider_spec: StepSpecification) -> float:
    """
    Calculate compatibility score between dependency and output.
    
    Args:
        dep_spec: Dependency specification
        output_spec: Output specification
        provider_spec: Provider step specification
        
    Returns:
        Compatibility score between 0.0 and 1.0
    """
    score = 0.0
    
    # 1. Dependency type compatibility (40% weight)
    if dep_spec.dependency_type == output_spec.output_type:
        score += 0.4
    elif self._are_types_compatible(dep_spec.dependency_type, output_spec.output_type):
        score += 0.2
    else:
        # If types are not compatible at all, return 0
        return 0.0
    
    # 2. Data type compatibility (20% weight)
    if dep_spec.data_type == output_spec.data_type:
        score += 0.2
    elif self._are_data_types_compatible(dep_spec.data_type, output_spec.data_type):
        score += 0.1
    
    # 3. Enhanced semantic name matching with alias support (25% weight)
    semantic_score = self.semantic_matcher.calculate_similarity_with_aliases(
        dep_spec.logical_name, output_spec
    )
    score += semantic_score * 0.25
    
    # Optional: Add direct match bonus for exact matches
    if dep_spec.logical_name == output_spec.logical_name:
        score += 0.05  # Exact logical name match bonus
    elif dep_spec.logical_name in output_spec.aliases:
        score += 0.05  # Exact alias match bonus
    
    # 4. Compatible source check (10% weight)
    if dep_spec.compatible_sources:
        if provider_spec.step_type in dep_spec.compatible_sources:
            score += 0.1
    else:
        # If no compatible sources specified, give small bonus for any match
        score += 0.05
    
    # 5. Keyword matching bonus (5% weight)
    if dep_spec.semantic_keywords:
        keyword_score = self._calculate_keyword_match(dep_spec.semantic_keywords, output_spec.logical_name)
        score += keyword_score * 0.05
    
    return min(score, 1.0)  # Cap at 1.0
```

### 3. Type Compatibility Matrices

>[!important]
>The resolver includes **explicit compatibility matrices** for both **dependency types** and **data types**:

```python
def _are_types_compatible(self, dep_type: DependencyType, output_type: DependencyType) -> bool:
    """Check if dependency and output types are compatible."""
    # Define compatibility matrix
    compatibility_matrix = {
        DependencyType.MODEL_ARTIFACTS: [DependencyType.MODEL_ARTIFACTS],
        DependencyType.TRAINING_DATA: [DependencyType.PROCESSING_OUTPUT, DependencyType.TRAINING_DATA],
        DependencyType.PROCESSING_OUTPUT: [DependencyType.PROCESSING_OUTPUT, DependencyType.TRAINING_DATA],
        DependencyType.HYPERPARAMETERS: [DependencyType.HYPERPARAMETERS, DependencyType.CUSTOM_PROPERTY],
        DependencyType.PAYLOAD_SAMPLES: [DependencyType.PAYLOAD_SAMPLES, DependencyType.PROCESSING_OUTPUT],
        DependencyType.CUSTOM_PROPERTY: [DependencyType.CUSTOM_PROPERTY]
    }
    
    compatible_types = compatibility_matrix.get(dep_type, [])
    return output_type in compatible_types

def _are_data_types_compatible(self, dep_data_type: str, output_data_type: str) -> bool:
    """Check if data types are compatible."""
    # Define data type compatibility
    compatibility_map = {
        'S3Uri': ['S3Uri', 'String'],  # S3Uri can sometimes be used as String
        'String': ['String', 'S3Uri'],  # String can sometimes accept S3Uri
        'Integer': ['Integer', 'Float'],  # Integer can be used as Float
        'Float': ['Float', 'Integer'],   # Float can accept Integer
        'Boolean': ['Boolean'],
    }
    
    compatible_types = compatibility_map.get(dep_data_type, [dep_data_type])
    return output_data_type in compatible_types
```

>[!info]
>This design allows for *flexible matching* while still enforcing *type safety*.

- [[Base Step Specification Dependency Type]]
- [[Base Step Specification Node Type]]

### 4. Resolution Strategy

>[!important]
> The resolver uses a strategic approach to dependency resolution:
> 
> 1. **Candidate Selection**: Find all *potential outputs* that could satisfy each dependency
> 2. **Confidence Scoring**: Calculate a *compatibility score* for each candidate
> 3. **Best Match Selection**: Choose the candidate with the *highest score* above a threshold
> 4. **Property Reference Creation**: Create a PropertyReference object for the resolved dependency

>[!info]
>For ambiguous cases, the resolver provides detailed logging about why a particular match was chosen:

```python
# Log alternative matches if they exist
if len(candidates) > 1:
    alternatives = [(c[2], c[3], c[1]) for c in candidates[1:3]]  # Top 2 alternatives
    logger.debug(f"Alternative matches: {alternatives}")
```

### 5. Performance Optimization with Caching

>[!important]
>The resolver includes a **caching mechanism** to avoid redundant calculations:

```python
def resolve_step_dependencies(self, consumer_step: str, 
                            available_steps: List[str]) -> Dict[str, PropertyReference]:
    """
    Resolve dependencies for a single step.
    """
    # Check cache first
    cache_key = f"{consumer_step}:{':'.join(sorted(available_steps))}"
    if cache_key in self._resolution_cache:
        logger.debug(f"Using cached resolution for step '{consumer_step}'")
        return self._resolution_cache[cache_key]
    
    # Perform resolution...
    
    # Cache the result
    self._resolution_cache[cache_key] = resolved
    return resolved
```

This caching is particularly valuable when using the same resolver for multiple related pipelines.

## Key Methods

### Registration

```python
def register_specification(self, step_name: str, spec: StepSpecification):
    """Register a step specification with the resolver."""
    self.registry.register(step_name, spec)
    # Clear cache when new specifications are added
    self._resolution_cache.clear()
```

### Dependency Resolution

```python
def resolve_all_dependencies(self, available_steps: List[str]) -> Dict[str, Dict[str, PropertyReference]]:
    """
    Resolve dependencies for all registered steps.
    
    Args:
        available_steps: List of step names that are available in the pipeline
        
    Returns:
        Dictionary mapping step names to their resolved dependencies
    """
```

```python
def resolve_step_dependencies(self, consumer_step: str, 
                            available_steps: List[str]) -> Dict[str, PropertyReference]:
    """
    Resolve dependencies for a single step.
    
    Args:
        consumer_step: Name of the step whose dependencies to resolve
        available_steps: List of available step names
        
    Returns:
        Dictionary mapping dependency names to property references
    """
```

### Debugging and Reporting

```python
def get_resolution_report(self, available_steps: List[str]) -> Dict[str, any]:
    """
    Generate a detailed resolution report for debugging.
    
    Args:
        available_steps: List of available step names
        
    Returns:
        Detailed report of resolution process
    """
```

## Factory Function

>[!important]
>The module provides a convenient **factory function** for creating properly configured dependency resolvers:

```python
def create_dependency_resolver(registry: Optional[SpecificationRegistry] = None,
                             semantic_matcher: Optional[SemanticMatcher] = None) -> UnifiedDependencyResolver:
    """
    Create a properly configured dependency resolver.
    
    Args:
        registry: Optional specification registry. If None, creates a new one.
        semantic_matcher: Optional semantic matcher. If None, creates a new one.
        
    Returns:
        Configured UnifiedDependencyResolver instance
    """
```

- [[Design Pattern Factory Method Pattern]]

## Usage Example

```python
# Create dependency resolver components
registry = SpecificationRegistry()
matcher = SemanticMatcher()
resolver = UnifiedDependencyResolver(registry, matcher)

# Register step specifications
resolver.register_specification("data_loading", data_loading_spec)
resolver.register_specification("preprocessing", preprocessing_spec)
resolver.register_specification("training", training_spec)

# Resolve dependencies for all steps
all_dependencies = resolver.resolve_all_dependencies(["data_loading", "preprocessing", "training"])

# Print the resolved dependencies for each step
for step_name, deps in all_dependencies.items():
    print(f"Step {step_name} dependencies:")
    for dep_name, prop_ref in deps.items():
        print(f"  {dep_name} -> {prop_ref}")

# Generate a detailed resolution report
report = resolver.get_resolution_report(["data_loading", "preprocessing", "training"])
print(f"Resolution rate: {report['resolution_summary']['resolution_rate']:.2f}")
```

## Integration with Pipeline Assembler

>[!important]
>The dependency resolver integrates with the **pipeline assembler** to *automatically wire step dependencies*:

```python
# In PipelineAssembler._propagate_messages:
resolver = self._get_dependency_resolver()

for src_step, dst_step in self.dag.edges:
    src_builder = self.step_builders[src_step]
    dst_builder = self.step_builders[dst_step]
    
    for dep_name, dep_spec in dst_builder.spec.dependencies.items():
        matches = []
        
        for out_name, out_spec in src_builder.spec.outputs.items():
            compatibility = resolver._calculate_compatibility(dep_spec, out_spec, src_builder.spec)
            if compatibility > 0.5:  # Same threshold as resolver
                matches.append((out_name, out_spec, compatibility))
        
        # Use best match if found
        if matches:
            matches.sort(key=lambda x: x[2], reverse=True)
            best_match = matches[0]
            
            self.step_messages[dst_step][dep_name] = {
                'source_step': src_step,
                'source_output': best_match[0],
                'match_type': 'specification_match',
                'compatibility': best_match[2]
            }
```

## Benefits of the Design

>[!important]
> The UnifiedDependencyResolver design provides several key benefits:
> 
> 1. **Declarative Pipeline Definition**: Steps declare their requirements and capabilities
> 2. **Automatic Connection**: Dependencies are resolved without manual wiring
> 3. **Loose Coupling**: Steps don't need knowledge of each other's implementation
> 4. **Flexibility**: Steps can be added, removed, or swapped with minimal changes
> 5. **Resilience**: Intelligent matching reduces brittleness in pipeline definitions
> 6. **Performance**: Caching improves resolution speed for complex pipelines


-----------
##  Recommended Notes

- [[Dependency Resolver Design]]
- [[Dependency Resolver Connect to Pipeline DAG]]
- [[Step Specification Design as Declarative Pipeline Architecture]]
