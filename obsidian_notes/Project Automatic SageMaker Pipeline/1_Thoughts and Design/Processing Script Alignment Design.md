---
tags:
  - thought
  - design/design_architecture
aliases: 
date of note: 2025-07-04
---

Excellent point! You're absolutely right - there's significant redundancy with the existing specification system. Let me redesign this to **extend and enhance** the current architecture rather than duplicate it.

# 🔄 **Reusing Existing Specification Design**

## **Current Architecture Analysis**

Looking at your existing system:
- `StepSpecification` already defines dependencies and outputs
- `SpecificationRegistry` already manages step specifications  
- `DependencySpec` and `OutputSpec` already capture I/O contracts
- Step builders already use specifications for validation

## **Enhanced Architecture: Extending Current Design**

### 1. **Extend StepSpecification with Script Contract**

```python
# src/pipeline_deps/base_specifications.py (extend existing)
@dataclass
class StepSpecification:
    # ... existing fields ...
    
    # NEW: Script execution contract
    script_contract: Optional['ScriptContract'] = None
    
    def validate_script_compliance(self, script_path: str) -> ValidationResult:
        """Validate script matches specification"""
        if not self.script_contract:
            return ValidationResult.success("No script contract defined")
            
        return self.script_contract.validate_implementation(script_path)

@dataclass  
class ScriptContract:
    """Script-specific execution details"""
    entry_point: str
    expected_input_paths: Dict[str, str]  # logical_name -> expected_path
    expected_output_paths: Dict[str, str]  # logical_name -> expected_path
    required_env_vars: List[str]
    framework_requirements: Dict[str, str]
    
    def validate_implementation(self, script_path: str) -> ValidationResult:
        """Validate script implementation matches contract"""
        analyzer = ScriptAnalyzer(script_path)
        
        # Check input path usage
        script_inputs = analyzer.get_input_paths()
        for logical_name, expected_path in self.expected_input_paths.items():
            if expected_path not in script_inputs:
                return ValidationResult.error(f"Script doesn't use expected input path: {expected_path}")
        
        # Check environment variable usage
        script_env_vars = analyzer.get_env_var_usage()
        missing_env_vars = set(self.required_env_vars) - script_env_vars
        if missing_env_vars:
            return ValidationResult.error(f"Script missing required env vars: {missing_env_vars}")
            
        return ValidationResult.success("Script complies with contract")
```

### 2. **Enhance SpecificationRegistry with Script Validation**

```python
# src/pipeline_deps/specification_registry.py (extend existing)
class SpecificationRegistry:
    # ... existing methods ...
    
    def validate_script_compliance(self, step_type: str, script_path: str) -> ValidationResult:
        """Validate script against its specification"""
        spec = self.get_specification(step_type)
        if not spec:
            return ValidationResult.error(f"No specification found for {step_type}")
            
        return spec.validate_script_compliance(script_path)
    
    def get_script_channel_mapping(self, step_type: str) -> Dict[str, str]:
        """Get logical to physical channel mapping for a step"""
        spec = self.get_specification(step_type)
        if not spec or not spec.script_contract:
            return {}
            
        return spec.script_contract.expected_input_paths
```

### 3. **Script Runtime Using Existing Specifications**

```python
# src/pipeline_runtime/script_runtime.py (NEW)
class SpecificationAwareScriptRuntime:
    """Runtime that uses existing StepSpecification system"""
    
    def __init__(self, step_type: str):
        self.step_type = step_type
        self.spec = SpecificationRegistry.get_specification(step_type)
        if not self.spec:
            raise RuntimeError(f"No specification found for {step_type}")
        
        self.channel_mapping = self._build_channel_mapping()
    
    def _build_channel_mapping(self) -> Dict[str, str]:
        """Build channel mapping from specification"""
        mapping = {}
        
        # Map dependencies to input paths
        for dep in self.spec.dependencies:
            logical_name = dep.logical_name
            # Use script contract if available, otherwise use default path
            if self.spec.script_contract and logical_name in self.spec.script_contract.expected_input_paths:
                mapping[logical_name] = self.spec.script_contract.expected_input_paths[logical_name]
            else:
                mapping[logical_name] = f"/opt/ml/processing/input/{logical_name.lower()}"
        
        return mapping
    
    def get_input_path(self, logical_name: str) -> str:
        """Get physical path for logical input"""
        if logical_name not in self.channel_mapping:
            raise ValueError(f"Unknown input channel: {logical_name}")
        
        path = self.channel_mapping[logical_name]
        if not os.path.exists(path):
            # Check if it's optional
            dep = next((d for d in self.spec.dependencies if d.logical_name == logical_name), None)
            if dep and not dep.required:
                return None
            raise RuntimeError(f"Required input path not found: {path}")
        
        return path
    
    def validate_inputs(self) -> ValidationResult:
        """Validate all required inputs exist"""
        errors = []
        
        for dep in self.spec.dependencies:
            if dep.required:
                path = self.get_input_path(dep.logical_name)
                if not path or not os.path.exists(path):
                    errors.append(f"Missing required input: {dep.logical_name}")
        
        return ValidationResult.success() if not errors else ValidationResult.error(errors)
```

