---
tags:
  - planning
  - aws/sagemaker_pipeline
aliases: 
date of note: 2025-07-04
---

Based on the comprehensive implementation plan you've provided, I'll propose a **Minimal Viable Product (MVP)** that focuses on the core functionality needed to demonstrate the enhanced DAG-centric pipeline architecture. Here's my MVP plan:

# MVP Plan: Enhanced DAG-Centric Pipeline Architecture

## **MVP Scope: Core Dependency Resolution with One Working Example**

The MVP will focus on proving the core concept with a single, complete end-to-end example that demonstrates automatic dependency resolution.

## **MVP Phase 1: Essential Foundation (Week 1)**

### **1.1 Core Infrastructure - Minimal Set**
**Keep existing structure, add only essential new folders:**
```
src/pipeline_dag/          # Enhanced DAG functionality
src/pipeline_step_specs/    # Step specifications (already exists)
```

**Skip for MVP:**
- `src/pipeline_contracts/` (merge into step_specs)
- `src/pipeline_proxies/` (defer smart proxies)
- `src/pipeline_fluent/` (defer fluent API)
- `src/pipeline_validation/` (basic validation only)

### **1.2 Enhanced DAG - Core Only**
**Create minimal enhanced DAG:**
```python
# src/pipeline_dag/enhanced_dag.py
class EnhancedPipelineDAG(PipelineDAG):
    """MVP: Basic enhanced DAG with dependency resolution."""
    
    def __init__(self):
        super().__init__()
        self.step_specifications = {}
        self.resolved_dependencies = {}
    
    def register_step_spec(self, step_name: str, spec: StepSpecification):
        """Register a step specification."""
        self.step_specifications[step_name] = spec
        self.add_node(step_name)
    
    def auto_resolve_dependencies(self) -> Dict[str, Dict[str, PropertyReference]]:
        """MVP: Simple dependency resolution."""
        # Basic implementation that matches by type and name similarity
        pass
```

### **1.3 Step Specifications - Use Existing**
**Leverage existing `src/pipeline_step_specs/` and enhance:**
- Use existing `StepSpecification` from `base_specifications.py`
- Enhance 2-3 existing step specs with proper dependency/output definitions
- Focus on: `preprocessing_spec.py`, `xgboost_training_spec.py`, `registration_spec.py`

## **MVP Phase 2: Single Working Pipeline (Week 2)**

### **2.1 Choose One Pipeline for MVP**
**Target: XGBoost End-to-End Pipeline**
- Preprocessing → Training → Registration
- 3 steps, clear dependencies
- Already exists in codebase

### **2.2 Enhanced Step Specifications**
**Update only 3 step specs:**

```python
# src/pipeline_step_specs/preprocessing_spec.py
PREPROCESSING_SPEC = StepSpecification(
    step_type="TabularPreprocessing",
    node_type=NodeType.INTERNAL,
    dependencies=[
        DependencySpec(
            logical_name="raw_data",
            dependency_type=DependencyType.TRAINING_DATA,
            required=True,
            compatible_sources=["DataLoad"],
            semantic_keywords=["data", "input", "raw"]
        )
    ],
    outputs=[
        OutputSpec(
            logical_name="processed_data",
            output_type=DependencyType.PROCESSING_OUTPUT,
            property_path="properties.ProcessingOutputConfig.Outputs['train'].S3Output.S3Uri"
        )
    ]
)
```

### **2.3 Basic Dependency Resolution**
**Simple resolver that works for MVP:**
```python
# src/pipeline_deps/dependency_resolver.py (enhance existing)
class MVPDependencyResolver:
    """MVP: Simple dependency resolution by type matching."""
    
    def resolve_pipeline_dependencies(self, dag: EnhancedPipelineDAG) -> Dict[str, Dict[str, PropertyReference]]:
        """Resolve all dependencies in the pipeline."""
        resolved = {}
        
        for step_name, spec in dag.step_specifications.items():
            resolved[step_name] = {}
            
            for dep_name, dep_spec in spec.dependencies.items():
                # Find compatible output
                source_step, source_output = self._find_compatible_output(dep_spec, dag)
                if source_step:
                    resolved[step_name][dep_name] = PropertyReference(
                        step_name=source_step,
                        output_spec=source_output
                    )
        
        return resolved
```

## **MVP Phase 3: Integration (Week 3)**

### **3.1 Update One Step Builder**
**Enhance only `XGBoostTrainingStepBuilder`:**
```python
# src/pipeline_steps/builder_training_step_xgboost.py
class XGBoostTrainingStepBuilder(StepBuilderBase):
    """MVP: Enhanced with specification."""
    
    STEP_SPEC = XGBOOST_TRAINING_SPEC  # Reference to spec
    
    def create_step_with_resolved_inputs(self, resolved_inputs: Dict[str, PropertyReference], **kwargs):
        """MVP: Create step using resolved dependencies."""
        # Convert PropertyReference to SageMaker format
        training_input = None
        if "training_data" in resolved_inputs:
            training_input = TrainingInput(
                s3_data=resolved_inputs["training_data"].to_sagemaker_property()
            )
        
        return self.create_step(training_input=training_input, **kwargs)
```

