---
tags:
  - code
  - code_snippet
  - prompt
  - llm
  - cline_coding_agent
  - claude_llm
  - large_language_models
keywords: 
topics: 
language: python
date of note: 2025-07-01
---

## Code Snippet Summary

>[!important]


## Code

```markdown
Prompt Template for SageMaker Pipeline Development

Objective: To develop, debug, and refactor SageMaker pipelines and their components (configurations, step builders) following established best practices and standardization rules.

---

### Part 1: Key Design Principles

Remember to adhere to these core principles throughout the coding process:

- **Single Source of Truth**: All validation logic and configuration definitions should be centralized in their respective component's configuration class. This avoids redundancy and conflicts.
    
- **Explicit Over Implicit**: Always favor explicit connections and parameter passing between pipeline steps. Avoid relying on implicit, automatic matching based on naming conventions, as this is less robust and more error-prone.
    
- **Standardized Interfaces**: Follow the "Standard Pattern" for how step builders manage inputs and outputs. This is crucial for a modular, predictable, and maintainable pipeline framework.
    
- **Separation of Concerns**: The pipeline builder's main role is orchestration. The specifics of configuration and I/O should be handled by the individual step builders.
    
- **Defensive Programming**: Anticipate potential runtime issues and build in mechanisms to handle them gracefully. Examples include the **Property Path Registry** and **safe logging utilities**.
    
- **Robust Scripting for Refactoring**: When performing codebase-wide changes like renaming directories or updating references, use a script. This is more reliable and less error-prone than manual changes.
    

---

### Part 2: Standardization Rules for the Universal Pipeline

Follow these rules strictly when creating or modifying pipeline components:

#### A. Configuration (`input_names` and `output_names`)

1. **`output_names`**: In a step's configuration, this should be a dictionary mapping a `logical_name` to a `DescriptiveValue`. The **`DescriptiveValue`** should be used as the key in the `outputs` dictionary passed to the next step.
    
    - _Example_: `output_names = {"processed_data": "ProcessedTabularData"}`
        
2. **`input_names`**: In a step's configuration, this should be a dictionary mapping a `logical_name` to a `ScriptInputName`. The **`logical_name` (the KEY)** should be used as the key in the `inputs` dictionary when a step receives input. The **VALUE** of the `output_names` of the previous step should match the **KEY** of the `input_names` of the current step.
    
    - _Example_: `input_names = {"ModelArtifacts": "model_input"}`
        

#### B. Pipeline Code (Connecting Steps)

1. To get an output from a preceding step, use the **`DescriptiveValue`** from its `output_names` to access the output URI.
    
2. To set an input for a subsequent step, use the **`logical_name` (the KEY)** from its `input_names`.
    

#### C. Step Builder Implementation

1. When **validating outputs**, the builder should check for the presence of the **`DescriptiveValue`** from `output_names` in the `outputs` dictionary.
    
2. When **validating inputs**, the builder should check for the presence of the **`logical_name` (the KEY)** from `input_names` in the `inputs` dictionary.
    
3. If a configuration field is optional, the builder must handle the `None` case gracefully, either by providing a default value in a validator or by having conditional logic to handle its absence.
    
4. The validation logic within a builder's `validate_configuration` method must be consistent with the fields defined in its corresponding configuration and with the implementation of the builder's other methods.
    

---

### Part 3: Instructions from Pain Points (Lessons Learned)

This is a list of "lessons learned" that will help you avoid common errors:

- **Handling Different Step Outputs**: Be aware that different step types have different property access patterns. For example:
    
    - `ProcessingStep`: `properties.ProcessingOutputConfig.Outputs[name].S3Output.S3Uri`
        
    - `LambdaStep`: `properties.Outputs[name]`
        
    - `TrainingStep`: `properties.ModelArtifacts.S3ModelArtifacts`
        
- **Input Auto-Detection**: Training steps should be able to auto-detect their inputs from their dependencies if no inputs are explicitly provided. This will avoid a `ValueError: inputs must be provided` error.
    
- **Handling `PropertiesList`**: Never use `len()` on a `PropertiesList` object. Iterate through it or access known properties directly.
    
- **Avoiding Redundant Validation**: The config class is the single source of truth for validation. Do not duplicate validation logic in the pipeline builder.
    
- **Using Exact Type Checks for Configs**: When dealing with inherited config classes, use `type()` instead of `isinstance()` to ensure the correct class is matched.
    
- **Safe Logging**: Always use the safe logging utility for Pipeline Variables to avoid `TypeError`s.
    
- **Path Normalization**: Ensure all S3 paths are normalized to remove trailing slashes to prevent errors from double slashes (`//`).
    
- **Empty Container Arguments**: If a processing step does not require any container arguments, provide a dummy argument (`["--dummy-arg"]`) to avoid a `ValidationException`.
```





-----------
##  Recommended Notes

