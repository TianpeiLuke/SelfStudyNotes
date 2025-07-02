---
tags:
  - thought
  - aws/sagemaker_pipeline
  - design_principles
  - design/standardization
aliases: 
date of note: 2025-07-01
---


After examining all step builders involved in the pipeline, I've identified the exact patterns causing the inconsistency issue. Here's a detailed breakdown of how each step builder handles inputs:

## 1. Pipeline Builder Template - Source of Dual Storage

In `pipeline_builder_template.py`, the `_instantiate_step` method creates dual storage:

```python
# Add to top-level kwargs for backward compatibility
kwargs[input_name] = output_value
# Also add to inputs dictionary for newer steps
kwargs['inputs'][input_name] = output_value
```

This creates values in both places, expecting step builders to handle them properly.

## 2. Input Normalization Usage By Step

| Step Builder         | Uses `_normalize_inputs`                  | Storage Location in `_match_custom_properties`      | Validation Location             |     |
| -------------------- | ----------------------------------------- | --------------------------------------------------- | ------------------------------- | --- |
| CradleDataLoading    | N/A (no inputs)                           | N/A                                                 | N/A                             |     |
| TabularPreprocessing | ✅ Yes, in `create_step`                   | ✅ Top-level: `inputs[input_key] = value`            | ✅ Top-level                     |     |
| XGBoostTraining      | ✅ Yes, in `create_step`                   | ✅ Top-level                                         | ✅ Top-level                     |     |
| MIMSPackaging        | ✅ Yes, in `create_step`                   | ✅ Top-level: `inputs[model_input_key] = model_uri`  | ✅ Top-level                     |     |
| MIMSPayload          | ✅ Yes, in `create_step`                   | ❌ Nested: `inputs["inputs"][model_key] = model_uri` | ✅ Top-level                     |     |
| ModelRegistration    | ❌ No, missing in `_get_processing_inputs` | ❌ Nested: `inputs["inputs"][payload_key] = s3_uri`  | ❌ Top-level without normalizing |     |


## 3. Critical Issues Identified

1. __Payload Step__:

   - Uses `_normalize_inputs` correctly in `create_step`

   - But in `_match_custom_properties`, it stores matched values in nested structure:

     ```python
     inputs["inputs"][model_key] = model_uri
     ```

2. __Registration Step__: Has multiple problems:

   - Doesn't call `_normalize_inputs` in `_get_processing_inputs`

   - Stores matches in nested structure in `_match_custom_properties`:

     ```python
     inputs["inputs"][payload_key] = s3_uri
     ```

   - But validates at top level in `_get_processing_inputs` without normalizing first:

     ```python
     if payload_sample_key not in inputs:
         raise ValueError(...)
     ```

3. The error occurs specifically because:

   - __Pipeline template__ puts payload data in both places initially
   - __Payload step__ when matching stores it in nested structure
   - __Registration step__ looks for it at top level without normalizing

## 4. Clear Pattern for Solution

1. __Standardize all step builders__:

   - Always call `_normalize_inputs` in `create_step` AND in `_get_processing_inputs`
   - Store all matched values at top-level in `_match_custom_properties`

2. __Fix Registration Step__:

   - Add normalization in `_get_processing_inputs`
   - Change storage pattern in `_match_custom_properties` to use top-level

3. __Fix Payload Step__:

   - Change storage pattern in `_match_custom_properties` to use top-level

Most step builders (TabularPreprocessing, XGBoostTraining, MIMSPackaging) follow the correct pattern. Only MIMSPayload and ModelRegistration have issues, with ModelRegistration having the most severe problems causing the error.










-----------
##  Recommended Notes