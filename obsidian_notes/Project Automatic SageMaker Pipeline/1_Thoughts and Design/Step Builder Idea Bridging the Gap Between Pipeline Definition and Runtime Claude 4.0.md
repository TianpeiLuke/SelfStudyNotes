---
tags:
  - thought
  - aws/sagemaker_pipeline
aliases: 
date of note: 2025-07-02
---

## Background

![[Step Builder Methods Most Time Consuming Group Pain Points#2. Bridging the Gap Between Pipeline Definition and Runtime]]

- [[Step Builder Methods Most Time Consuming Group Pain Points]]
- [[Step Builder Idea Bridging the Gap Between Pipeline Definition and Runtime Claude 3.7]]
- [[Step Builder Idea Bridging the Gap Between Pipeline Definition and Runtime Gemini]]

# Research-Based Systematic Solutions for Pipeline Definition vs Runtime Execution

After researching established patterns from workflow orchestration frameworks (SageMaker Pipelines, Apache Airflow, Prefect), I've identified systematic solutions based on proven industry practices for handling the gap between pipeline definition and runtime execution.

## Core Problem Analysis

The fundamental issue is the **temporal separation** between:
1. **Definition Time**: When pipeline structure and dependencies are declared
2. **Runtime**: When actual data flows and property values become available

This is a well-known problem in distributed systems and workflow orchestration, addressed differently by various frameworks:

- **SageMaker Pipelines**: Uses `JsonGet` and property files for runtime data access
- **Apache Airflow**: Uses XComs (cross-communications) for task-to-task data passing
- **Prefect**: Uses artifacts and result storage for workflow output management

## Systematic Solutions Based on Research

### 1. **Lazy Evaluation Pattern with Reference Objects**

**Research Basis**: This pattern is used extensively in TensorFlow's computation graphs and SageMaker's pipeline definitions.

**Implementation**:
```python
class PropertyReference:
    """Lazy evaluation reference to step properties."""
    
    def __init__(self, step_name: str, property_path: str, output_descriptor: str = None):
        self.step_name = step_name
        self.property_path = property_path
        self.output_descriptor = output_descriptor
        self._resolved_value = None
        
    def to_sagemaker_reference(self):
        """Convert to SageMaker-compatible reference format."""
        if self.output_descriptor:
            # For ProcessingStep outputs with descriptors
            return {"Get": f"Steps.{self.step_name}.ProcessingOutputConfig.Outputs['{self.output_descriptor}'].S3Output.S3Uri"}
        else:
            # For direct property access
            return {"Get": f"Steps.{self.step_name}.{self.property_path}"}
    
    def __str__(self):
        return f"PropertyReference({self.step_name}.{self.property_path})"

class StepOutputRegistry:
    """Central registry for step outputs using lazy evaluation."""
    
    def __init__(self):
        self._outputs = {}
        
    def register_output(self, step_name: str, logical_name: str, property_path: str, output_descriptor: str = None):
        """Register an output with lazy evaluation."""
        if step_name not in self._outputs:
            self._outputs[step_name] = {}
        
        self._outputs[step_name][logical_name] = PropertyReference(
            step_name=step_name,
            property_path=property_path,
            output_descriptor=output_descriptor
        )
    
    def get_output_reference(self, step_name: str, logical_name: str) -> PropertyReference:
        """Get a lazy reference to a step output."""
        if step_name not in self._outputs or logical_name not in self._outputs[step_name]:
            raise ValueError(f"Output {step_name}.{logical_name} not registered")
        
        return self._outputs[step_name][logical_name]
```

### 2. **Contract-Based Interface Definition**

**Research Basis**: Inspired by Airflow's XCom system and interface segregation principles from software architecture.

**Implementation**:
```python
from abc import ABC, abstractmethod
from typing import Dict, Any, Protocol

class StepContract(Protocol):
    """Protocol defining the contract for step inputs and outputs."""
    
    def get_input_schema(self) -> Dict[str, Any]:
        """Return the expected input schema."""
        ...
    
    def get_output_schema(self) -> Dict[str, Any]:
        """Return the provided output schema."""
        ...

class ContractValidator:
    """Validates contracts between pipeline steps."""
    
    @staticmethod
    def validate_connection(producer: StepContract, consumer: StepContract, 
                          output_name: str, input_name: str) -> bool:
        """Validate that producer output can satisfy consumer input."""
        producer_outputs = producer.get_output_schema()
        consumer_inputs = consumer.get_input_schema()
        
        if output_name not in producer_outputs:
            raise ValueError(f"Producer does not provide output: {output_name}")
        
        if input_name not in consumer_inputs:
            raise ValueError(f"Consumer does not expect input: {input_name}")
        
        # Type compatibility check
        producer_type = producer_outputs[output_name].get('type')
        consumer_type = consumer_inputs[input_name].get('type')
        
        if producer_type and consumer_type and producer_type != consumer_type:
            raise TypeError(f"Type mismatch: {producer_type} -> {consumer_type}")
        
        return True

# Enhanced StepBuilderBase with contracts
class ContractAwareStepBuilder(StepBuilderBase):
    """Step builder with contract validation."""
    
    def get_input_schema(self) -> Dict[str, Any]:
        """Return input schema based on config."""
        schema = {}
        for logical_name, description in self.get_input_requirements().items():
            schema[logical_name] = {
                'description': description,
                'type': 'S3Uri',  # Default type
                'required': 'optional' not in description.lower()
            }
        return schema
    
    def get_output_schema(self) -> Dict[str, Any]:
        """Return output schema based on config."""
        schema = {}
        for logical_name, description in self.get_output_properties().items():
            schema[logical_name] = {
                'description': description,
                'type': 'S3Uri',  # Default type
                'property_path': self.get_property_paths().get(logical_name)
            }
        return schema
```

- [[Step Contract for Dependency Resolution]]

### 3. **Event-Driven Pipeline Assembly**

**Research Basis**: Based on reactive programming patterns and event-driven architectures used in modern workflow systems.

**Implementation**:
```python
from typing import Callable, List
import logging

class PipelineEvent:
    """Represents an event in pipeline assembly."""
    
    def __init__(self, event_type: str, step_name: str, data: Dict[str, Any]):
        self.event_type = event_type
        self.step_name = step_name
        self.data = data
        self.timestamp = time.time()

class PipelineEventBus:
    """Event bus for pipeline assembly events."""
    
    def __init__(self):
        self._handlers = {}
        
    def subscribe(self, event_type: str, handler: Callable[[PipelineEvent], None]):
        """Subscribe to pipeline events."""
        if event_type not in self._handlers:
            self._handlers[event_type] = []
        self._handlers[event_type].append(handler)
    
    def publish(self, event: PipelineEvent):
        """Publish a pipeline event."""
        if event.event_type in self._handlers:
            for handler in self._handlers[event.event_type]:
                try:
                    handler(event)
                except Exception as e:
                    logging.error(f"Error in event handler: {e}")

class EventDrivenPipelineBuilder:
    """Pipeline builder using event-driven assembly."""
    
    def __init__(self):
        self.event_bus = PipelineEventBus()
        self.steps = {}
        self.connections = []
        
        # Subscribe to step registration events
        self.event_bus.subscribe("step_registered", self._on_step_registered)
        self.event_bus.subscribe("output_declared", self._on_output_declared)
        
    def register_step(self, step_builder: StepBuilderBase):
        """Register a step and publish event."""
        step_name = step_builder.__class__.__name__
        self.steps[step_name] = step_builder
        
        # Publish step registration event
        event = PipelineEvent("step_registered", step_name, {
            "builder": step_builder,
            "inputs": step_builder.get_input_requirements(),
            "outputs": step_builder.get_output_properties()
        })
        self.event_bus.publish(event)
    
    def _on_step_registered(self, event: PipelineEvent):
        """Handle step registration - attempt auto-wiring."""
        new_step = event.data["builder"]
        new_step_inputs = event.data["inputs"]
        
        # Try to auto-wire with existing steps
        for existing_step_name, existing_step in self.steps.items():
            if existing_step_name == event.step_name:
                continue
                
            existing_outputs = existing_step.get_output_properties()
            
            # Look for matching input/output pairs
            for input_name, input_desc in new_step_inputs.items():
                for output_name, output_desc in existing_outputs.items():
                    if self._can_connect(input_name, input_desc, output_name, output_desc):
                        self._create_connection(existing_step_name, output_name, event.step_name, input_name)
    
    def _can_connect(self, input_name: str, input_desc: str, output_name: str, output_desc: str) -> bool:
        """Determine if an input and output can be connected."""
        # Simple heuristic - can be made more sophisticated
        input_keywords = set(input_name.lower().split('_'))
        output_keywords = set(output_name.lower().split('_'))
        
        # Check for keyword overlap
        overlap = input_keywords.intersection(output_keywords)
        return len(overlap) > 0
    
    def _create_connection(self, producer_step: str, output_name: str, consumer_step: str, input_name: str):
        """Create a connection between steps."""
        connection = {
            "producer": producer_step,
            "output": output_name,
            "consumer": consumer_step,
            "input": input_name
        }
        self.connections.append(connection)
        
        logging.info(f"Auto-wired: {producer_step}.{output_name} -> {consumer_step}.{input_name}")
```

### 4. **Declarative Pipeline DSL with Validation**

**Research Basis**: Inspired by Kubernetes YAML manifests and Infrastructure as Code patterns.

**Implementation**:
```python
import yaml
from typing import Dict, Any, List
from dataclasses import dataclass

@dataclass
class PipelineStepDefinition:
    """Declarative step definition."""
    name: str
    type: str
    config: Dict[str, Any]
    inputs: Dict[str, Any] = None
    outputs: Dict[str, str] = None
    depends_on: List[str] = None

@dataclass
class PipelineDefinition:
    """Declarative pipeline definition."""
    name: str
    description: str
    steps: List[PipelineStepDefinition]
    parameters: Dict[str, Any] = None

class DeclarativePipelineParser:
    """Parser for declarative pipeline definitions."""
    
    @staticmethod
    def from_yaml(yaml_content: str) -> PipelineDefinition:
        """Parse pipeline definition from YAML."""
        data = yaml.safe_load(yaml_content)
        
        steps = []
        for step_data in data.get('steps', []):
            step = PipelineStepDefinition(
                name=step_data['name'],
                type=step_data['type'],
                config=step_data.get('config', {}),
                inputs=step_data.get('inputs', {}),
                outputs=step_data.get('outputs', {}),
                depends_on=step_data.get('depends_on', [])
            )
            steps.append(step)
        
        return PipelineDefinition(
            name=data['name'],
            description=data.get('description', ''),
            steps=steps,
            parameters=data.get('parameters', {})
        )
    
    @staticmethod
    def validate_definition(definition: PipelineDefinition) -> List[str]:
        """Validate pipeline definition for consistency."""
        errors = []
        step_names = {step.name for step in definition.steps}
        
        for step in definition.steps:
            # Check dependencies exist
            if step.depends_on:
                for dep in step.depends_on:
                    if dep not in step_names:
                        errors.append(f"Step '{step.name}' depends on non-existent step '{dep}'")
            
            # Check input references
            if step.inputs:
                for input_name, input_def in step.inputs.items():
                    if isinstance(input_def, dict) and 'from_step' in input_def:
                        source_step = input_def['from_step']
                        if source_step not in step_names:
                            errors.append(f"Step '{step.name}' input '{input_name}' references non-existent step '{source_step}'")
        
        return errors

# Example YAML pipeline definition
EXAMPLE_PIPELINE_YAML = """
name: "xgboost-training-pipeline"
description: "End-to-end XGBoost training pipeline"
parameters:
  region: "us-east-1"
  instance_type: "ml.m5.large"

steps:
  - name: "data-preprocessing"
    type: "TabularPreprocessing"
    config:
      processing_instance_type: "ml.m5.large"
      processing_instance_count: 1
    outputs:
      processed_data: "ProcessedTabularData"
  
  - name: "model-training"
    type: "XGBoostTraining"
    config:
      training_instance_type: "ml.m5.large"
      training_instance_count: 1
    inputs:
      training_data:
        from_step: "data-preprocessing"
        output: "processed_data"
    depends_on: ["data-preprocessing"]
    outputs:
      model_artifacts: "ModelArtifacts"
  
  - name: "model-registration"
    type: "ModelRegistration"
    config:
      model_package_group_name: "xgboost-models"
    inputs:
      model_data:
        from_step: "model-training"
        output: "model_artifacts"
    depends_on: ["model-training"]
"""
```

### 5. **Runtime Property Resolution Service**

**Research Basis**: Based on service-oriented architecture patterns and dependency injection frameworks.

**Implementation**:
```python
class PropertyResolutionService:
    """Service for resolving property references at runtime."""
    
    def __init__(self):
        self._resolution_strategies = []
        self._cache = {}
    
    def register_strategy(self, strategy: 'PropertyResolutionStrategy'):
        """Register a property resolution strategy."""
        self._resolution_strategies.append(strategy)
    
    def resolve_property(self, step_name: str, property_path: str, context: Dict[str, Any]) -> Any:
        """Resolve a property reference to its actual value."""
        cache_key = f"{step_name}.{property_path}"
        
        if cache_key in self._cache:
            return self._cache[cache_key]
        
        for strategy in self._resolution_strategies:
            if strategy.can_resolve(step_name, property_path, context):
                value = strategy.resolve(step_name, property_path, context)
                self._cache[cache_key] = value
                return value
        
        raise ValueError(f"Cannot resolve property: {step_name}.{property_path}")

class PropertyResolutionStrategy(ABC):
    """Abstract base class for property resolution strategies."""
    
    @abstractmethod
    def can_resolve(self, step_name: str, property_path: str, context: Dict[str, Any]) -> bool:
        """Check if this strategy can resolve the property."""
        pass
    
    @abstractmethod
    def resolve(self, step_name: str, property_path: str, context: Dict[str, Any]) -> Any:
        """Resolve the property to its actual value."""
        pass

class SageMakerPropertyStrategy(PropertyResolutionStrategy):
    """Strategy for resolving SageMaker step properties."""
    
    def can_resolve(self, step_name: str, property_path: str, context: Dict[str, Any]) -> bool:
        return property_path.startswith("properties.")
    
    def resolve(self, step_name: str, property_path: str, context: Dict[str, Any]) -> Any:
        # Implementation would use SageMaker SDK to resolve the property
        # This is a simplified example
        pipeline_execution = context.get('pipeline_execution')
        if pipeline_execution:
            return pipeline_execution.describe_step(step_name).get_property(property_path)
        
        # Return a reference object for pipeline definition time
        return {"Get": f"Steps.{step_name}.{property_path}"}
```

## Implementation Roadmap

### Phase 1: Foundation (Immediate)
1. Implement **Lazy Evaluation Pattern** with PropertyReference objects
2. Enhance existing Property Path Registry with validation
3. Add **Contract-Based Interface Definition** to step builders

### Phase 2: Automation (Short-term)
1. Implement **Event-Driven Pipeline Assembly** for auto-wiring
2. Create **Declarative Pipeline DSL** with YAML support
3. Add comprehensive validation and error reporting

### Phase 3: Advanced Features (Medium-term)
1. Implement **Runtime Property Resolution Service**
2. Add pipeline visualization and debugging tools
3. Create migration utilities for existing pipelines

## Benefits of This Systematic Approach

1. **Proven Patterns**: Based on successful implementations in major workflow frameworks
2. **Incremental Adoption**: Can be implemented gradually without breaking existing code
3. **Type Safety**: Contract-based validation catches errors at definition time
4. **Maintainability**: Declarative definitions are easier to understand and modify
5. **Debugging**: Clear separation of concerns makes issues easier to diagnose
6. **Scalability**: Event-driven architecture supports complex pipeline topologies

This research-based approach addresses the core problem systematically while building on proven patterns from the workflow orchestration domain.


-----------
##  Recommended Notes

- [[Step Builder Methods Analysis and Grouping]]
- [[Step Builder Methods Analysis Average Code lines Statistics]]
- [[Step Builder Methods Group Bug-Fix Focus]]
- [[Step Builder Methods Group Pain Points]]