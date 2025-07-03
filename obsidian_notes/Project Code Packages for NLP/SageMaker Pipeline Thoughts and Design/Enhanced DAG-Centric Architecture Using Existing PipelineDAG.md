---
tags:
  - thought
  - aws/sagemaker_pipeline
aliases: 
date of note: 2025-07-02
---

![[Pipeline DAG and Declarative Spec and Reference Property for Step Builder#^9fd7e1]]

Perfect! I can see the existing `PipelineDAG` class provides a solid foundation. Let me adjust the solution to build upon this existing infrastructure while adding the port-based dependency management and property reference capabilities.

## **Enhanced PipelineDAG with Port-Based Dependencies**

- [[Pipeline DAG]]

```python
from dataclasses import dataclass
from typing import Dict, List, Optional, Any, Set, Tuple
from src.pipeline_builder.pipeline_dag import PipelineDAG

@dataclass
class InputPort:
    """Input port specification for a pipeline step."""
    name: str
    data_type: str
    required: bool = True
    description: str = ""
    semantic_keywords: List[str] = None
    
    def __post_init__(self):
        if self.semantic_keywords is None:
            self.semantic_keywords = []

@dataclass
class OutputPort:
    """Output port specification for a pipeline step."""
    name: str
    data_type: str
    property_path: str  # Runtime SageMaker property path
    description: str = ""
    
@dataclass
class PropertyReference:
    """Lazy evaluation reference that bridges definition-time and runtime."""
    step_name: str
    output_port: OutputPort
    
    def to_sagemaker_property(self):
        """Convert to SageMaker Properties object at runtime."""
        return {"Get": f"Steps.{self.step_name}.{self.output_port.property_path}"}
    
    def __str__(self):
        return f"{self.step_name}.{self.output_port.name}"

@dataclass
class DependencyEdge:
    """Represents a typed dependency edge between step ports."""
    source_step: str
    target_step: str
    source_port: OutputPort
    target_port: InputPort
    confidence: float = 1.0
    
    def to_property_reference(self) -> PropertyReference:
        """Convert edge to a property reference for SageMaker."""
        return PropertyReference(
            step_name=self.source_step,
            output_port=self.source_port
        )

class EnhancedPipelineDAG(PipelineDAG):
    """
    Enhanced version of PipelineDAG with port-based dependency management.
    Extends the existing PipelineDAG to add typed ports and intelligent dependency resolution.
    """
    
    def __init__(self, nodes: Optional[List[str]] = None, edges: Optional[List[tuple]] = None):
        super().__init__(nodes, edges)
        
        # Enhanced data structures for port-based dependencies
        self.step_contracts: Dict[str, 'StepContract'] = {}
        self.dependency_edges: List[DependencyEdge] = []
        self.property_references: Dict[str, Dict[str, PropertyReference]] = {}
        
    def register_step_contract(self, step_name: str, contract: 'StepContract'):
        """Register a step contract defining its input/output ports."""
        self.step_contracts[step_name] = contract
        self.add_node(step_name)
        logger.info(f"Registered contract for step: {step_name}")
        
    def auto_resolve_dependencies(self) -> List[DependencyEdge]:
        """Automatically resolve dependencies based on port compatibility."""
        resolved_edges = []
        
        for target_step, target_contract in self.step_contracts.items():
            for input_port in target_contract.inputs.values():
                if input_port.required and not self._is_input_satisfied(target_step, input_port.name):
                    # Find compatible output ports
                    candidates = self._find_compatible_outputs(target_step, input_port)
                    if candidates:
                        best_match = max(candidates, key=lambda x: x[1])
                        source_step, output_port, confidence = best_match
                        
                        # Create dependency edge
                        edge = DependencyEdge(
                            source_step=source_step,
                            target_step=target_step,
                            source_port=output_port,
                            target_port=input_port,
                            confidence=confidence
                        )
                        
                        self.add_dependency_edge(edge)
                        resolved_edges.append(edge)
                        
        return resolved_edges
    
    def add_dependency_edge(self, edge: DependencyEdge):
        """Add a typed dependency edge."""
        self.dependency_edges.append(edge)
        
        # Add to the base DAG structure
        self.add_edge(edge.source_step, edge.target_step)
        
        # Create property reference
        prop_ref = edge.to_property_reference()
        if edge.target_step not in self.property_references:
            self.property_references[edge.target_step] = {}
        self.property_references[edge.target_step][edge.target_port.name] = prop_ref
        
        logger.info(f"Added dependency edge: {edge.source_step}.{edge.source_port.name} -> {edge.target_step}.{edge.target_port.name}")
    
    def _find_compatible_outputs(self, target_step: str, input_port: InputPort) -> List[Tuple[str, OutputPort, float]]:
        """Find compatible output ports for an input port."""
        candidates = []
        
        for source_step, source_contract in self.step_contracts.items():
            if source_step == target_step:
                continue  # Skip self-connections
                
            for output_port in source_contract.outputs.values():
                confidence = self._calculate_port_compatibility(output_port, input_port)
                if confidence > 0.5:
                    candidates.append((source_step, output_port, confidence))
                    
        return candidates
    
    def _calculate_port_compatibility(self, output_port: OutputPort, input_port: InputPort) -> float:
        """Calculate compatibility score between ports."""
        # Data type compatibility (40%)
        type_score = 1.0 if output_port.data_type == input_port.data_type else 0.3
        
        # Semantic name similarity (40%)
        semantic_score = self._semantic_similarity(output_port.name, input_port.name)
        
        # Keyword matching (20%)
        keyword_score = 0.0
        if input_port.semantic_keywords:
            for keyword in input_port.semantic_keywords:
                if keyword.lower() in output_port.name.lower():
                    keyword_score = 1.0
                    break
        
        return (type_score * 0.4) + (semantic_score * 0.4) + (keyword_score * 0.2)
    
    def _semantic_similarity(self, name1: str, name2: str) -> float:
        """Calculate semantic similarity between two names."""
        # Simple implementation - can be enhanced with more sophisticated matching
        name1_norm = name1.lower().replace('_', '').replace('-', '')
        name2_norm = name2.lower().replace('_', '').replace('-', '')
        
        if name1_norm == name2_norm:
            return 1.0
        
        # Check for substring matches
        if name1_norm in name2_norm or name2_norm in name1_norm:
            return 0.8
        
        # Check for common keywords
        common_keywords = ['model', 'data', 'output', 'input', 'artifacts', 'training']
        for keyword in common_keywords:
            if keyword in name1_norm and keyword in name2_norm:
                return 0.6
        
        return 0.0
    
    def _is_input_satisfied(self, step_name: str, input_name: str) -> bool:
        """Check if an input port is already satisfied by an existing edge."""
        for edge in self.dependency_edges:
            if edge.target_step == step_name and edge.target_port.name == input_name:
                return True
        return False
    
    def get_step_inputs(self, step_name: str) -> Dict[str, PropertyReference]:
        """Get all property references for a step's inputs."""
        return self.property_references.get(step_name, {})
    
    def validate_dependencies(self) -> List[str]:
        """Validate the dependency graph for completeness and correctness."""
        errors = []
        
        # Check for cycles (inherited from base class)
        try:
            self.topological_sort()
        except ValueError as e:
            errors.append(str(e))
        
        # Check for unsatisfied required inputs
        for step_name, contract in self.step_contracts.items():
            for input_port in contract.inputs.values():
                if input_port.required and not self._is_input_satisfied(step_name, input_port.name):
                    errors.append(f"Required input '{input_port.name}' on step '{step_name}' is not satisfied")
        
        return errors
    
    def to_sagemaker_inputs(self) -> Dict[str, Dict[str, Any]]:
        """Convert the dependency graph to SageMaker input format."""
        sagemaker_inputs = {}
        
        for step_name in self.nodes:
            step_inputs = {}
            for input_name, prop_ref in self.get_step_inputs(step_name).items():
                step_inputs[input_name] = prop_ref.to_sagemaker_property()
            
            if step_inputs:
                sagemaker_inputs[step_name] = step_inputs
                
        return sagemaker_inputs
```

## **Step Contract Definition**

- [[Step Contract for Dependency Resolution]]

```python
@dataclass
class StepContract:
    """Complete contract defining a step's input and output ports."""
    step_type: str
    inputs: Dict[str, InputPort]
    outputs: Dict[str, OutputPort]
    
    def __init__(self, step_type: str, inputs: List[InputPort], outputs: List[OutputPort]):
        self.step_type = step_type
        self.inputs = {port.name: port for port in inputs}
        self.outputs = {port.name: port for port in outputs}
    
    def get_input_port(self, name: str) -> Optional[InputPort]:
        return self.inputs.get(name)
    
    def get_output_port(self, name: str) -> Optional[OutputPort]:
        return self.outputs.get(name)
```

## **Enhanced Step Builder Integration**

```python
class EnhancedStepBuilderBase(StepBuilderBase):
    """Enhanced step builder that integrates with the DAG-based dependency system."""
    
    # Subclasses must define this
    STEP_CONTRACT: StepContract = None
    
    def __init_subclass__(cls, **kwargs):
        super().__init_subclass__(**kwargs)
        if not hasattr(cls, 'STEP_CONTRACT') or cls.STEP_CONTRACT is None:
            raise ValueError(f"{cls.__name__} must define STEP_CONTRACT")
    
    def register_with_dag(self, dag: EnhancedPipelineDAG, step_name: str):
        """Register this step builder with a pipeline DAG."""
        dag.register_step_contract(step_name, self.STEP_CONTRACT)
    
    def create_step_with_dag_inputs(self, dag: EnhancedPipelineDAG, step_name: str, **kwargs):
        """Create step using inputs resolved from the DAG."""
        # Get resolved inputs from the DAG
        dag_inputs = dag.get_step_inputs(step_name)
        
        # Convert property references to SageMaker format
        sagemaker_inputs = {}
        for input_name, prop_ref in dag_inputs.items():
            sagemaker_inputs[input_name] = prop_ref.to_sagemaker_property()
        
        # Merge with any additional kwargs
        sagemaker_inputs.update(kwargs)
        
        # Create the step
        return self.create_step(**sagemaker_inputs)
```

## **Concrete Implementation Example**

```python
# Define step contracts
XGBOOST_TRAINING_CONTRACT = StepContract(
    step_type="XGBoostTraining",
    inputs=[
        InputPort(
            name="training_data",
            data_type="S3Uri",
            required=True,
            description="Training dataset S3 location",
            semantic_keywords=["data", "input", "training", "dataset"]
        ),
        InputPort(
            name="hyperparameters",
            data_type="S3Uri",
            required=False,
            description="Hyperparameters configuration file",
            semantic_keywords=["config", "params", "hyperparameters"]
        )
    ],
    outputs=[
        OutputPort(
            name="model_artifacts",
            data_type="S3Uri",
            property_path="properties.ModelArtifacts.S3ModelArtifacts",
            description="Trained model artifacts"
        ),
        OutputPort(
            name="training_job_name",
            data_type="String",
            property_path="properties.TrainingJobName",
            description="Training job name"
        )
    ]
)

class XGBoostTrainingStepBuilder(EnhancedStepBuilderBase):
    """XGBoost training step builder with DAG integration."""
    
    STEP_CONTRACT = XGBOOST_TRAINING_CONTRACT
    
    def create_step(self, **resolved_inputs):
        """Create step using resolved inputs from DAG."""
        # All dependency resolution is handled by the DAG
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

## **Pipeline Construction with Enhanced DAG**

```python
def build_pipeline_with_enhanced_dag():
    """Build pipeline using the enhanced DAG system."""
    
    # Create enhanced DAG
    dag = EnhancedPipelineDAG()
    
    # Create step builders
    preprocessing_builder = TabularPreprocessingStepBuilder(config=preprocess_config)
    training_builder = XGBoostTrainingStepBuilder(config=training_config)
    registration_builder = ModelRegistrationStepBuilder(config=registration_config)
    
    # Register step contracts with the DAG
    preprocessing_builder.register_with_dag(dag, "preprocessing-step")
    training_builder.register_with_dag(dag, "training-step")
    registration_builder.register_with_dag(dag, "registration-step")
    
    # Auto-resolve dependencies
    resolved_edges = dag.auto_resolve_dependencies()
    logger.info(f"Auto-resolved {len(resolved_edges)} dependency edges")
    
    # Validate the DAG
    errors = dag.validate_dependencies()
    if errors:
        raise ValueError(f"DAG validation failed: {errors}")
    
    # Build steps in topological order
    execution_order = dag.topological_sort()
    steps = []
    
    for step_name in execution_order:
        if step_name == "preprocessing-step":
            step = preprocessing_builder.create_step_with_dag_inputs(dag, step_name)
        elif step_name == "training-step":
            step = training_builder.create_step_with_dag_inputs(dag, step_name)
        elif step_name == "registration-step":
            step = registration_builder.create_step_with_dag_inputs(dag, step_name)
        
        steps.append(step)
    
    return Pipeline(name="enhanced-dag-pipeline", steps=steps)
```

## **Benefits of Enhanced DAG Approach**

### **1. Builds on Existing Infrastructure**
- Leverages the proven `PipelineDAG` class
- Maintains backward compatibility
- Adds port-based enhancements incrementally

### **2. Unified Dependency Management**
- **Nodes** represent steps with typed input/output ports
- **Edges** represent typed dependencies with confidence scoring
- **Property References** bridge definition-time and runtime

### **3. Intelligent Auto-Resolution**
- Semantic matching based on port names and keywords
- Type compatibility checking
- Confidence scoring for ambiguous matches

### **4. Validation and Safety**
- DAG cycle detection (inherited)
- Required input validation
- Type safety through port definitions

This enhanced approach builds upon your existing `PipelineDAG` infrastructure while adding the sophisticated dependency management and property reference capabilities we need to solve both the dependency complexity and definition-runtime bridge problems.

Would you like me to proceed with implementing this enhanced DAG-based solution?

-----------
##  Recommended Notes

- [[Step Builder Declarative Pipeline Architecture with Smart Proxies]]