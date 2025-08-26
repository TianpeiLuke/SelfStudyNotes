---
tags:
  - code
  - code_snippet
  - aws/sagemaker_pipeline
  - amazon/mods_pipeline
keywords: 
topics: 
language: python
date of note: 2025-07-16
---

## Code Snippet Summary

>[!important]
>The **PropertyReference** class is a critical component that bridges between *definition-time specifications* and *runtime property references* in the SageMaker pipeline context. 
>- It provides a way to lazily evaluate references to properties of pipeline steps, enabling the *automatic wiring* of pipeline steps based on specifications rather than manual coding.


## Code

### Class Definition

```python
class PropertyReference(BaseModel):
    """Lazy evaluation reference bridging definition-time and runtime."""
    
    model_config = ConfigDict(
        validate_assignment=True,
        arbitrary_types_allowed=True
    )
    
    step_name: str = Field(
        ...,
        description="Name of the step that produces this output",
        min_length=1
    )
    output_spec: OutputSpec = Field(
        ...,
        description="Output specification for the referenced output"
    )
```

## Key Design Choices

### 1. Definition-Time vs. Runtime Bridging

>[!important]
> The primary purpose of PropertyReference is to bridge between two worlds:
> 
> 1. **Definition Time**: When the pipeline is being constructed and only specifications are available
> 2. **Runtime**: When the pipeline is executing and actual SageMaker step instances exist
> 
> This bridging enables the core capability of the specification-driven dependency resolution system: resolving dependencies based on specifications, but using them to create actual SageMaker property references at runtime.

### 2. Pydantic Integration

>[!info]
> PropertyReference is implemented as a Pydantic model, which provides several benefits:
> 
> - **Validation**: Automatic validation of inputs at creation time
> - **Serialization**: Easy serialization/deserialization for storage or transmission
> - **Type Safety**: Strong typing for better IDE support and fewer runtime errors
> - **Field Documentation**: Self-documenting field descriptions

### 3. Property Path Parsing

>[!important]
>The class contains sophisticated **property path parsing logic** to handle the complex structure of *SageMaker property references*:

```python
def _parse_property_path(self, path: str) -> List[Union[str, Tuple[str, str]]]:
    """
    Parse a property path into a sequence of access operations.
    
    This method handles various property path formats, including:
    - Regular attribute access: "properties.ProcessingOutputConfig"
    - Dictionary access: "Outputs['DATA']"
    - Combined access: "properties.ProcessingOutputConfig.Outputs['DATA']"
    
    Args:
        path: Property path as a string
        
    Returns:
        List of access operations, where each operation is either:
        - A string for attribute access
        - A tuple (attr_name, key) for dictionary access
    """
    # Remove "properties." prefix if present
    if path.startswith("properties."):
        path = path[11:]  # Remove "properties."
    
    result = []
    
    # Improved pattern to match dictionary access like: 
    # Outputs['DATA'] or Outputs["DATA"] or Outputs[0]
    dict_pattern = re.compile(r'(\w+)\[([\'"]?)([^\]\'\"]+)\2\]')
    
    # Split by dots first, but preserve quoted parts
    parts = []
    current = ""
    in_brackets = False
    bracket_depth = 0
    
    for char in path:
        if char == '.' and not in_brackets:
            if current:
                parts.append(current)
                current = ""
        elif char == '[':
            in_brackets = True
            bracket_depth += 1
            current += char
        elif char == ']':
            bracket_depth -= 1
            if bracket_depth == 0:
                in_brackets = False
            current += char
        else:
            current += char
    
    if current:
        parts.append(current)
    
    # Process each part
    for part in parts:
        # Check if this part contains dictionary access
        dict_match = dict_pattern.match(part)
        if dict_match:
            # Extract the attribute name and key
            attr_name = dict_match.group(1)
            quote_type = dict_match.group(2)  # This will be ' or " or empty
            key = dict_match.group(3)
            
            # Handle numeric indices
            if not quote_type and key.isdigit():
                key = int(key)
                
            # Add a tuple for dictionary access
            result.append((attr_name, key))
        else:
            # Regular attribute access
            result.append(part)
    
    return result
```

