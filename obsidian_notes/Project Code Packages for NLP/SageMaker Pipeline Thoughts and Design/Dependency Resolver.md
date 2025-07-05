---
tags:
  - thought
  - aws/sagemaker_pipeline
  - design/design_architecture
aliases: 
date of note: 2025-07-04
---

## What is the Purpose of Dependency Resolver?

The Dependency Resolver serves as the **intelligent matching engine** that automatically connects pipeline steps by analyzing their [step specifications](step_specification.md) and finding compatible input-output relationships. It transforms manual, error-prone dependency wiring into intelligent, automated resolution based on semantic compatibility scoring.

## Core Purpose

The Dependency Resolver provides **intelligent automation for pipeline dependency management** that:

1. **Automatic Dependency Resolution** - Eliminate manual property path wiring between steps
2. **Semantic Compatibility Matching** - Use intelligent scoring to find best matches
3. **Type Safety Validation** - Ensure data type compatibility between connected steps
4. **Multi-Criteria Scoring** - Consider type, semantics, keywords, and source compatibility
5. **Context-Scoped Resolution** - Work with isolated registry contexts for different pipelines
6. **Performance Optimization** - Cache resolution results and optimize matching algorithms

## Current Architecture

The dependency resolver follows a **composition pattern** where the resolver is independent and works with any specification registry:

```python
# Architecture Overview
RegistryManager
├── SpecificationRegistry (context: "pipeline_a")
├── SpecificationRegistry (context: "pipeline_b")
└── SpecificationRegistry (context: "default")

UnifiedDependencyResolver
├── registry: SpecificationRegistry (injected)
├── semantic_matcher: SemanticMatcher
└── _resolution_cache: Dict[str, Dict[str, PropertyReference]]
```

### Key Components

1. **UnifiedDependencyResolver** - Standalone resolver that works with any registry
2. **SpecificationRegistry** - Context-aware storage for step specifications
3. **RegistryManager** - Coordinates multiple isolated registry contexts
4. **SemanticMatcher** - Provides intelligent name similarity scoring

## Key Features

### 1. Intelligent Compatibility Scoring

The resolver uses a multi-factor scoring algorithm to determine the best matches:

```python
def _calculate_compatibility(self, dep_spec: DependencySpec, output_spec: OutputSpec,
                           provider_spec: StepSpecification) -> float:
    """Calculate compatibility score between dependency and output."""
    score = 0.0
    
    # 1. Dependency type compatibility (40% weight)
    if dep_spec.dependency_type == output_spec.output_type:
        score += 0.4
    elif self._are_types_compatible(dep_spec.dependency_type, output_spec.output_type):
        score += 0.2
    else:
        return 0.0  # Incompatible types
    
    # 2. Data type compatibility (20% weight)
    if dep_spec.data_type == output_spec.data_type:
        score += 0.2
    elif self._are_data_types_compatible(dep_spec.data_type, output_spec.data_type):
        score += 0.1
    
    # 3. Semantic name similarity (25% weight)
    semantic_score = self.semantic_matcher.calculate_similarity(
        dep_spec.logical_name, output_spec.logical_name
    )
    score += semantic_score * 0.25
    
    # 4. Compatible source check (10% weight)
    if dep_spec.compatible_sources:
        if provider_spec.step_type in dep_spec.compatible_sources:
            score += 0.1
    else:
        score += 0.05  # Small bonus if no sources specified
    
    # 5. Keyword matching bonus (5% weight)
    if dep_spec.semantic_keywords:
        keyword_score = self._calculate_keyword_match(dep_spec.semantic_keywords, output_spec.logical_name)
        score += keyword_score * 0.05
    
    return min(score, 1.0)
```

### 2. Type Compatibility Matrix

The resolver maintains a compatibility matrix for different dependency types:

```python
def _are_types_compatible(self, dep_type: DependencyType, output_type: DependencyType) -> bool:
    """Check if dependency and output types are compatible."""
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
```

### 3. Data Type Compatibility

The resolver also handles data type compatibility for flexible matching:

```python
def _are_data_types_compatible(self, dep_data_type: str, output_data_type: str) -> bool:
    """Check if data types are compatible."""
    compatibility_map = {
        'S3Uri': ['S3Uri', 'String'],      # S3Uri can be used as String
        'String': ['String', 'S3Uri'],     # String can accept S3Uri
        'Integer': ['Integer', 'Float'],   # Integer can be used as Float
        'Float': ['Float', 'Integer'],     # Float can accept Integer
        'Boolean': ['Boolean'],
    }
    
    compatible_types = compatibility_map.get(dep_data_type, [dep_data_type])
    return output_data_type in compatible_types
```

### 4. Context-Scoped Resolution

The resolver works with context-specific registries managed by the RegistryManager:

```python
# Get context-specific registry
from src.pipeline_deps.registry_manager import get_registry

# Each pipeline gets its own isolated registry
fraud_registry = get_registry("fraud_detection")
credit_registry = get_registry("credit_scoring")

# Create resolver for specific context
fraud_resolver = UnifiedDependencyResolver(fraud_registry)
credit_resolver = UnifiedDependencyResolver(credit_registry)

# Registries are completely isolated
fraud_resolver.register_specification("preprocessing", FRAUD_PREPROCESSING_SPEC)
credit_resolver.register_specification("preprocessing", CREDIT_PREPROCESSING_SPEC)
```

### 5. Performance Optimization

The resolver includes caching and optimization features:

```python
class UnifiedDependencyResolver:
    def __init__(self, registry: Optional[SpecificationRegistry] = None):
        self.registry = registry or SpecificationRegistry()
        self.semantic_matcher = SemanticMatcher()
        self._resolution_cache: Dict[str, Dict[str, PropertyReference]] = {}
    
    def resolve_step_dependencies(self, consumer_step: str, available_steps: List[str]) -> Dict[str, PropertyReference]:
        """Resolve dependencies with caching."""
        # Check cache first
        cache_key = f"{consumer_step}:{':'.join(sorted(available_steps))}"
        if cache_key in self._resolution_cache:
            return self._resolution_cache[cache_key]
        
        # Perform resolution and cache result
        resolved = self._perform_resolution(consumer_step, available_steps)
        self._resolution_cache[cache_key] = resolved
        return resolved
```

### 6. Comprehensive Error Handling

The resolver provides detailed error reporting and debugging capabilities:

```python
def get_resolution_report(self, available_steps: List[str]) -> Dict[str, any]:
    """Generate detailed resolution report for debugging."""
    report = {
        'total_steps': len(available_steps),
        'registered_steps': len([s for s in available_steps if self.registry.get_specification(s)]),
        'step_details': {},
        'unresolved_dependencies': [],
        'resolution_summary': {}
    }
    
    for step_name in available_steps:
        # Detailed analysis for each step
        step_report = self._analyze_step_resolution(step_name, available_steps)
        report['step_details'][step_name] = step_report
    
    return report
```

## Integration with Other Components

### With Step Specifications

The resolver consumes [step specifications](step_specification.md) to understand step capabilities:

```python
from src.pipeline_deps.base_specifications import StepSpecification, DependencySpec, OutputSpec, DependencyType, NodeType

# Define step specification
XGBOOST_TRAINING_SPEC = StepSpecification(
    step_type="XGBoostTraining",
    node_type=NodeType.INTERNAL,
    dependencies=[
        DependencySpec(
            logical_name="training_data",
            dependency_type=DependencyType.PROCESSING_OUTPUT,
            required=True,
            compatible_sources=["TabularPreprocessing"],
            semantic_keywords=["data", "processed", "training"]
        )
    ],
    outputs=[
        OutputSpec(
            logical_name="model_artifacts",
            output_type=DependencyType.MODEL_ARTIFACTS,
            property_path="properties.ModelArtifacts.S3ModelArtifacts"
        )
    ]
)

# Register with resolver
resolver.register_specification("training", XGBOOST_TRAINING_SPEC)
resolved = resolver.resolve_step_dependencies("training", ["preprocessing", "training"])
```

### With Specification Registry

The resolver works with any specification registry through dependency injection:

```python
from src.pipeline_deps.specification_registry import SpecificationRegistry
from src.pipeline_deps.dependency_resolver import UnifiedDependencyResolver

# Create context-specific registry
pipeline_registry = SpecificationRegistry("fraud_detection")

# Create resolver with the registry
resolver = UnifiedDependencyResolver(pipeline_registry)

# Register steps through resolver (delegates to registry)
resolver.register_specification("preprocessing", PREPROCESSING_SPEC)
resolver.register_specification("training", XGBOOST_TRAINING_SPEC)

# Resolve dependencies
resolved = resolver.resolve_all_dependencies(["preprocessing", "training"])
```

### With Registry Manager

The registry manager coordinates multiple isolated contexts:

```python
from src.pipeline_deps.registry_manager import get_registry, list_contexts, get_context_stats

# Get registries for different pipelines
fraud_registry = get_registry("fraud_detection")
credit_registry = get_registry("credit_scoring")

# Create resolvers for each context
fraud_resolver = UnifiedDependencyResolver(fraud_registry)
credit_resolver = UnifiedDependencyResolver(credit_registry)

# Check all contexts
contexts = list_contexts()  # ["fraud_detection", "credit_scoring"]
stats = get_context_stats()  # Statistics for each context
```

## Resolution Algorithm

### 1. Step-by-Step Resolution Process

```python
def resolve_all_dependencies(self, available_steps: List[str]) -> Dict[str, Dict[str, PropertyReference]]:
    """
    Resolution Process:
    1. For each step in available_steps:
       a. Get step specification from registry
       b. For each dependency in the specification:
          i. Find all compatible outputs from other steps
          ii. Score each compatibility using multi-factor algorithm
          iii. Select best match above threshold (0.5)
          iv. Create PropertyReference for the match
       c. Validate all required dependencies are resolved
    2. Return complete resolution mapping
    """
```

### 2. Compatibility Scoring Factors

| Factor | Weight | Description |
|--------|--------|-------------|
| **Dependency Type Match** | 40% | Exact or compatible dependency type matching |
| **Data Type Compatibility** | 20% | S3Uri, String, Integer, Float, Boolean compatibility |
| **Semantic Name Similarity** | 25% | Fuzzy matching between logical names |
| **Compatible Source Check** | 10% | Step type listed in compatible_sources |
| **Keyword Matching** | 5% | Semantic keywords found in output name |

### 3. Resolution Confidence Levels

```python
# Confidence thresholds for resolution decisions
RESOLUTION_THRESHOLD = 0.5  # Minimum score for automatic resolution

# Typical score ranges:
# 0.9-1.0: Excellent match (exact type + source + keywords)
# 0.7-0.9: Good match (compatible type + good semantic similarity)
# 0.5-0.7: Acceptable match (compatible type + some similarity)
# 0.0-0.5: Poor match (not automatically resolved)
```

## Usage Examples

### 1. Basic Resolution

```python
from src.pipeline_deps.dependency_resolver import UnifiedDependencyResolver
from src.pipeline_deps.registry_manager import get_registry

# Get context-specific registry
registry = get_registry("my_pipeline")

# Create resolver
resolver = UnifiedDependencyResolver(registry)

# Register step specifications
resolver.register_specification("preprocessing", PREPROCESSING_SPEC)
resolver.register_specification("training", XGBOOST_TRAINING_SPEC)
resolver.register_specification("registration", REGISTRATION_SPEC)

# Resolve all dependencies
available_steps = ["preprocessing", "training", "registration"]
resolved = resolver.resolve_all_dependencies(available_steps)

# Result:
# {
#   "training": {
#     "training_data": PropertyReference(step="preprocessing", output="processed_data")
#   },
#   "registration": {
#     "model_artifacts": PropertyReference(step="training", output="model_artifacts")
#   }
# }
```

### 2. Context-Isolated Resolution

```python
# Create separate contexts for different pipelines
fraud_registry = get_registry("fraud_detection")
credit_registry = get_registry("credit_scoring")

# Create resolvers for each context
fraud_resolver = UnifiedDependencyResolver(fraud_registry)
credit_resolver = UnifiedDependencyResolver(credit_registry)

# Register different specifications in each context
fraud_resolver.register_specification("preprocessing", FRAUD_PREPROCESSING_SPEC)
credit_resolver.register_specification("preprocessing", CREDIT_PREPROCESSING_SPEC)

# Resolve within each context independently
fraud_resolved = fraud_resolver.resolve_all_dependencies(["preprocessing", "training"])
credit_resolved = credit_resolver.resolve_all_dependencies(["preprocessing", "training"])
```

