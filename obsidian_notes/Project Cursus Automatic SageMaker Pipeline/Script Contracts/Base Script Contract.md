---
tags:
  - code
  - code_snippet
  - amazon/mods_pipeline
  - aws/sagemaker_pipeline
keywords: 
topics: 
language: python
date of note: 2025-07-16
---

## Code Snippet Summary

>[!important]
>The **Base Script Contract** provides the foundational data structures and validation framework for *defining* and *enforcing explicit I/O* and *environment requirements* for **pipeline scripts**. 
>- It enables **fail-fast validation** by catching configuration errors at build time rather than runtime.


## Code

### ValidationResult

>[!important]
>Represents the outcome of script contract validation with detailed error and warning information.

```python
class ValidationResult(BaseModel):
    """Result of script contract validation"""
    is_valid: bool
    errors: List[str] = Field(default_factory=list)
    warnings: List[str] = Field(default_factory=list)
```

#### Factory Methods

```python
# Success result
result = ValidationResult.success("Validation passed")

# Error result
result = ValidationResult.error(["Missing input path", "Invalid env var"])

# Combine multiple results
combined = ValidationResult.combine([result1, result2, result3])
```

- [[Design Pattern Factory Method Pattern]]

### ScriptContract

>[!important]
>The core **contract class** that defines explicit requirements for *script execution*.

```python
class ScriptContract(BaseModel):
    """Script execution contract that defines explicit I/O and environment requirements"""
    entry_point: str = Field(..., description="Script entry point filename")
    expected_input_paths: Dict[str, str] = Field(..., description="Mapping of logical names to expected input paths")
    expected_output_paths: Dict[str, str] = Field(..., description="Mapping of logical names to expected output paths")
    required_env_vars: List[str] = Field(..., description="List of required environment variables")
    optional_env_vars: Dict[str, str] = Field(default_factory=dict, description="Optional environment variables with defaults")
    framework_requirements: Dict[str, str] = Field(default_factory=dict, description="Framework version requirements")
    description: str = Field(default="", description="Human-readable description of the script")
```

## Usage Examples

### Creating a Script Contract
```python
from src.pipeline_script_contracts.base_script_contract import ScriptContract

# Define a processing script contract
preprocessing_contract = ScriptContract(
    entry_point="tabular_preprocess.py",
    expected_input_paths={
        "raw_data": "/opt/ml/processing/input/data",
        "metadata": "/opt/ml/processing/input/metadata"
    },
    expected_output_paths={
        "processed_data": "/opt/ml/processing/output/data",
        "feature_stats": "/opt/ml/processing/output/stats"
    },
    required_env_vars=["LABEL_FIELD", "TRAIN_RATIO"],
    optional_env_vars={
        "RANDOM_SEED": "42",
        "VALIDATION_RATIO": "0.2"
    },
    framework_requirements={
        "pandas": ">=1.3.0",
        "scikit-learn": ">=1.0.0"
    },
    description="Tabular data preprocessing with feature engineering"
)
```

### Validating Script Implementation
```python
# Validate a script against its contract
validation_result = preprocessing_contract.validate_implementation("src/pipeline_scripts/tabular_preprocess.py")

if validation_result.is_valid:
    print("✅ Script complies with contract")
else:
    print("❌ Script validation failed:")
    for error in validation_result.errors:
        print(f"  - {error}")
    
    if validation_result.warnings:
        print("Warnings:")
        for warning in validation_result.warnings:
            print(f"  - {warning}")
```

### Combining Validation Results
```python
# Validate multiple aspects and combine results
path_validation = validate_paths(script)
env_validation = validate_environment(script)
framework_validation = validate_frameworks(script)

# Combine all validation results
overall_result = ValidationResult.combine([
    path_validation,
    env_validation,
    framework_validation
])

print(f"Overall validation: {'PASS' if overall_result.is_valid else 'FAIL'}")
```

## Validation Framework

### Path Validation
The contract enforces SageMaker-specific path conventions:

```python
@field_validator('expected_input_paths')
@classmethod
def validate_input_paths(cls, v: Dict[str, str]) -> Dict[str, str]:
    """Validate input paths are absolute SageMaker paths"""
    for logical_name, path in v.items():
        if not path.startswith('/opt/ml/processing/input'):
            raise ValueError(f'Input path for {logical_name} must start with /opt/ml/processing/input, got: {path}')
    return v
```