>[!info]
>This parsing logic is capable of handling complex nested property references with both *attribute access (dot notation)* and *dictionary/list access (bracket notation)*.


### 4. Runtime Property Navigation

>[!important]
>Once the property path is parsed, the class provides a method to **navigate** through the actual objects at **runtime**:

```python
def _get_property_value(self, obj: Any, path_parts: List[Union[str, Tuple[str, str]]]) -> Any:
    """
    Navigate through the property path to get the final value.
    
    Args:
        obj: The object to start navigation from
        path_parts: List of path parts from _parse_property_path
        
    Returns:
        The value at the end of the property path
        
    Raises:
        AttributeError: If any part of the path is invalid
        ValueError: If a path part has an invalid format
    """
    current_obj = obj
    
    # Navigate through each part of the path
    for part in path_parts:
        if isinstance(part, str):
            # Regular attribute access
            current_obj = getattr(current_obj, part)
        elif isinstance(part, tuple) and len(part) == 2:
            # Dictionary access with [key]
            attr_name, key = part
            if attr_name:  # If there's an attribute before the bracket
                current_obj = getattr(current_obj, attr_name)
            # Handle the key access
            if isinstance(key, int) or (isinstance(key, str) and key.isdigit()):  
                # Array index - convert string digits to int if needed
                idx = key if isinstance(key, int) else int(key)
                current_obj = current_obj[idx]
            else:  # Dictionary key
                current_obj = current_obj[key]
        else:
            raise ValueError(f"Invalid path part: {part}")
    
    return current_obj
```

>[!info]
>This method handles both attribute access and dictionary/list access with proper error handling.

### 5. SageMaker Integration

>[!important]
>The class provides methods to convert **property references** to **SageMaker-compatible formats**:

```python
def to_sagemaker_property(self) -> Dict[str, str]:
    """Convert to SageMaker Properties dictionary format at pipeline definition time."""
    # Get the property path without 'properties.' prefix
    property_path = self.output_spec.property_path
    if property_path.startswith('properties.'):
        property_path = property_path[11:]
    
    return {"Get": f"Steps.{self.step_name}.{property_path}"}

def to_runtime_property(self, step_instances: Dict[str, Any]) -> Any:
    """
    Create an actual SageMaker property reference using step instances.
    
    This method navigates the property path to create a proper SageMaker
    Properties object that can be used at runtime.
    
    Args:
        step_instances: Dictionary mapping step names to step instances
        
    Returns:
        SageMaker Properties object for the referenced property
        
    Raises:
        ValueError: If the step is not found or property path is invalid
        AttributeError: If any part of the property path is invalid
    """
    if self.step_name not in step_instances:
        raise ValueError(f"Step '{self.step_name}' not found in step instances. Available steps: {list(step_instances.keys())}")
    
    # Get the step instance
    step_instance = step_instances[self.step_name]
    
    # Parse and navigate the property path
    path_parts = self._parse_property_path(self.output_spec.property_path)
    
    # Use helper method to navigate property path
    return self._get_property_value(step_instance.properties, path_parts)
```

These methods support both pipeline definition time (using a dictionary format) and runtime (using actual SageMaker Properties objects).

## Usage Patterns

### Creation by Dependency Resolver

>[!important]
>PropertyReference objects are typically created by the **dependency resolver** during the *resolution process*:

```python
# In UnifiedDependencyResolver._resolve_single_dependency:
if confidence > 0.5:  # Threshold for viable candidates
    prop_ref = PropertyReference(
        step_name=provider_step,
        output_spec=output_spec
    )
    candidates.append((prop_ref, confidence, provider_step, output_name))
```

- [[Dependency Resolver for Automatic Pipeline]]
### Usage in PipelineAssembler

>[!important]
>The **PipelineAssembler** uses PropertyReference objects to create *actual SageMaker property references*:

```python
# In PipelineAssembler._instantiate_step:
if output_spec:
    try:
        # Create a PropertyReference object
        prop_ref = PropertyReference(
            step_name=src_step,
            output_spec=output_spec
        )
        
        # Use the enhanced to_runtime_property method to get a SageMaker Properties object
        runtime_prop = prop_ref.to_runtime_property(self.step_instances)
        inputs[input_name] = runtime_prop
    except Exception as e:
        # Fallback handling...
```

