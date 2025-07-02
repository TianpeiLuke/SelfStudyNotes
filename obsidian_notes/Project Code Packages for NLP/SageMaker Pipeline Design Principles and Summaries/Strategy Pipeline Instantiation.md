---
tags:
  - thought
  - aws/sagemaker_pipeline
  - design/standardization
aliases: 
date of note: 2025-07-01
---

## Input Storage Standard

- [[Rule Standard Input Storage]]

## Pipeline _instantiate_step Strategy

The pipeline template's `_instantiate_step` method now follows a consistent strategy:

1. **Single Nested Storage**:
   - Inputs are stored only in the nested dictionary:
     ```python
     kwargs['inputs'][input_name] = output_value
     ```
   - No more storage at top-level (`kwargs[input_name]`)

2. **Property Path Resolution**:
   - When resolving property paths, outputs are stored only in inputs dictionary:
     ```python
     output_value = self._resolve_property_path(source_step_instance, path)
     if output_value is not None:
         kwargs['inputs'][input_name] = output_value  # Only nested storage
     ```

3. **Direct Attribute Access**:
   - When accessing attributes directly, they're stored only in inputs dictionary:
     ```python
     if hasattr(source_step_instance, source_output):
         output_value = getattr(source_step_instance, source_output)
         kwargs['inputs'][input_name] = output_value  # Only nested storage
     ```

4. **Explicit Comment Documentation**:
   - Comments clarify that step builders normalize inputs:
     ```python
     # Store only in the inputs dictionary - all step builders now normalize with _normalize_inputs
     ```

This standardized approach creates a clean contract between the pipeline template and step builders:

- **Pipeline Template**: Stores all inputs in the nested `kwargs['inputs']` dictionary
- **Step Builders**: Call `_normalize_inputs` to handle this nested structure
- **Result**: A consistent, predictable pattern throughout the codebase









-----------
##  Recommended Notes