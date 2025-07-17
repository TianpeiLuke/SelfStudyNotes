---
tags:
  - thought
  - design/design_architecture
  - aws/sagemaker_pipeline
aliases: 
date of note: 2025-07-04
---

## What is the Purpose of Script Contract?

Script Contracts serve as the **execution bridge** between declarative Step Specifications and imperative script implementations. They provide explicit validation that scripts conform to their architectural specifications, eliminating the risk of runtime failures due to script-specification misalignment.

## Core Purpose

Script Contracts provide a **declarative way to define script execution requirements** and validate implementation compliance, enabling:

1. **Explicit I/O Validation** - Ensure scripts use expected input/output channels
2. **Runtime Environment Contracts** - Define and validate environment variable requirements
3. **Implementation Compliance** - Verify scripts match their specifications
4. **Development Safety** - Catch misalignments at build time, not runtime
5. **Documentation as Code** - Self-documenting script requirements

## Key Features

### 1. Input/Output Channel Contracts

Scripts explicitly declare their expected physical paths for logical channels:

```python
PREPROCESSING_SCRIPT_CONTRACT = ScriptContract(
    entry_point="tabular_preprocess.py",
    expected_input_paths={
        "DATA": "/opt/ml/processing/input/data",           # Required
        "METADATA": "/opt/ml/processing/input/metadata",   # Optional
        "SIGNATURE": "/opt/ml/processing/input/signature"  # Optional
    },
    expected_output_paths={
        "processed_data": "/opt/ml/processing/output"
    },
    required_env_vars=["LABEL_FIELD", "TRAIN_RATIO", "TEST_VAL_RATIO"],
    framework_requirements={"sklearn": ">=1.0.0", "pandas": ">=1.3.0"}
)
```

### 2. Environment Variable Contracts

Explicit declaration of required and optional environment variables:

```python
# Required environment variables that script must access
required_env_vars=["LABEL_FIELD", "TRAIN_RATIO", "TEST_VAL_RATIO"]

# Optional environment variables with defaults
optional_env_vars={
    "CATEGORICAL_COLUMNS": "",
    "NUMERICAL_COLUMNS": "",
    "DEBUG_MODE": "false"
}
```

### 3. Framework Dependency Contracts

Explicit declaration of framework and version requirements:

```python
framework_requirements={
    "sklearn": ">=1.0.0",
    "pandas": ">=1.3.0", 
    "xgboost": ">=1.6.0",
    "numpy": ">=1.21.0"
}
```

### 4. Implementation Validation

Automatic validation that scripts comply with their contracts:

```python
# Validate script implementation
validation = script_contract.validate_implementation("path/to/script.py")

if not validation.is_valid:
    raise ValueError(f"Script validation failed: {validation.errors}")
    # Errors might include:
    # - "Script doesn't use expected input path: /opt/ml/processing/input/data"
    # - "Script missing required env vars: ['LABEL_FIELD']"
    # - "Script uses undeclared input path: /opt/ml/processing/input/unknown"
```

## Integration with Step Specifications

Script Contracts extend existing Step Specifications without breaking changes:

```python
# Extend existing StepSpecification
@dataclass
class StepSpecification:
    # ... existing fields ...
    script_contract: Optional[ScriptContract] = None  # NEW: Optional addition
    
    def validate_script_compliance(self, script_path: str) -> ValidationResult:
        """Validate script matches specification"""
        if not self.script_contract:
            return ValidationResult.success("No script contract defined")
        return self.script_contract.validate_implementation(script_path)

# Enhanced specification with script contract
PREPROCESSING_SPEC = StepSpecification(
    step_type="TabularPreprocessing",
    node_type=NodeType.INTERNAL,
    dependencies=[...],  # Existing dependency specs
    outputs=[...],       # Existing output specs
    script_contract=PREPROCESSING_SCRIPT_CONTRACT  # NEW: Script execution contract
)
```

## Runtime Integration

### Specification-Aware Script Runtime

Scripts use runtime that validates against specifications:

```python
# Enhanced script structure
from src.pipeline_runtime.script_runtime import SpecificationAwareScriptRuntime

def main(job_type: str, label_field: str, train_ratio: float, test_val_ratio: float):
    # Initialize specification-aware runtime
    runtime = SpecificationAwareScriptRuntime("TabularPreprocessing")
    
    # Validate inputs using specification
    validation = runtime.validate_inputs()
    if not validation.is_valid:
        raise RuntimeError(f"Input validation failed: {validation.errors}")
    
    # Get input paths from specification (not hardcoded)
    data_path = runtime.get_input_path("DATA")
    metadata_path = runtime.get_input_path("METADATA")  # May be None if optional
    
    # Process data with validated inputs
    process_data(data_path, metadata_path)
```

### Step Builder Integration