### 4. **Enhanced Step Specifications with Script Contracts**

```python
# src/pipeline_step_specs/preprocessing_spec.py (extend existing)
from ..pipeline_deps.base_specifications import ScriptContract

# Add script contract to existing specification
PREPROCESSING_SCRIPT_CONTRACT = ScriptContract(
    entry_point="tabular_preprocess.py",
    expected_input_paths={
        "DATA": "/opt/ml/processing/input/data",
        "METADATA": "/opt/ml/processing/input/metadata",  # Optional
        "SIGNATURE": "/opt/ml/processing/input/signature"  # Optional
    },
    expected_output_paths={
        "processed_data": "/opt/ml/processing/output"
    },
    required_env_vars=["LABEL_FIELD", "TRAIN_RATIO", "TEST_VAL_RATIO"],
    framework_requirements={"sklearn": ">=1.0.0", "pandas": ">=1.3.0"}
)

# Extend existing specification
PREPROCESSING_SPEC = StepSpecification(
    # ... existing fields ...
    script_contract=PREPROCESSING_SCRIPT_CONTRACT  # NEW
)
```

### 5. **Enhanced Step Builders with Script Validation**

```python
# src/pipeline_steps/builder_tabular_preprocessing_step.py (extend existing)
class TabularPreprocessingStepBuilder(StepBuilderBase):
    # ... existing methods ...
    
    def validate_configuration(self) -> None:
        """Enhanced validation including script compliance"""
        # Existing validation
        super().validate_configuration()
        
        # NEW: Validate script compliance
        script_path = self.config.get_script_path()
        validation = SpecificationRegistry.validate_script_compliance(
            "TabularPreprocessing", script_path
        )
        
        if not validation.is_valid:
            raise ValueError(f"Script validation failed: {validation.errors}")
    
    def _get_processor_inputs(self, inputs: Dict[str, Any]) -> List[ProcessingInput]:
        """Enhanced input processing using specification"""
        # Get channel mapping from specification
        channel_mapping = SpecificationRegistry.get_script_channel_mapping("TabularPreprocessing")
        
        processing_inputs = []
        
        # Use specification to determine required vs optional inputs
        for dep in self.spec.dependencies:
            logical_name = dep.logical_name
            
            if dep.required and logical_name not in inputs:
                raise ValueError(f"Missing required input: {logical_name}")
            
            if logical_name in inputs:
                # Get expected path from script contract
                expected_path = channel_mapping.get(logical_name, f"/opt/ml/processing/input/{logical_name.lower()}")
                
                processing_inputs.append(
                    ProcessingInput(
                        source=inputs[logical_name],
                        destination=expected_path,
                        input_name=self.config.input_names[logical_name]
                    )
                )
        
        return processing_inputs
```

### 6. **Updated Scripts Using Specification Runtime**

```python
# dockers/xgboost_atoz/pipeline_scripts/tabular_preprocess_v2.py
from src.pipeline_runtime.script_runtime import SpecificationAwareScriptRuntime

def main(job_type: str, label_field: str, train_ratio: float, test_val_ratio: float, 
         input_base_dir: str, output_dir: str):
    """Enhanced main function using specification runtime"""
    
    # Initialize specification-aware runtime
    runtime = SpecificationAwareScriptRuntime("TabularPreprocessing")
    
    # Validate inputs using specification
    validation = runtime.validate_inputs()
    if not validation.is_valid:
        raise RuntimeError(f"Input validation failed: {validation.errors}")
    
    # Get input paths from specification
    data_path = runtime.get_input_path("DATA")
    metadata_path = runtime.get_input_path("METADATA")  # May be None if optional
    signature_path = runtime.get_input_path("SIGNATURE")  # May be None if optional
    
    # Process data (existing logic)
    df = combine_shards(data_path)
    
    # Handle optional metadata
    if metadata_path:
        logger.info(f"Processing metadata from {metadata_path}")
        # Process metadata...
    
    # Continue with existing processing logic...
    # ... rest of existing main() function
```

## **Benefits of This Approach**

✅ **Reuses Existing Architecture**: Extends `StepSpecification` and `SpecificationRegistry`
✅ **Minimal Changes**: Adds script contracts without breaking existing code  
✅ **Backward Compatible**: Existing specifications work without script contracts
✅ **Incremental Adoption**: Can add script contracts step by step
✅ **Leverages Existing Validation**: Uses current dependency/output validation
✅ **Consistent**: Uses same patterns as existing specification system

## **Implementation Priority**

1. **Phase 1**: Add `ScriptContract` to `StepSpecification` (non-breaking)
2. **Phase 2**: Enhance one step specification with script contract (tabular preprocessing)
3. **Phase 3**: Create `SpecificationAwareScriptRuntime` 
4. **Phase 4**: Update one script to use runtime (proof of concept)
5. **Phase 5**: Gradually migrate other steps

This approach leverages your existing investment in the specification system while adding the explicit script validation you need. Would you like me to focus on any specific phase or component?








-----------
##  Recommended Notes