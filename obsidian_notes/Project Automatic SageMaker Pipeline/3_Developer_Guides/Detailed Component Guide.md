---
tags:
  - project
  - documentation
  - aws/sagemaker_pipeline
aliases: 
date of note: 2025-07-16
---
This guide provides detailed information about the key components involved in creating a new pipeline step. Each component plays a specific role in the architecture, and understanding how they fit together is crucial for successful integration.

## Overview of Components

The pipeline architecture follows a specification-driven approach with a four-layer design:

1. **Step Specifications**: Define inputs and outputs with logical names [[Step Specification Design as Declarative Pipeline Architecture]]
2. **Script Contracts**: Define container paths for script inputs/outputs 
3. **Step Builders**: Connect specifications and contracts via SageMaker
4. **Processing Scripts**: Implement the actual business logic

## Component Relationships

The components are related as follows:

- **Processing Scripts** implement the actual business logic and are executed in SageMaker containers
- **Script Contracts** define the interface between scripts and the SageMaker environment
- **Step Specifications** define how steps connect with other steps in the pipeline
- **Step Builders** transform configurations and specifications into SageMaker steps

## Detailed Component Guides

For detailed guidance on developing each component, refer to the following sections:

- [Script Contract Development](Script%20Contract%20Development.md): How to create and validate script contracts
- [Step Specification Development](Step%20Specification%20Development.md): How to define step specifications for pipeline integration
- [Step Builder Implementation](Step%20Builder%20Implementation.md): How to implement the builder that creates SageMaker steps

## Component Alignment

The alignment between components is crucial for successful integration:

```
┌───────────────────┐          ┌───────────────────┐
│  Processing Script │◄────────┤  Script Contract  │
└─────────┬─────────┘          └────────┬──────────┘
          │                             │
          │                             │
          │                             │
┌─────────▼─────────┐          ┌───────▼──────────┐
│   Step Builder     │◄────────┤ Step Specification│
└───────────────────┘          └──────────────────┘
```

Alignment rules:
1. **Script to Contract Alignment**: The script must use exactly the paths defined in the contract
2. **Contract to Specification Alignment**: Contract input/output paths must have matching logical names in the specification
3. **Specification to Dependencies Alignment**: Step specification dependencies must match upstream steps' outputs
4. **Builder to Configuration Alignment**: Step builder must use configuration values correctly

## Validation and Testing

Each component should be validated:

1. **Script Contracts**: Validate against actual script implementation
2. **Step Specifications**: Validate property path consistency and contract alignment
3. **Step Builders**: Test input/output generation and environment variable handling
4. **Integration**: Test end-to-end integration with other steps

For more details on specific components, refer to the relevant sections linked above.

-----------
##  Recommended Notes