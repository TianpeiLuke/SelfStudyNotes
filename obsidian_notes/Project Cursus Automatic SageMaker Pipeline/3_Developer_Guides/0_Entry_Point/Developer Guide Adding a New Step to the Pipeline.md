---
tags:
  - entry_point
  - documentation
  - code_package
  - amazon/mods_pipeline
  - aws/sagemaker
aliases: 
keywords: 
topics: 
language: python
date of note: 2025-07-12
name: "Developer Guide: Adding a New Step to the Pipeline"
version: "3.0"
year: 2025
---

## Overview

>[!quote]
>This guide provides a standardized procedure for adding a new step to the pipeline system. Following these guidelines ensures that your implementation maintains consistency with the existing code structure and adheres to our design principles.

>[!important]
> Our pipeline architecture follows a specification-driven approach with a four-layer design:
> 
> 1. **Step Specifications**: Define inputs and outputs with logical names
> 2. **Script Contracts**: Define container paths for script inputs/outputs
> 3. **Step Builders**: Connect specifications and contracts via SageMaker
> 4. **Processing Scripts**: Implement the actual business logic

## Table of Contents

1. [[Prerequisites for Adding a New Pipeline Step]]
2. [[Step Creation Process]]
3. [[Detailed Component Guide]]
   - [[Script Contract Development]]
   - [Step Specification Development](Step%20Specification%20Development.md)
   - [Step Builder Implementation](Step%20Builder%20Implementation.md)
1. [[Design Principles]]
2. [[Best Practices]]
3. [[Standardization Rules]]
4. [Common Pitfalls to Avoid](Common%20Pitfalls%20to%20Avoid.md)
5. [[Alignment Rules]]
6. [Example](Example%20Adding%20a%20Feature%20Selection%20Step.md)
7. [[Validation Checklist]]

## Quick Start

>[!info]
> To add a new step to the pipeline:
> 
> 1. Review the [Prerequisites for Adding a New Pipeline Step](Prerequisites%20for%20Adding%20a%20New%20Pipeline%20Step.md) to ensure you have all required information
> 2. Follow the [step creation process](Step%20Creation%20Process.md) to implement all required components
> 3. Validate your implementation using the [validation checklist](Validation%20Checklist.md)
> 
> For detailed guidance on specific components, refer to the relevant sections in the [detailed component guide](Detailed%20Component%20Guide.md).



-----------
##  Recommended Notes


- [Specification-Driven Architecture](../pipeline_design/specification_driven_design.md)
- [Hybrid Design](../pipeline_design/hybrid_design.md)
- [Script-Specification Alignment](../project_planning/script_specification_alignment_prevention_plan.md)
- [Script Contract](../pipeline_design/script_contract.md)
- [Step Specification](../pipeline_design/step_specification.md)
