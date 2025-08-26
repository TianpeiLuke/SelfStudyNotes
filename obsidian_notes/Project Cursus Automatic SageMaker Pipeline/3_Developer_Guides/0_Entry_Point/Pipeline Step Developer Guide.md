---
tags:
  - entry_point
  - aws/sagemaker_pipeline
aliases: 
date of note: 2025-07-16
---
This directory contains comprehensive documentation for developing new steps in our SageMaker-based ML pipeline architecture. The guide is designed to help both new and experienced developers create pipeline steps that align with our architectural patterns and best practices.

## Guide Structure

The developer guide is organized into several interconnected documents:

### Main Documentation

- **[Adding a New Pipeline Step](Developer%20Guide%20Adding%20a%20New%20Step%20to%20the%20Pipeline.md)** - The main entry point providing an overview of the step development process

### Process Documentation

- **[Prerequisites](Prerequisites%20for%20Adding%20a%20New%20Pipeline%20Step.md)** - What you need before starting development
- **[Creation Process](Step%20Creation%20Process.md)** - Step-by-step process for adding a new pipeline step

### Component Documentation

- **[Component Guide](Detailed%20Component%20Guide.md)** - Overview of the key components and their relationships
- **[Script Contract Development](Script%20Contract%20Development.md)** - Detailed guide for developing script contracts
- **[Step Specification Development](Step%20Specification%20Development.md)** - Detailed guide for developing step specifications
- **[Step Builder Implementation](Step%20Builder%20Implementation.md)** - Detailed guide for implementing step builders

### Best Practices and Guidelines

- **[Design Principles](Design%20Principles.md)** - Core design principles to follow
- **[Best Practices](Best%20Practices.md)** - Recommended best practices for development
- **[Standardization Rules](Standardization%20Rules.md)** - Enhanced architectural constraints for universal patterns
- **[Common Pitfalls](Common%20Pitfalls%20to%20Avoid.md)** - Common mistakes to avoid
- **[Alignment Rules](Alignment%20Rules.md)** - Centralized alignment guidance across scripts, specifications, and builders
- **[Validation Checklist](Validation%20Checklist.md)** - Comprehensive checklist for validating implementations

### Examples

- **[Example Implementation](Example%20Adding%20a%20Feature%20Selection%20Step.md)** - Complete example of adding a new pipeline step

## Quick Start Summary

**New to pipeline development?** Follow this rapid orientation:

1. **Understand the Architecture**: Four layers work together - Scripts → Contracts → Specifications → Builders
2. **Check Prerequisites**: Ensure you have step requirements and understand the business logic
3. **Follow the Process**: Register step → Create config → Develop contract → Build specification → Implement builder → Test
4. **Key Decision Points**:
   - What inputs/outputs does your step need?
   - What SageMaker step type (Processing, Training, Transform)?
   - What job type variants (training, calibration, validation)?
5. **Essential Files to Create**:
   - `config_your_step.py` (configuration)
   - `your_step_contract.py` (script contract)
   - `your_step_spec.py` (step specification)
   - `builder_your_step.py` (step builder)
6. **Validation**: Use alignment rules and validation checklist before integration

**Experienced developers?** Jump to [Creation Process](Step%20Creation%20Process.md) for the step-by-step procedure.

## Recommended Reading Order

For new developers, we recommend the following reading order:

1. Start with **[Adding a New Pipeline Step](Developer%20Guide%20Adding%20a%20New%20Step%20to%20the%20Pipeline.md)** for an overview
2. Check **[Prerequisites](Prerequisites%20for%20Adding%20a%20New%20Pipeline%20Step.md)** to ensure you have everything needed
3. Review the **[Creation Process](Step%20Creation%20Process.md)** for the step-by-step procedure
4. Read the **[Component Guide](Detailed%20Component%20Guide.md)** to understand component relationships
5. Dive deeper into specific component documentation:
   - **[Script Contract Development](Script%20Contract%20Development.md)**
   - **[Step Specification Development](Step%20Specification%20Development.md)**
   - **[Step Builder Implementation](Step%20Builder%20Implementation.md)**
6. Study the **[Example Implementation](Example%20Adding%20a%20Feature%20Selection%20Step.md)** to see how everything fits together
7. Review best practices and guidelines:
   - **[Design Principles](Design%20Principles.md)**
   - **[Best Practices](Best%20Practices.md)**
   - **[Common Pitfalls](Common%20Pitfalls%20to%20Avoid.md)**
8. Use the **[Validation Checklist](Validation%20Checklist.md)** to verify your implementation

## Key Architectural Concepts

Our pipeline architecture follows a specification-driven approach with a four-layer design:

1. **Step Specifications**: Define inputs and outputs with logical names
2. **Script Contracts**: Define container paths for script inputs/outputs
3. **Step Builders**: Connect specifications and contracts via SageMaker
4. **Processing Scripts**: Implement the actual business logic

Understanding these layers and their relationships is crucial for successful step development.

## Using AI to Assist Development

For guidance on using Claude v3 to assist with pipeline step development, see the AI prompt templates in the [../developer_prompts](../developer_prompts) directory.

## Getting Help

If you encounter issues or have questions while developing a new pipeline step:

1. Consult the **[Common Pitfalls](Common%20Pitfalls%20to%20Avoid.md)** document
2. Use the **[Validation Checklist](Validation%20Checklist.md)** to identify potential issues
3. Review the **[Example Implementation](Example%20Adding%20a%20Feature%20Selection%20Step.md)** for reference
4. Reach out to the architecture team for assistance

## Contributing to the Guide

If you identify gaps in the documentation or have suggestions for improvements:

1. Document your proposed changes
2. Discuss with the architecture team
3. Update the relevant documentation
4. Ensure consistency across all documents

The developer guide is a living document that evolves with our architecture.


-----------
##  Recommended Notes