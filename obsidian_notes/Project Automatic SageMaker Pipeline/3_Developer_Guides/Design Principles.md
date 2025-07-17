---
tags:
  - project
  - design_principles
  - aws/sagemaker_pipeline
aliases: 
date of note: 2025-07-16
---
Our pipeline architecture follows a set of core design principles that guide development and integration. Understanding these principles is essential for developing pipeline steps that align with the overall system design.

## Core Design Principles

### 1. Separation of Concerns

Each component in the architecture has a specific, well-defined responsibility:

- **Step Specifications**: Define the "what" - inputs, outputs, and connectivity
- **Script Contracts**: Define the "where" - container paths and environment variables
- **Step Builders**: Define the "how" - SageMaker integration and resources
- **Processing Scripts**: Define the "logic" - business logic and algorithms

This separation allows components to evolve independently while maintaining compatibility through well-defined interfaces.

### 2. Specification-Driven Design

The architecture is fundamentally specification-driven, with specifications defining step requirements and capabilities:

- **Declarative Intent**: Express what you want, not how to implement it
- **Explicit Contracts**: Make requirements and dependencies explicit
- **Self-Documenting**: Specifications serve as documentation
- **Validation-First**: Validate at design time, not runtime

By prioritizing specifications, we can ensure robustness, maintainability, and consistency across the pipeline.

### 3. Dependency Resolution via Semantic Matching

Dependencies between steps are resolved through semantic matching rather than hard-coded connections:

- **Logical Names**: Use descriptive names for inputs and outputs
- **Semantic Keywords**: Enrich connections with semantic metadata
- **Compatible Sources**: Explicitly define which steps can provide dependencies
- **Required vs. Optional**: Clearly distinguish between required and optional dependencies

This approach enables flexible pipeline assembly while maintaining strong validation.

### 4. Build-Time Validation

Our architecture prioritizes catching issues at build time rather than runtime:

- **Contract Alignment**: Validate script contracts against specifications
- **Property Path Consistency**: Ensure consistent property paths in outputs
- **Cross-Step Validation**: Validate connectivity between steps
- **Configuration Validation**: Validate configurations before execution

By shifting validation left, we reduce the risk of runtime failures and improve developer experience.

### 5. Hybrid Design Approach

We follow a hybrid design approach that combines the best of specification-driven and config-driven approaches:

- **Specifications for Dependencies**: Use specifications for dependency resolution
- **Configurations for Implementation**: Use configurations for SageMaker implementation details
- **Universal Resolution Logic**: Apply consistent resolution across all pipeline types
- **Progressive Interfaces**: Support both high-level and detailed interfaces

This hybrid approach balances ease of use with flexibility and control.

## Architectural Patterns

### Four-Layer Architecture

The pipeline follows a four-layer architecture:

1. **Specification Layer**: Defines step inputs, outputs, and connections
2. **Contract Layer**: Defines script interface and environment
3. **Builder Layer**: Creates SageMaker steps and resolves dependencies
4. **Script Layer**: Implements business logic

Each layer has a well-defined responsibility and communicates with adjacent layers through explicit interfaces.

### Registry Pattern

Step components are registered in centralized registries:

- **Step Name Registry**: Maps step names to component types
- **Specification Registry**: Provides access to step specifications
- **Builder Registry**: Maps step types to builder classes

This pattern enables discovery, validation, and consistency checking across the system.

### Template Pattern

Pipeline templates provide reusable pipeline patterns:

- **DAG Definition**: Define the pipeline's directed acyclic graph
- **Config Mapping**: Map configurations to steps
- **Builder Mapping**: Map step types to builder classes

Templates enforce consistent pipeline patterns while allowing customization through configurations.

## Implementation Principles

### Avoid Hardcoding

Avoid hardcoding paths, environment variables, or dependencies:

- **Use Script Contracts**: Reference paths from contracts
- **Use Specifications**: Reference dependencies from specifications
- **Use Configurations**: Reference parameters from configurations

Hardcoded values reduce flexibility and increase maintenance costs.

### Follow SageMaker Conventions

Adhere to SageMaker's conventions for container paths and environment:

- **Processing Inputs**: `/opt/ml/processing/input/{logical_name}`
- **Processing Outputs**: `/opt/ml/processing/output/{logical_name}`
- **Training Inputs**: `/opt/ml/input/data/{channel_name}`
- **Model Outputs**: `/opt/ml/model`

Following these conventions ensures compatibility with SageMaker's infrastructure.

### Test for Edge Cases

Always test for edge cases in your components:

- **Missing Dependencies**: How does your step handle missing optional dependencies?
- **Type Conversion**: Do you handle type conversion correctly in environment variables?
- **Path Handling**: Do you handle directory vs. file path differences?
- **Job Type Variants**: Does your step work for all job type variants?

Edge case testing improves robustness and reduces production issues.

### Design for Extensibility

Design your components with extensibility in mind:

- **Support Job Type Variants**: Allow for training, calibration, validation variants
- **Allow Configuration Override**: Make parameters configurable
- **Use Inheritance**: Leverage inheritance for shared functionality
- **Follow Template Method Pattern**: Define abstract methods for specialization

Extensible components adapt to changing requirements with minimal changes.

## Design Anti-Patterns to Avoid

### Anti-Pattern: Direct Script-to-Builder Coupling

**Avoid** having step builders directly reference script paths or environment variables without going through contracts:

```python
# WRONG - Hardcoded path
def _get_inputs(self):
    return [
        ProcessingInput(
            source=s3_uri,
            destination="/opt/ml/processing/input/data"  # Hardcoded
        )
    ]
```

**Correct** approach - use script contract:

```python
# CORRECT - Use contract
def _get_inputs(self, inputs):
    contract = self.spec.script_contract
    return [
        ProcessingInput(
            source=inputs["data"],
            destination=contract.expected_input_paths["data"]
        )
    ]
```

### Anti-Pattern: Property Path Inconsistency

**Avoid** inconsistent property paths in output specifications:

```python
# WRONG - Inconsistent property path
"output": OutputSpec(
    logical_name="output",
    property_path="properties.Outputs.output.S3Uri"  # Wrong format
)
```

**Correct** approach - use standard format:

```python
# CORRECT - Standard format
"output": OutputSpec(
    logical_name="output",
    property_path="properties.ProcessingOutputConfig.Outputs['output'].S3Output.S3Uri"
)
```

### Anti-Pattern: Script Path Hardcoding

**Avoid** hardcoding paths in scripts:

```python
# WRONG - Hardcoded paths
input_path = "/opt/ml/processing/input/data"  # Hardcoded
output_path = "/opt/ml/processing/output/data"  # Hardcoded
```

**Correct** approach - use contract enforcer:

```python
# CORRECT - Use contract enforcer
contract = get_script_contract()
with ContractEnforcer(contract) as enforcer:
    input_path = enforcer.get_input_path("data")
    output_path = enforcer.get_output_path("output")
```

### Anti-Pattern: Missing Script Contract Validation

**Avoid** deploying scripts without contract validation:

```python
# WRONG - No validation
def main():
    # Process data without validation
    process_data()
```

**Correct** approach - validate contract:

```python
# CORRECT - Validate contract
def main():
    contract = get_script_contract()
    validation = contract.validate_implementation(__file__)
    if not validation.is_valid:
        raise RuntimeError(f"Contract validation failed: {validation.errors}")
    process_data()
```

## Conclusion

By adhering to these design principles, we create a robust, maintainable pipeline architecture that supports a wide range of machine learning workflows. When developing new steps, ensure your implementation follows these principles to maintain consistency and quality across the system.


-----------
##  Recommended Notes