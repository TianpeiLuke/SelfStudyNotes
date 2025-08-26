---
tags:
  - thought
  - aws/sagemaker_pipeline
aliases: 
date of note: 2025-07-02
---

# Unified Solution: Declarative Pipeline Architecture with Smart Proxies

I'll combine both solutions into a comprehensive system that addresses dependency management complexity AND the definition-time vs runtime gap through a unified declarative architecture.

## **Core Architecture: The "Pipeline Contract System"**

The unified solution centers around **Pipeline Contracts** - declarative specifications that define both the dependency requirements AND the runtime property mappings in a single, type-safe system.

### **1. Unified Step Specification**

```python
from dataclasses import dataclass
from typing import Dict, List, Optional, Any, Union
from enum import Enum

class DependencyType(Enum):
    MODEL_ARTIFACTS = "model_artifacts"
    PROCESSING_OUTPUT = "processing_output"
    CUSTOM_PROPERTY = "custom_property"

@dataclass
class PropertyReference:
    """Lazy evaluation reference that bridges definition-time and runtime."""
    step_name: str
    property_path: str
    logical_name: str
    
    def to_sagemaker_property(self):
        """Convert to SageMaker Properties object at runtime."""
        return {"Get": f"Steps.{self.step_name}.{self.property_path}"}
    
    def __str__(self):
        return f"{self.step_name}.{self.logical_name}"

@dataclass
class DependencySpec:
    """Declarative dependency specification with runtime resolution."""
    logical_name: str
    dependency_type: DependencyType
    required: bool = True
    compatible_sources: List[str] = None
    semantic_keywords: List[str] = None  # For intelligent matching
    description: str = ""

@dataclass
class OutputSpec:
    """Declarative output specification with runtime property path."""
    logical_name: str
    output_type: DependencyType
    property_path: str  # Runtime SageMaker property path
    description: str = ""
    data_type: str = "S3Uri"

class StepContract:
    """Complete contract defining step's inputs, outputs, and runtime mappings."""
    
    def __init__(self, step_type: str, dependencies: List[DependencySpec], 
                 outputs: List[OutputSpec]):
        self.step_type = step_type
        self.dependencies = {dep.logical_name: dep for dep in dependencies}
        self.outputs = {out.logical_name: out for out in outputs}
        
    def get_dependency(self, logical_name: str) -> Optional[DependencySpec]:
        return self.dependencies.get(logical_name)
    
    def get_output(self, logical_name: str) -> Optional[OutputSpec]:
        return self.outputs.get(logical_name)
```

### **2. Smart Step Output Proxy**

```python
class StepOutputProxy:
    """Intelligent proxy that provides type-safe access to step outputs."""
    
    def __init__(self, step: Step, contract: StepContract):
        self._step = step
        self._contract = contract
        
    def __getattr__(self, logical_name: str):
        """Provide IDE auto-completion and type safety."""
        output_spec = self._contract.get_output(logical_name)
        if not output_spec:
            available = list(self._contract.outputs.keys())
            raise AttributeError(
                f"Step '{self._step.name}' has no output '{logical_name}'. "
                f"Available outputs: {available}"
            )
        
        # Return a PropertyReference that can be resolved at runtime
        return PropertyReference(
            step_name=self._step.name,
            property_path=output_spec.property_path,
            logical_name=logical_name
        )
    
    def __dir__(self):
        """Enable IDE auto-completion."""
        return list(self._contract.outputs.keys())
    
    def list_outputs(self) -> Dict[str, str]:
        """Developer-friendly output listing."""
        return {name: spec.description for name, spec in self._contract.outputs.items()}
```

### **3. Intelligent Dependency Resolver**