#### Valid Path Examples
```python
# ✅ Valid input paths
valid_inputs = {
    "training_data": "/opt/ml/processing/input/data/train.csv",
    "validation_data": "/opt/ml/processing/input/data/val.csv",
    "config": "/opt/ml/processing/input/config/params.json"
}

# ✅ Valid output paths
valid_outputs = {
    "processed_data": "/opt/ml/processing/output/data/processed.csv",
    "model_artifacts": "/opt/ml/processing/output/model/model.pkl",
    "metrics": "/opt/ml/processing/output/metrics/metrics.json"
}

# ❌ Invalid paths (will raise validation error)
invalid_inputs = {
    "data": "/tmp/data.csv",  # Not SageMaker path
    "config": "config.json"   # Not absolute path
}
```

### Entry Point Validation
```python
@field_validator('entry_point')
@classmethod
def validate_entry_point(cls, v: str) -> str:
    """Validate entry point is a Python file"""
    if not v.endswith('.py'):
        raise ValueError('Entry point must be a Python file (.py)')
    return v
```

## Script Analysis Framework

### ScriptAnalyzer

>[!important]
>Analyzes Python scripts using **AST (Abstract Syntax Tree) parsing** to extract I/O patterns and environment variable usage.

```python
class ScriptAnalyzer:
    """Analyzes Python scripts to extract I/O patterns and environment variable usage"""
    
    def __init__(self, script_path: str):
        self.script_path = script_path
        
    def get_input_paths(self) -> Set[str]:
        """Extract input paths used by the script"""
        
    def get_output_paths(self) -> Set[str]:
        """Extract output paths used by the script"""
        
    def get_env_var_usage(self) -> Set[str]:
        """Extract environment variables accessed by the script"""
```

### AST Pattern Detection

#### Input/Output Path Detection
```python
# Detects patterns like:
input_path = "/opt/ml/processing/input/data"
df = pd.read_csv("/opt/ml/processing/input/data/train.csv")
output_dir = "/opt/ml/processing/output/model"
```

#### Environment Variable Detection
```python
# Detects patterns like:
label_field = os.environ["LABEL_FIELD"]
batch_size = os.environ.get("BATCH_SIZE", "32")
seed = os.getenv("RANDOM_SEED", 42)
```

### Analysis Examples
```python
from src.pipeline_script_contracts.base_script_contract import ScriptAnalyzer

# Analyze a script
analyzer = ScriptAnalyzer("src/pipeline_scripts/tabular_preprocess.py")

# Extract usage patterns
input_paths = analyzer.get_input_paths()
output_paths = analyzer.get_output_paths()
env_vars = analyzer.get_env_var_usage()

print(f"Input paths found: {input_paths}")
print(f"Output paths found: {output_paths}")
print(f"Environment variables used: {env_vars}")

# Example output:
# Input paths found: {'/opt/ml/processing/input/data', '/opt/ml/processing/input/metadata'}
# Output paths found: {'/opt/ml/processing/output/data', '/opt/ml/processing/output/stats'}
# Environment variables used: {'LABEL_FIELD', 'TRAIN_RATIO', 'RANDOM_SEED'}
```

## Contract Validation Process

### Validation Steps

>[!important]
> 1. **File Existence Check** - Verify script file exists
> 2. **AST Parsing** - Parse script into Abstract Syntax Tree
> 3. **Path Analysis** - Extract input/output path usage
> 4. **Environment Analysis** - Extract environment variable usage
> 5. **Contract Comparison** - Compare actual usage vs. contract requirements
> 6. **Result Generation** - Create detailed validation report

### Validation Logic
```python
def _validate_against_analysis(self, analyzer: ScriptAnalyzer) -> ValidationResult:
    """Validate contract against script analysis"""
    errors = []
    warnings = []
    
    # Validate input paths
    script_input_paths = analyzer.get_input_paths()
    for logical_name, expected_path in self.expected_input_paths.items():
        if expected_path not in script_input_paths:
            errors.append(f"Script doesn't use expected input path: {expected_path} (for {logical_name})")
    
    # Check for unexpected input paths
    expected_paths = set(self.expected_input_paths.values())
    unexpected_paths = script_input_paths - expected_paths
    for path in unexpected_paths:
        if path.startswith("/opt/ml/processing/input"):
            warnings.append(f"Script uses undeclared input path: {path}")
    
    # Validate output paths
    script_output_paths = analyzer.get_output_paths()
    for logical_name, expected_path in self.expected_output_paths.items():
        if expected_path not in script_output_paths:
            errors.append(f"Script doesn't use expected output path: {expected_path} (for {logical_name})")
    
    # Validate environment variables
    script_env_vars = analyzer.get_env_var_usage()
    missing_env_vars = set(self.required_env_vars) - script_env_vars
    if missing_env_vars:
        errors.append(f"Script missing required environment variables: {list(missing_env_vars)}")
    
    return ValidationResult(
        is_valid=len(errors) == 0,
        errors=errors,
        warnings=warnings
    )
```

