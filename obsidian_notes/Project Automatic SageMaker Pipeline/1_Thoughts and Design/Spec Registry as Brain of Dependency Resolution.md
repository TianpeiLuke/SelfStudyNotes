---
tags:
  - thought
  - design/design_architecture
aliases: 
date of note: 2025-07-16
---
Excellent question! Let me explain how `SpecificationRegistry` is used within the `UnifiedDependencyResolver` (the dependency manager). The registry serves as the **knowledge base** that the resolver queries to make intelligent dependency matching decisions.

## Core Integration Pattern

The `UnifiedDependencyResolver` uses `SpecificationRegistry` as its **data source** for dependency resolution:

```python
class UnifiedDependencyResolver:
    def __init__(self, registry: SpecificationRegistry, semantic_matcher: SemanticMatcher):
        self.registry = registry  # Registry provides the step specifications
        self.semantic_matcher = semantic_matcher
```

## Key Usage Patterns in Dependency Resolution

### 1. **Step Specification Lookup**
```python
def resolve_step_dependencies(self, consumer_step: str, available_steps: List[str]):
    # Registry provides the specification for the consuming step
    consumer_spec = self.registry.get_specification(consumer_step)
    if not consumer_spec:
        return {}
    
    # Iterate through the step's declared dependencies
    for dep_name, dep_spec in consumer_spec.dependencies.items():
        # Resolve each dependency...
```

### 2. **Provider Discovery**
```python
def _resolve_single_dependency(self, dep_spec: DependencySpec, consumer_step: str, available_steps: List[str]):
    candidates = []
    
    for provider_step in available_steps:
        # Registry provides specification for each potential provider
        provider_spec = self.registry.get_specification(provider_step)
        if not provider_spec:
            continue
            
        # Check each output of the provider step
        for output_name, output_spec in provider_spec.outputs.items():
            confidence = self._calculate_compatibility(dep_spec, output_spec, provider_spec)
            # Build candidates list...
```

### 3. **Compatibility Analysis**
The registry enables the resolver to:
- **Access dependency requirements**: What does the consuming step need?
- **Access output capabilities**: What can each provider step offer?
- **Compare specifications**: Are they compatible?

## Detailed Workflow

### Step 1: **Consumer Analysis**
```python
# Registry provides the consumer's dependency requirements
consumer_spec = self.registry.get_specification("model_training_step")
# Returns StepSpecification with dependencies like:
# - "training_data" (DependencySpec: type=PROCESSING_OUTPUT, required=True)
# - "hyperparameters" (DependencySpec: type=HYPERPARAMETERS, required=False)
```

### Step 2: **Provider Discovery**
```python
# For each available step, registry provides their output capabilities
for provider_step in ["data_loading", "preprocessing", "config_generation"]:
    provider_spec = self.registry.get_specification(provider_step)
    # Each spec contains outputs like:
    # - preprocessing: outputs={"processed_data": OutputSpec(type=PROCESSING_OUTPUT)}
    # - config_generation: outputs={"model_config": OutputSpec(type=HYPERPARAMETERS)}
```

### Step 3: **Compatibility Matching**
```python
def _calculate_compatibility(self, dep_spec: DependencySpec, output_spec: OutputSpec, provider_spec: StepSpecification):
    # Registry data enables these checks:
    
    # 1. Type compatibility
    if dep_spec.dependency_type == output_spec.output_type:  # PROCESSING_OUTPUT == PROCESSING_OUTPUT
        score += 0.4
    
    # 2. Source compatibility  
    if provider_spec.step_type in dep_spec.compatible_sources:  # "PreprocessingStep" in ["DataLoadingStep", "PreprocessingStep"]
        score += 0.1
    
    # 3. Semantic matching
    semantic_score = self.semantic_matcher.calculate_similarity_with_aliases(
        dep_spec.logical_name,      # "training_data" 
        output_spec                 # logical_name="processed_data", aliases=["TrainingData", "DATA"]
    )
```

## Registry Methods Used by Resolver

### **Primary Query Methods**:
```python
# Get step specification by name
consumer_spec = registry.get_specification("training_step")

# Get all specifications of a certain type (less commonly used)
processing_steps = registry.get_specifications_by_type("ProcessingStep")

# List all available steps
all_steps = registry.list_step_names()
```

### **Compatibility Helper** (used internally):
```python
# Registry's built-in compatibility finder
compatible_outputs = registry.find_compatible_outputs(dependency_spec)
# Returns: [(step_name, output_name, output_spec, score), ...]
```

## Data Flow Example

Let's trace a real dependency resolution:

```python
# 1. Resolver gets consumer requirements from registry
consumer_spec = registry.get_specification("model_training")
training_data_dep = consumer_spec.dependencies["training_data"]
# DependencySpec(logical_name="training_data", dependency_type=PROCESSING_OUTPUT, required=True)

# 2. Resolver checks each provider via registry
preprocessing_spec = registry.get_specification("data_preprocessing") 
processed_data_output = preprocessing_spec.outputs["processed_data"]
# OutputSpec(logical_name="processed_data", output_type=PROCESSING_OUTPUT, aliases=["TrainingData"])

# 3. Resolver calculates compatibility using registry data
compatibility = resolver._calculate_compatibility(training_data_dep, processed_data_output, preprocessing_spec)
# Result: High compatibility due to:
# - Type match: PROCESSING_OUTPUT == PROCESSING_OUTPUT
# - Semantic match: "training_data" matches alias "TrainingData"

# 4. Resolver creates PropertyReference using registry data
property_ref = PropertyReference(
    step_name="data_preprocessing",
    output_spec=processed_data_output  # From registry
)
```

## Why Registry is Essential for Dependency Resolution

### **Without Registry**:
- Resolver would need step specifications passed manually
- No centralized knowledge of what steps provide/require
- No systematic way to discover compatible outputs
- Hard to maintain consistency across pipeline

### **With Registry**:
- **Centralized knowledge**: All step capabilities in one place
- **Systematic discovery**: Query all available providers
- **Consistent specifications**: Validated, structured data
- **Efficient lookup**: Indexed by step name and type

## Registry as the "Brain" of Dependency Resolution

The registry essentially serves as the **knowledge graph** that enables intelligent dependency resolution:

- **Nodes**: Step specifications (what each step does)
- **Edges**: Compatibility relationships (what can connect to what)
- **Queries**: Resolver asks "who can provide X?" and registry answers with candidates
- **Scoring**: Registry data enables confidence-based matching

This design separates **knowledge storage** (registry) from **resolution logic** (resolver), making the system more maintainable and testable.


-----------
##  Recommended Notes

- [[Specification Registry Design]]
- [[Dependency Resolver Design]]
- [[Semantic Matcher for Dependency Resolution]]