Step builders validate script compliance during configuration:

```python
class TabularPreprocessingStepBuilder(StepBuilderBase):
    def validate_configuration(self) -> None:
        # Existing validation
        super().validate_configuration()
        
        # NEW: Validate script compliance
        script_path = self.config.get_script_path()
        validation = SpecificationRegistry.validate_script_compliance(
            "TabularPreprocessing", script_path
        )
        
        if not validation.is_valid:
            raise ValueError(f"Script validation failed: {validation.errors}")
```

## Problem Solved: Script-Specification Misalignment

### Before Script Contracts (Implicit, Fragile)

```python
# Script hardcodes paths - no validation
def main():
    # Implicit assumption about input location
    data_path = "/opt/ml/processing/input/data"  # Hardcoded
    
    # Implicit assumption about environment
    label_field = os.environ["LABEL_FIELD"]  # May not exist
    
    # No validation that inputs exist
    df = pd.read_csv(data_path)  # May fail at runtime
```

**Problems:**
- ❌ Runtime failures if paths don't match step builder configuration
- ❌ No validation that required inputs exist
- ❌ Implicit dependencies on environment variables
- ❌ No documentation of script requirements

### After Script Contracts (Explicit, Validated)

```python
# Script uses specification-aware runtime
def main():
    runtime = SpecificationAwareScriptRuntime("TabularPreprocessing")
    
    # Explicit validation before processing
    runtime.validate_inputs()  # Fails fast if inputs missing
    
    # Specification-driven path resolution
    data_path = runtime.get_input_path("DATA")  # From specification
    
    # Validated environment access
    label_field = runtime.get_env_var("LABEL_FIELD")  # Validated to exist
    
    # Safe processing with validated inputs
    df = pd.read_csv(data_path)
```

**Benefits:**
- ✅ Build-time validation prevents runtime failures
- ✅ Explicit documentation of script requirements
- ✅ Automatic validation that scripts match specifications
- ✅ Safe environment variable access
- ✅ Specification-driven path resolution

## Strategic Value

Script Contracts enable:

1. **Fail-Fast Validation**: Catch errors at build time, not runtime
2. **Explicit Documentation**: Script requirements are self-documenting
3. **Safe Refactoring**: Changes to specifications validate all implementations
4. **Development Confidence**: Developers know scripts will work if they pass validation
5. **Maintainability**: Clear contracts make scripts easier to understand and modify
6. **Interoperability**: Common interface for script validation across different frameworks

## Integration with Other Components

### With Step Specifications
Script Contracts extend [Step Specifications](Step%20Specification%20Development.md) with execution details.

### With Registry System
```python
# Validate all registered specifications have compliant scripts
for step_type in registry.get_all_step_types():
    validation = registry.validate_script_compliance(step_type, script_path)
    if not validation.is_valid:
        logger.error(f"Script compliance failed for {step_type}: {validation.errors}")
```

### With Step Builders
[Step Builders](Step%20Builder%20Implementation.md) use Script Contracts for validation and channel mapping.

## Example: Complete Integration

```python
# 1. Define script contract
EVAL_SCRIPT_CONTRACT = ScriptContract(
    entry_point="model_eval_xgb.py",
    expected_input_paths={
        "model_input": "/opt/ml/processing/input/model",
        "eval_data_input": "/opt/ml/processing/input/eval_data",
        "code_input": "/opt/ml/processing/input/code"
    },
    expected_output_paths={
        "eval_output": "/opt/ml/processing/output/eval",
        "metrics_output": "/opt/ml/processing/output/metrics"
    },
    required_env_vars=["ID_FIELD", "LABEL_FIELD"],
    framework_requirements={"xgboost": ">=1.6.0", "sklearn": ">=1.0.0"}
)

# 2. Extend specification
MODEL_EVAL_SPEC = StepSpecification(
    step_type="XGBoostModelEvaluation",
    node_type=NodeType.INTERNAL,
    dependencies=[...],
    outputs=[...],
    script_contract=EVAL_SCRIPT_CONTRACT  # Add contract
)

# 3. Enhanced script
def main():
    runtime = SpecificationAwareScriptRuntime("XGBoostModelEvaluation")
    runtime.validate_inputs()
    
    model_path = runtime.get_input_path("model_input")
    eval_data_path = runtime.get_input_path("eval_data_input")
    
    # Safe processing with validated inputs
    evaluate_model(model_path, eval_data_path)
```

Script Contracts bridge the gap between **architectural intent** ([Step Specifications](Step%20Specification%20Development.md)) and **implementation reality** (actual scripts), ensuring they remain aligned throughout the development lifecycle.








-----------
##  Recommended Notes

- [[Step Specification Design as Declarative Pipeline Architecture]]
- [[Specification Registry Design]]
- [[Registry Manager Design]]