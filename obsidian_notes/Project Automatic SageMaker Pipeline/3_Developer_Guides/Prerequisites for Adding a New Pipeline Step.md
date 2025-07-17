---
tags:
  - project
  - design
  - documentation
  - aws/sagemaker_pipeline
aliases: 
date of note: 2025-07-16
---
Before you begin developing a new pipeline step, ensure you have gathered all the necessary information and have a clear understanding of the system. This preparation will significantly streamline the development process and help prevent common integration issues.

## Required Inputs

### 1. Task Description

Clearly define what your step will do:

- **Purpose**: What business or technical problem does this step solve?
- **Input Requirements**: What data does your step need to function?
- **Expected Outputs**: What will your step produce?
- **Pipeline Position**: Where does this step fit in the overall pipeline flow?
- **Success Criteria**: How will you know if the step is working correctly?

### 2. Processing Script

Ensure you have a working script that implements the core functionality:

- **Implementation**: A functional script that processes inputs and generates outputs
- **Error Handling**: Comprehensive error handling and logging
- **Unit Tests**: Tests that verify the script's functionality in isolation
- **Path Documentation**: Clear documentation of all input/output paths used
- **Environment Variables**: List of all environment variables the script accesses

### 3. Step Identification

Define the step's identity within the pipeline system:

- **Canonical Name**: Choose a name following our conventions (e.g., `TabularPreprocessing`)
- **Step Type**: Determine if this is a processing, training, source, or sink step
- **Job Type Variants**: Consider if you need variants for training, calibration, validation, etc.
- **Logical Names**: Define logical input and output names for semantic matching

### 4. SageMaker Component Type

Identify which SageMaker component will be used to implement the step:

- **ProcessingStep**: For data processing operations
- **TrainingStep**: For model training operations
- **Model**: For model artifact packaging
- **Transform**: For batch transformation operations
- **Other**: Any specialized step type needed for your use case

## Understanding Existing Components

Before implementing your new step, familiarize yourself with:

### 1. Key Documentation

Review these documents to understand our architecture:

- [Specification-Driven Architecture](../pipeline_design/specification_driven_design.md)
- [Hybrid Design](../pipeline_design/hybrid_design.md)
- [Script-Specification Alignment](../project_planning/script_specification_alignment_prevention_plan.md)
- [Script Contract](../pipeline_design/script_contract.md)
- [Step Specification](../pipeline_design/step_specification.md)

### 2. Similar Existing Steps

Study implementations similar to your planned step:

- For processing steps, review `TabularPreprocessingStepBuilder`
- For training steps, review `XGBoostTrainingStepBuilder`
- For model steps, review `XGBoostModelStepBuilder`
- For registration steps, review `ModelRegistrationStepBuilder`

### 3. Pipeline Flow

Understand how your step will connect with others:

- **Upstream Steps**: Identify steps that will provide inputs to your step
- **Downstream Steps**: Identify steps that will consume outputs from your step
- **Dependency Contracts**: Review the logical names used in connected steps
- **Data Flow**: Understand the data formats passed between steps

## Checklist Before Starting

✅ I have a clear task description with defined inputs and outputs  
✅ My processing script is functional and well-tested  
✅ I've chosen appropriate step and node types  
✅ I've identified the correct SageMaker component to use  
✅ I've reviewed the key documentation on our architecture  
✅ I've studied similar existing step implementations  
✅ I understand which steps will connect to my new step  
✅ I've identified all logical names for cross-step connections  
✅ I've documented all environment variables needed by my script  
✅ I've validated my script's input/output path conventions

Once you've completed this preparation, proceed to the [Step Creation Process](Step%20Creation%20Process.md).


-----------
##  Recommended Notes