### 3. Resolution Debugging

```python
# Generate detailed resolution report
report = resolver.get_resolution_report(["preprocessing", "training", "registration"])

print(f"Resolution Summary:")
print(f"  Total Dependencies: {report['resolution_summary']['total_dependencies']}")
print(f"  Resolved: {report['resolution_summary']['resolved_dependencies']}")
print(f"  Resolution Rate: {report['resolution_summary']['resolution_rate']:.1%}")

# Detailed step analysis
for step_name, details in report['step_details'].items():
    print(f"\nStep: {step_name}")
    print(f"  Type: {details['step_type']}")
    print(f"  Dependencies: {details['total_dependencies']} ({details['required_dependencies']} required)")
    print(f"  Resolved: {len(details['resolved_dependencies'])}")
    
    if details['unresolved_dependencies']:
        print(f"  Unresolved: {details['unresolved_dependencies']}")
```

### 4. Working with PropertyReference

```python
# PropertyReference provides runtime property resolution
resolved = resolver.resolve_step_dependencies("training", ["preprocessing", "training"])

for dep_name, prop_ref in resolved.items():
    print(f"Dependency: {dep_name}")
    print(f"  Source Step: {prop_ref.step_name}")
    print(f"  Output: {prop_ref.output_spec.logical_name}")
    print(f"  Property Path: {prop_ref.output_spec.property_path}")
    
    # Convert to SageMaker Properties object
    sagemaker_prop = prop_ref.to_sagemaker_property()
    print(f"  SageMaker Property: {sagemaker_prop}")
    # Result: {"Get": "Steps.preprocessing.properties.ProcessingOutputConfig.Outputs['ProcessedData'].S3Output.S3Uri"}
```

### 5. Error Handling

```python
from src.pipeline_deps.dependency_resolver import DependencyResolutionError

try:
    resolved = resolver.resolve_all_dependencies(["training", "registration"])
except DependencyResolutionError as e:
    print(f"Resolution failed: {e}")
    
    # Generate report to understand what went wrong
    report = resolver.get_resolution_report(["training", "registration"])
    
    for step_name in report['unresolved_dependencies']:
        step_details = report['step_details'][step_name]
        print(f"Step '{step_name}' failed:")
        print(f"  Error: {step_details.get('error', 'Unknown error')}")
        print(f"  Unresolved: {step_details['unresolved_dependencies']}")
```

## Strategic Value

### For Pipeline Development

1. **Elimination of Manual Wiring** - No more fragile property path management
2. **Intelligent Automation** - System understands step relationships
3. **Error Prevention** - Type safety and compatibility checking
4. **Rapid Prototyping** - Quick pipeline construction without detailed wiring

### For System Architecture

1. **Separation of Concerns** - Resolution logic isolated from step implementation
2. **Context Isolation** - Complete separation between different pipeline contexts
3. **Extensibility** - Easy to add new compatibility rules and scoring factors
4. **Maintainability** - Centralized dependency logic
5. **Testability** - Resolution logic can be thoroughly tested in isolation

### For Developer Experience

1. **Reduced Cognitive Load** - Focus on business logic, not wiring details
2. **Better Error Messages** - Detailed resolution reports for debugging
3. **IDE Support** - Type-safe property references
4. **Documentation** - Self-documenting dependency relationships

## Performance Characteristics

### Caching Strategy

The resolver implements intelligent caching to optimize repeated resolutions:

```python
# Cache key includes consumer step and sorted available steps
cache_key = f"{consumer_step}:{':'.join(sorted(available_steps))}"

# Cache is automatically cleared when new specifications are registered
resolver.register_specification("new_step", NEW_SPEC)  # Clears cache
```

### Complexity Analysis

- **Registration**: O(1) per step
- **Single Step Resolution**: O(n*m) where n = available steps, m = outputs per step
- **Full Pipeline Resolution**: O(s*n*m) where s = steps with dependencies
- **Cached Resolution**: O(1) for repeated queries

### Memory Usage

- **Specifications**: Stored once per context in registry
- **Cache**: Grows with unique (step, available_steps) combinations
- **Resolver**: Lightweight, can be created per operation if needed

