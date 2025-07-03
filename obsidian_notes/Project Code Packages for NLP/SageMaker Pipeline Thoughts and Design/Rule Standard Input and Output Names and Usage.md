---
tags:
  - thought
  - design_principles
  - amazon/mods_pipeline
  - aws/sagemaker_pipeline
  - design
aliases: 
date of note: 2025-07-01
---
## Standard Pattern for Input / Output Names


> [!important]
> Standard Pattern for `input_names` and `output_names`:
>     
> 1. In **config classes**:
> ```python
> output_names = {"logical_name": "DescriptiveValue"}  # VALUE used as key in outputs dict
> 
> input_names = {"logical_name": "ScriptInputName"}    # KEY used as key in inputs dict
> ```
>     
> 2. In **pipeline code**:
>        
> ```python
> # Get output using VALUE from output_names
> output_value = step_a.config.output_names["logical_name"]
> output_uri = step_a.properties.ProcessingOutputConfig.Outputs[output_value].S3Output.S3Uri
>        
> # Set input using KEY from input_names
> inputs = {"logical_name": output_uri}
> ```
>     
> 3. In **step builders**:
> ```python
> # For outputs - validate using VALUES
> value = self.config.output_names["logical_name"]
> if value not in outputs:
>     raise ValueError(f"Must supply an S3 URI for '{value}'")
>            
> # For inputs - validate using KEYS
> for logical_name in self.config.input_names.keys():
>     if logical_name not in inputs:
>         raise ValueError(f"Must supply an S3 URI for '{logical_name}'")
> ```










-----------
##  Recommended Notes