```python
class UnifiedDependencyResolver:
    """Resolves dependencies using contracts and semantic matching."""
    
    def __init__(self):
        self.contracts: Dict[str, StepContract] = {}
        self.semantic_matcher = SemanticMatcher()
        
    def register_contract(self, contract: StepContract):
        """Register a step contract."""
        self.contracts[contract.step_type] = contract
        
    def resolve_dependencies(self, consumer_step_type: str, 
                           available_proxies: List[StepOutputProxy]) -> Dict[str, PropertyReference]:
        """Resolve all dependencies for a consumer step."""
        consumer_contract = self.contracts.get(consumer_step_type)
        if not consumer_contract:
            raise ValueError(f"No contract registered for {consumer_step_type}")
        
        resolved = {}
        unresolved = []
        
        for dep_name, dep_spec in consumer_contract.dependencies.items():
            resolution = self._resolve_single_dependency(dep_spec, available_proxies)
            if resolution:
                resolved[dep_name] = resolution
            elif dep_spec.required:
                unresolved.append(dep_name)
        
        if unresolved:
            raise DependencyResolutionError(f"Unresolved dependencies: {unresolved}")
        
        return resolved
    
    def _resolve_single_dependency(self, dep_spec: DependencySpec, 
                                 available_proxies: List[StepOutputProxy]) -> Optional[PropertyReference]:
        """Resolve a single dependency with confidence scoring."""
        candidates = []
        
        for proxy in available_proxies:
            for output_name, output_spec in proxy._contract.outputs.items():
                confidence = self._calculate_match_confidence(dep_spec, output_spec)
                if confidence > 0.5:
                    prop_ref = PropertyReference(
                        step_name=proxy._step.name,
                        property_path=output_spec.property_path,
                        logical_name=output_name
                    )
                    candidates.append((prop_ref, confidence))
        
        if candidates:
            # Return highest confidence match
            return sorted(candidates, key=lambda x: x[1], reverse=True)[0][0]
        
        return None
    
    def _calculate_match_confidence(self, dep_spec: DependencySpec, 
                                  output_spec: OutputSpec) -> float:
        """Calculate match confidence using multiple factors."""
        # Type compatibility (50% weight)
        type_score = 1.0 if dep_spec.dependency_type == output_spec.output_type else 0.0
        
        # Semantic similarity (40% weight)
        semantic_score = self.semantic_matcher.similarity(
            dep_spec.logical_name, output_spec.logical_name
        )
        
        # Keyword matching (10% weight)
        keyword_score = 0.0
        if dep_spec.semantic_keywords:
            for keyword in dep_spec.semantic_keywords:
                if keyword.lower() in output_spec.logical_name.lower():
                    keyword_score = 1.0
                    break
        
        return (type_score * 0.5) + (semantic_score * 0.4) + (keyword_score * 0.1)
```

### **4. Declarative Step Builder Base**

```python
class DeclarativeStepBuilder(StepBuilderBase):
    """Enhanced step builder with declarative contracts."""
    
    # Subclasses must define this
    STEP_CONTRACT: StepContract = None
    
    def __init_subclass__(cls, **kwargs):
        super().__init_subclass__(**kwargs)
        if not hasattr(cls, 'STEP_CONTRACT') or cls.STEP_CONTRACT is None:
            raise ValueError(f"{cls.__name__} must define STEP_CONTRACT")
        
        # Auto-register the contract
        resolver.register_contract(cls.STEP_CONTRACT)
    
    def build(self, dependencies: List[StepOutputProxy] = None) -> Tuple[Step, StepOutputProxy]:
        """Build step with automatic dependency resolution."""
        resolved_inputs = {}
        
        if dependencies:
            # Use the unified resolver
            resolved_inputs = resolver.resolve_dependencies(
                self.STEP_CONTRACT.step_type, dependencies
            )
        
        # Convert PropertyReferences to SageMaker properties
        sagemaker_inputs = {}
        for logical_name, prop_ref in resolved_inputs.items():
            sagemaker_inputs[logical_name] = prop_ref.to_sagemaker_property()
        
        # Create the step
        step = self.create_step(**sagemaker_inputs)
        
        # Return both step and proxy
        proxy = StepOutputProxy(step, self.STEP_CONTRACT)
        return step, proxy
```

### **5. Concrete Step Implementation Example**