## Best Practices

### 1. Context Management

```python
# Use meaningful context names
fraud_registry = get_registry("fraud_detection_v2")
credit_registry = get_registry("credit_scoring_prod")

# Clear contexts when no longer needed
from src.pipeline_deps.registry_manager import clear_context
clear_context("temporary_experiment")
```

### 2. Specification Design

```python
# Design specifications for good resolution
GOOD_SPEC = StepSpecification(
    step_type="DataPreprocessing",
    node_type=NodeType.INTERNAL,
    dependencies=[
        DependencySpec(
            logical_name="raw_data",
            dependency_type=DependencyType.PROCESSING_OUTPUT,
            compatible_sources=["DataLoading", "DataIngestion"],  # Specific sources
            semantic_keywords=["raw", "data", "input"],           # Helpful keywords
            description="Raw input data for preprocessing"
        )
    ],
    outputs=[
        OutputSpec(
            logical_name="processed_data",                        # Clear, descriptive name
            output_type=DependencyType.PROCESSING_OUTPUT,
            property_path="properties.ProcessingOutputConfig.Outputs['ProcessedData'].S3Output.S3Uri",
            description="Cleaned and preprocessed data"
        )
    ]
)
```

### 3. Resolution Debugging

```python
# Always check resolution reports for complex pipelines
report = resolver.get_resolution_report(all_steps)

if report['resolution_summary']['resolution_rate'] < 0.8:
    print("Warning: Low resolution rate, check specifications")
    
    # Identify problematic steps
    for step_name, details in report['step_details'].items():
        if details['unresolved_dependencies']:
            print(f"Step '{step_name}' has unresolved dependencies:")
            for dep in details['unresolved_dependencies']:
                print(f"  - {dep}")
```

### 4. Performance Optimization

```python
# Create resolver once per context, reuse for multiple resolutions
resolver = UnifiedDependencyResolver(get_registry("my_pipeline"))

# Register all specifications upfront
for step_name, spec in all_specifications.items():
    resolver.register_specification(step_name, spec)

# Resolve multiple times with caching benefits
resolved_1 = resolver.resolve_all_dependencies(steps_batch_1)
resolved_2 = resolver.resolve_all_dependencies(steps_batch_2)

# Clear cache if memory becomes a concern
resolver.clear_cache()
```

## Limitations and Considerations

### Current Limitations

1. **Single Registry per Resolver** - Each resolver works with one registry at a time
2. **No Cross-Context Resolution** - Cannot resolve dependencies across different contexts
3. **Static Compatibility Rules** - Compatibility matrix is hardcoded, not configurable
4. **Simple Semantic Matching** - Uses basic string similarity, not advanced NLP

### Future Enhancement Opportunities

1. **Configurable Compatibility Rules** - Allow custom compatibility matrices
2. **Advanced Semantic Matching** - Integrate with embedding-based similarity
3. **Cross-Context Dependencies** - Support for dependencies spanning multiple pipelines
4. **Resolution Strategies** - Multiple resolution algorithms (greedy, optimal, etc.)
5. **Performance Monitoring** - Built-in metrics and performance tracking

## Related Components

- **[Step Specification](step_specification.md)** - Provides the declarative metadata that drives resolution
- **[Specification Registry](specification_registry.md)** - Context-aware storage for step specifications
- **[Registry Manager](registry_manager.md)** - Coordinates multiple isolated registry contexts
- **[Base Specifications](step_specification.md)** - Core Pydantic models for dependencies and outputs

---

The Dependency Resolver represents the **intelligent automation layer** that transforms pipeline construction from manual, error-prone wiring into intelligent, specification-driven automation. It serves as the foundation for automated pipeline assembly while maintaining the flexibility and extensibility needed for complex ML pipeline scenarios.

-----------

##  Recommended Notes

- [[Dependency Resolver System Review]]
- [[Dependency Resolver Connect to Pipeline DAG]]
- [[Dependency Resolver Hybrid Design Review]]


- [[Step Specification as Declarative Pipeline Architecture]]
- [[Step Builder Methods Dependency Management Claude 4.0]]
- [[Step Builder Methods Dependency Management Gemini]]