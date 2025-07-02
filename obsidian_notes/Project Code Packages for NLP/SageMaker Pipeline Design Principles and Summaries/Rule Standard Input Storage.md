---
tags:
  - thought
  - aws/sagemaker_pipeline
  - design/standardization
aliases: 
date of note: 2025-07-01
---

## Input Storage Standard

The standardized input storage pattern consists of:

1. **Single Storage Location**: 
   - Inputs are stored only in the nested `kwargs['inputs']` dictionary
   - No more dual storage at both top-level and nested levels

2. **Normalization Requirement**:
   - All step builders must call `_normalize_inputs` as the first step in their `create_step` method
   - This flattens any nested structure and creates a consistent input format

3. **Top-Level Property Storage**:
   - Custom property matching (`_match_custom_properties`) stores all values at top-level:
     ```python
     inputs[key] = value  # Not inputs["inputs"][key]
     ```
   - Property tracking uses actual key names:
     ```python
     matched_inputs.add(key)  # Not matched_inputs.add("inputs")
     ```

4. **Post-Normalization Validation**:
   - Input validation happens *after normalization*
   - Input keys are *checked at top-level*:
     ```python
     if required_key not in inputs:  # After calling _normalize_inputs
         raise ValueError(f"Missing required input: {required_key}")
     ```


This standardized approach creates a clean contract between the pipeline template and step builders:

- **Pipeline Template**: Stores all inputs in the nested `kwargs['inputs']` dictionary
- **Step Builders**: Call `_normalize_inputs` to handle this nested structure
- **Result**: A consistent, predictable pattern throughout the codebase









-----------
##  Recommended Notes

- [[Strategy Pipeline Instantiation]]