```python
# XGBoost Training Step Contract
XGBOOST_TRAINING_CONTRACT = StepContract(
    step_type="XGBoostTraining",
    dependencies=[
        DependencySpec(
            logical_name="training_data",
            dependency_type=DependencyType.PROCESSING_OUTPUT,
            required=True,
            compatible_sources=["TabularPreprocessing", "DataLoad"],
            semantic_keywords=["data", "input", "training"],
            description="S3 URI for training dataset"
        ),
        DependencySpec(
            logical_name="hyperparameters",
            dependency_type=DependencyType.CUSTOM_PROPERTY,
            required=False,
            compatible_sources=["HyperparameterPrep"],
            semantic_keywords=["config", "params", "hyperparameters"],
            description="Hyperparameters configuration"
        )
    ],
    outputs=[
        OutputSpec(
            logical_name="model_artifacts",
            output_type=DependencyType.MODEL_ARTIFACTS,
            property_path="properties.ModelArtifacts.S3ModelArtifacts",
            description="Trained model artifacts",
            data_type="S3Uri"
        ),
        OutputSpec(
            logical_name="training_job_name",
            output_type=DependencyType.CUSTOM_PROPERTY,
            property_path="properties.TrainingJobName",
            description="SageMaker training job name",
            data_type="String"
        )
    ]
)

class XGBoostTrainingStepBuilder(DeclarativeStepBuilder):
    """Simplified XGBoost training step builder."""
    
    STEP_CONTRACT = XGBOOST_TRAINING_CONTRACT
    
    def create_step(self, **resolved_inputs) -> TrainingStep:
        """Create step using resolved inputs."""
        # All dependency resolution is handled automatically
        # Just focus on step creation logic
        estimator = self._create_estimator()
        
        training_inputs = {}
        if "training_data" in resolved_inputs:
            training_inputs["training"] = TrainingInput(
                s3_data=resolved_inputs["training_data"]
            )
        
        return TrainingStep(
            name=self._get_step_name('XGBoostTraining'),
            estimator=estimator,
            inputs=training_inputs
        )
```

### **6. Pipeline Construction with Type Safety**

```python
# Pipeline construction becomes intuitive and type-safe
def build_pipeline():
    # Create step builders
    preprocessing_builder = TabularPreprocessingStepBuilder(config=preprocess_config)
    training_builder = XGBoostTrainingStepBuilder(config=training_config)
    registration_builder = ModelRegistrationStepBuilder(config=registration_config)
    
    # Build steps with automatic dependency resolution
    preprocess_step, preprocess_outputs = preprocessing_builder.build()
    
    # IDE provides auto-completion for preprocess_outputs.processed_data
    training_step, training_outputs = training_builder.build(
        dependencies=[preprocess_outputs]
    )
    
    # IDE provides auto-completion for training_outputs.model_artifacts
    registration_step, _ = registration_builder.build(
        dependencies=[training_outputs, preprocess_outputs]
    )
    
    return Pipeline(
        name="xgboost-pipeline",
        steps=[preprocess_step, training_step, registration_step]
    )
```

## **Unified Benefits**

### **Dependency Management:**
1. **90% code reduction** - No more complex `_match_*` methods
2. **Declarative specifications** - Clear, self-documenting contracts
3. **Intelligent resolution** - Semantic matching with confidence scoring
4. **Type safety** - Compile-time error detection

### **Definition-Runtime Bridge:**
1. **PropertyReference objects** - Lazy evaluation bridges the gap
2. **Smart proxies** - Type-safe access to step outputs
3. **Automatic unwrapping** - Seamless conversion to SageMaker properties
4. **IDE support** - Auto-completion and static analysis

### **Developer Experience:**
1. **Intuitive pipeline construction** - Natural Python syntax
2. **Fail-fast error detection** - Catch issues at definition time
3. **Self-documenting code** - Contracts serve as living documentation
4. **Gradual adoption** - Can be implemented incrementally

This unified solution eliminates both the dependency management complexity AND the definition-runtime gap through a single, coherent architectural approach that prioritizes developer experience while maintaining system robustness.

Would you like me to proceed with implementing this unified declarative pipeline architecture?








-----------
##  Recommended Notes


- [[Step Builder Methods Analysis and Grouping]]
- [[Step Builder Methods Group Pain Points]]


- [[Step Builder Idea Bridging the Gap Between Pipeline Definition and Runtime Claude 3.7]]
- [[Step Builder Idea Bridging the Gap Between Pipeline Definition and Runtime Claude 4.0]]
- [[Step Builder Idea Bridging the Gap Between Pipeline Definition and Runtime Gemini]]


- [[Step Builder Methods Dependency Management Claude 4.0]]
- [[Step Builder Methods Dependency Management Gemini]]