## Advanced Features

### Lazy AST Loading

>[!important]
>The **ScriptAnalyzer** uses **lazy loading** for *efficient memory usage*:

```python
@property
def ast_tree(self):
    """Lazy load and parse the script AST"""
    if self._ast_tree is None:
        with open(self.script_path, 'r') as f:
            content = f.read()
        self._ast_tree = ast.parse(content)
    return self._ast_tree
```

### Caching Analysis Results

>[!important]
>Analysis results are cached to *avoid* **redundant AST parsing**:

```python
def get_input_paths(self) -> Set[str]:
    """Extract input paths used by the script"""
    if self._input_paths is None:
        self._input_paths = self._analyze_input_paths()
    return self._input_paths
```

### Complex Pattern Detection

>[!important]
>The analyzer handles various *Python patterns* for *accessing* **paths** and **environment variables**:

```python
# String literals
"/opt/ml/processing/input/data"

# os.path.join calls
os.path.join("/opt/ml/processing/input", "data", "train.csv")

# Environment variable access patterns
os.environ["VAR_NAME"]
os.environ.get("VAR_NAME", "default")
os.getenv("VAR_NAME", default_value)
```

## Error Handling

### Validation Errors
```python
# Handle script file not found
if not os.path.exists(script_path):
    return ValidationResult.error([f"Script file not found: {script_path}"])

# Handle AST parsing errors
try:
    analyzer = ScriptAnalyzer(script_path)
    return self._validate_against_analysis(analyzer)
except Exception as e:
    return ValidationResult.error([f"Error analyzing script: {str(e)}"])
```

### Pydantic Validation Errors

```python
# Invalid entry point
try:
    contract = ScriptContract(entry_point="script.txt")  # Not .py file
except ValidationError as e:
    print(f"Contract validation failed: {e}")

# Invalid paths
try:
    contract = ScriptContract(
        entry_point="script.py",
        expected_input_paths={"data": "/tmp/data"}  # Not SageMaker path
    )
except ValidationError as e:
    print(f"Path validation failed: {e}")
```

## Best Practices

### 1. Contract Design

>[!important]
> - Use descriptive logical names for inputs/outputs
> - Include all required environment variables
> - Specify framework versions explicitly
> - Provide clear descriptions

### 2. Path Conventions

>[!important]
> - Always use absolute SageMaker paths
> - Follow consistent directory structures
> - Use logical names that match script functionality

### 3. Environment Variables

>[!important]
> - List all required environment variables
> - Provide sensible defaults for optional variables
> - Use descriptive variable names

### 4. Validation Strategy

>[!important]
> - Validate contracts during CI/CD pipeline
> - Run validation before deployment
> - Address warnings to maintain code quality

- [[Continuous Integration or CI in DevOps and MLOps]]
- [[Continuous Delivery or CD in DevOps and MLOps]]

## Integration Points

### With Step Specifications
```python
@dataclass
class StepSpecification:
    script_contract: Optional[ScriptContract] = None
    
    def validate_script_compliance(self, script_path: str) -> ValidationResult:
        if self.script_contract:
            return self.script_contract.validate_implementation(script_path)
        return ValidationResult.success("No contract defined")
```

### With Pipeline Builders
```python
class ProcessingStepBuilder:
    def validate_script(self, script_path: str) -> None:
        if hasattr(self, 'contract'):
            result = self.contract.validate_implementation(script_path)
            if not result.is_valid:
                raise ValueError(f"Script validation failed: {result.errors}")
```

## Performance Considerations

### AST Parsing

>[!important]
> - AST parsing is performed once per script and cached
> - Large scripts may take longer to parse
> - Consider pre-parsing for frequently validated scripts

### Memory Usage

>[!important]
> - AST trees are stored in memory during analysis
> - Clear analyzer instances after validation to free memory
> - Use lazy loading to minimize memory footprint

### Validation Speed

>[!important]
> - Path validation is fast (string operations)
> - Environment variable detection requires AST traversal
> - Batch validation is more efficient than individual validations



-----------
##  Recommended Notes

- [[Script Contract Design]]
- [[Step Specification Design as Declarative Pipeline Architecture]]

- [[Base Step Specification]]