- [[Pipeline Assembler for Automatic Pipeline]]
## Error Handling and Fallbacks

The PropertyReference implementation includes robust error handling:

```python
# In PipelineAssembler._instantiate_step:
try:
    # Create a PropertyReference object
    prop_ref = PropertyReference(
        step_name=src_step,
        output_spec=output_spec
    )
    
    # Use the enhanced to_runtime_property method to get a SageMaker Properties object
    runtime_prop = prop_ref.to_runtime_property(self.step_instances)
    inputs[input_name] = runtime_prop
    
    logger.debug(f"Created runtime property reference for {step_name}.{input_name} -> {src_step}.{output_spec.property_path}")
except Exception as e:
    # Log the error and fall back to a safe string
    logger.warning(f"Error creating runtime property reference: {str(e)}")
    s3_uri = f"s3://pipeline-reference/{src_step}/{src_output}"
    inputs[input_name] = s3_uri
    logger.warning(f"Using S3 URI fallback: {s3_uri}")
```

This ensures that even if property resolution fails, the pipeline can still be created with placeholder values.

## String Representation

PropertyReference objects provide both string and representation methods for debugging:

```python
def __str__(self) -> str:
    return f"{self.step_name}.{self.output_spec.logical_name}"

def __repr__(self) -> str:
    return f"PropertyReference(step='{self.step_name}', output='{self.output_spec.logical_name}')"
```

## Example Usage

```python
# Create an output specification
model_output = OutputSpec(
    logical_name="model_output",
    output_type=DependencyType.MODEL_ARTIFACTS,
    property_path="properties.ModelArtifacts.S3ModelArtifacts",
    data_type="S3Uri"
)

# Create a property reference
prop_ref = PropertyReference(
    step_name="training_step",
    output_spec=model_output
)

# At definition time, get SageMaker property dictionary
sagemaker_prop = prop_ref.to_sagemaker_property()
print(sagemaker_prop)  # {"Get": "Steps.training_step.ModelArtifacts.S3ModelArtifacts"}

# At runtime, with step instances available
step_instances = {"training_step": training_step_instance}
runtime_prop = prop_ref.to_runtime_property(step_instances)
# This returns the actual SageMaker property object
```

## Integration with Step Specifications

>[!important]
>The PropertyReference class integrates with the **step specification system** through the **OutputSpec class**:

- [[Base Step Specification OutputSpec]]
- [[Base Step Specification]]

```python
# In the StepSpecification class:
def get_output_by_name_or_alias(self, name: str) -> Optional[OutputSpec]:
    """
    Get output specification by logical name or alias.
    
    Args:
        name: The logical name or alias to search for
        
    Returns:
        OutputSpec if found, None otherwise
    """
    # First try exact logical name match
    if name in self.outputs:
        return self.outputs[name]
    
    # Then search through aliases (case-insensitive)
    name_lower = name.lower()
    for output_spec in self.outputs.values():
        for alias in output_spec.aliases:
            if alias.lower() == name_lower:
                return output_spec
    
    return None
```

This allows property references to be created from both logical names and aliases.

- [[Base Step Specification]]


-----------
##  Recommended Notes


- [[Step Specification Design as Declarative Pipeline Architecture]]
- [[Specification Registry Design]]
- [[Config-Driven vs Specification-Driven Design]]
- [[Amazon SageMaker Step Dependencies]]

- SageMaker Python SDK 
	- [data-dependency-property-reference](https://sagemaker.readthedocs.io/en/v2.92.2/amazon_sagemaker_model_building_pipeline.html#data-dependency-property-reference)

- API Reference 
	- [DescribeTrainingJob](https://docs.aws.amazon.com/sagemaker/latest/APIReference/API_DescribeTrainingJob.html#sagemaker-DescribeTrainingJob-response-OutputDataConfig)
	- [API_OutputDataConfig](https://docs.aws.amazon.com/sagemaker/latest/APIReference/API_OutputDataConfig.html)