### **3.2 MVP Pipeline Builder**
**Simple builder that demonstrates the concept:**
```python
# src/pipeline_builder/mvp_enhanced_builder.py
class MVPEnhancedPipelineBuilder:
    """MVP: Demonstrates enhanced DAG with dependency resolution."""
    
    def __init__(self):
        self.dag = EnhancedPipelineDAG()
        self.step_builders = {}
        self.resolver = MVPDependencyResolver()
    
    def add_step(self, step_name: str, builder: StepBuilderBase):
        """Add step with specification."""
        if hasattr(builder, 'STEP_SPEC'):
            self.dag.register_step_spec(step_name, builder.STEP_SPEC)
        self.step_builders[step_name] = builder
    
    def build_pipeline(self) -> Pipeline:
        """Build pipeline with automatic dependency resolution."""
        # Resolve dependencies
        resolved = self.resolver.resolve_pipeline_dependencies(self.dag)
        
        # Build steps in topological order
        execution_order = self.dag.topological_sort()
        steps = []
        
        for step_name in execution_order:
            builder = self.step_builders[step_name]
            step_resolved_inputs = resolved.get(step_name, {})
            
            if hasattr(builder, 'create_step_with_resolved_inputs'):
                step = builder.create_step_with_resolved_inputs(step_resolved_inputs)
            else:
                step = builder.create_step()  # Fallback
            
            steps.append(step)
        
        return Pipeline(name="mvp-enhanced-pipeline", steps=steps)
```

## **MVP Phase 4: Working Example (Week 4)**

### **4.1 Create MVP Example**
```python
# pipeline_examples/mvp_enhanced_xgboost.py
def build_mvp_enhanced_pipeline():
    """MVP: XGBoost pipeline with automatic dependency resolution."""
    
    builder = MVPEnhancedPipelineBuilder()
    
    # Add steps (order doesn't matter - DAG will resolve)
    builder.add_step("registration", ModelRegistrationStepBuilder(config))
    builder.add_step("training", XGBoostTrainingStepBuilder(config))  # Enhanced
    builder.add_step("preprocessing", TabularPreprocessingStepBuilder(config))
    
    # Build with automatic dependency resolution
    pipeline = builder.build_pipeline()
    
    return pipeline
```

### **4.2 Basic Validation**
```python
# src/pipeline_dag/enhanced_dag.py (add method)
def validate_dependencies(self) -> List[str]:
    """MVP: Basic validation."""
    errors = []
    
    for step_name, spec in self.step_specifications.items():
        for dep_name, dep_spec in spec.dependencies.items():
            if dep_spec.required:
                # Check if dependency can be satisfied
                compatible_found = self._has_compatible_output(dep_spec)
                if not compatible_found:
                    errors.append(f"Step '{step_name}' missing required dependency '{dep_name}'")
    
    return errors
```

## **MVP Success Criteria**

### **Functional Requirements:**
1. ✅ **Automatic Dependency Resolution**: Pipeline builder automatically connects compatible steps
2. ✅ **Type Safety**: Dependency types are validated (basic level)
3. ✅ **Working Example**: One complete XGBoost pipeline builds and runs
4. ✅ **Backward Compatibility**: Existing pipelines continue to work

### **Technical Requirements:**
1. ✅ **Enhanced DAG**: Basic DAG with step specifications
2. ✅ **Step Specifications**: 3 steps have proper dependency/output specs
3. ✅ **Dependency Resolution**: Simple but working resolver
4. ✅ **Integration**: At least one step builder uses resolved inputs

### **Demonstration Value:**
1. ✅ **Proof of Concept**: Shows the architecture works
2. ✅ **Developer Experience**: Easier pipeline construction
3. ✅ **Maintainability**: Clear dependency declarations
4. ✅ **Extensibility**: Foundation for full implementation

## **MVP Timeline: 4 Weeks**

**Week 1**: Enhanced DAG + Step Specifications
**Week 2**: Dependency Resolution + Basic Integration  
**Week 3**: Step Builder Enhancement + MVP Builder
**Week 4**: Working Example + Testing + Documentation

## **Post-MVP Roadmap**

After MVP success:
1. **Smart Proxies** for IDE auto-completion
2. **Fluent API** for better developer experience
3. **Comprehensive Validation** with detailed error messages
4. **Multiple Pipeline Examples**
5. **Performance Optimization**

This MVP focuses on proving the core concept with minimal complexity while providing a solid foundation for the full implementation. Would you like me to proceed with this MVP approach?








-----------
##  Recommended Notes

- [[The Lean Product Playbook Chapter Summary 2.4 MVP Feature Sets]]
- [[The Lean Product Playbook Chapter Summary 2.5 MVP Testing]]

- [[Specification-Driven Design Architecture for Pipeline Automation]]
- [[Pain Points Summary for Template Pipeline Design]]
- [[Standardization Rules for Template Pipeline]]
- [[2025-07-02 Planning for Dependency Management and Smart Proxies]]