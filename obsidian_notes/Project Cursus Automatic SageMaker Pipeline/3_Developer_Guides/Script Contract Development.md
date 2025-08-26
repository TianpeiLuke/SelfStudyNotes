---
tags:
  - project
  - design/design_architecture
  - aws/sagemaker_pipeline
  - documentation
aliases: 
date of note: 2025-07-16
---

Script contracts are a critical component of our pipeline architecture. They define the interface between your processing script and the SageMaker container environment, ensuring proper alignment between the script implementation and the pipeline infrastructure.

## Purpose of Script Contracts

Script contracts serve several important purposes:

1. **Explicit Documentation**: They clearly document the input/output paths and environment variables required by the script
2. **Build-time Validation**: They enable validation of script-specification alignment before pipeline execution
3. **Runtime Safety**: They provide runtime enforcement of required environment variables and paths
4. **Developer Guidance**: They guide script authors on expected interfaces and requirements

## Contract Structure

A script contract is defined using the `ScriptContract` class and includes the following key components:

```python
from pydantic import BaseModel
from typing import Dict, List, Optional

from .base_script_contract import ScriptContract

YOUR_SCRIPT_CONTRACT = ScriptContract(
    entry_point="your_script.py",
    expected_input_paths={
        "input_data": "/opt/ml/processing/input/data",
        "input_metadata": "/opt/ml/processing/input/metadata"
    },
    expected_output_paths={
        "output_data": "/opt/ml/processing/output/data",
        "output_metadata": "/opt/ml/processing/output/metadata"
    },
    required_env_vars=[
        "REQUIRED_PARAM_1",
        "REQUIRED_PARAM_2"
    ],
    optional_env_vars={
        "OPTIONAL_PARAM_1": "default_value",
    },
    framework_requirements={
        "pandas": ">=1.3.0",
        "numpy": ">=1.20.0",
    },
    description="Your script's purpose and functionality description"
)
```

### Critical Fields in Script Contract

| Field | Critical? | Description | How to Find |
|-------|----------|-------------|-------------|
| `entry_point` | ✅ Required | Script filename | Look at your script's filename |
| `expected_input_paths` | ✅ Required | Container paths for inputs | Analyze script for input file paths |
| `expected_output_paths` | ✅ Required | Container paths for outputs | Analyze script for output file paths |
| `required_env_vars` | ✅ Required | Environment variables needed | Analyze script for `os.environ` usage |
| `optional_env_vars` | Optional | Env vars with defaults | Look for fallback values in script |
| `framework_requirements` | Recommended | Dependencies with versions | Check imports and requirements.txt |
| `description` | Recommended | Purpose of the script | Write based on script functionality |

## How to Develop a Script Contract

### 1. Analyze Your Script

The first step is to analyze your script to identify:

- **Input Paths**: Where the script expects to find input data
- **Output Paths**: Where the script writes output data
- **Environment Variables**: What environment variables the script accesses
- **Framework Dependencies**: What libraries the script imports

#### Input/Output Path Detection

Look for code patterns like:

```python
# Direct path references
input_path = "/opt/ml/processing/input/data"
output_path = "/opt/ml/processing/output/results"

# Path construction
input_dir = os.path.join("/opt/ml/processing/input", "data")

# File operations
with open("/opt/ml/processing/input/config.json", "r") as f:
    # Reading input
with open("/opt/ml/processing/output/results.csv", "w") as f:
    # Writing output
```

#### Environment Variable Detection

Look for patterns like:

```python
# Direct access
label_field = os.environ["LABEL_FIELD"]

# Access with default
normalize = os.environ.get("NORMALIZE", "True").lower() == "true"

# Alternative access
debug_mode = os.getenv("DEBUG_MODE", "False") == "True"
```

### 2. Follow SageMaker Path Conventions

Adhere to SageMaker's path conventions:

- **Processing Inputs**: `/opt/ml/processing/input/{logical_name}`
- **Processing Outputs**: `/opt/ml/processing/output/{logical_name}`
- **Training Inputs**: `/opt/ml/input/data/{channel_name}`
- **Model Outputs**: `/opt/ml/model`

### 3. Be Aware of Directory Creation Behavior

SageMaker automatically creates directories for paths specified in:
- `ProcessingInput` (at the `destination` path)
- `ProcessingOutput` (at the `source` path)

This can cause issues if your script expects to create a file at a path where SageMaker has already created a directory. For file outputs, either:
1. Specify the parent directory in the contract, or
2. Generate files with dynamic names within the specified directory

### 4. Create the Script Contract

Define your contract in a new file:

```python
# src/pipeline_script_contracts/your_script_contract.py
from .base_script_contract import ScriptContract

YOUR_SCRIPT_CONTRACT = ScriptContract(
    entry_point="your_script.py",
    expected_input_paths={
        # Use logical names as keys
        "input_data": "/opt/ml/processing/input/data",  # Full path as value
    },
    expected_output_paths={
        # Use logical names as keys
        "output_data": "/opt/ml/processing/output/data",  # Full path as value
    },
    required_env_vars=[
        # List required environment variables
        "PARAM_1",
    ],
    # Other fields...
)
```

### 5. Align Logical Names with Step Specification

The logical names used as keys in your contract must match:
- The dependency logical names in your step specification
- The output logical names in your step specification

This alignment is critical for the specification-driven approach to work correctly.

## Script-to-Contract Alignment

### Contract-Aware Script Pattern

For maximum safety, consider updating your script to use the contract at runtime:

```python
# your_script.py
import os
import logging

def get_script_contract():
    """Get the contract for this script."""
    from ..pipeline_script_contracts.your_script_contract import YOUR_SCRIPT_CONTRACT
    return YOUR_SCRIPT_CONTRACT

def main():
    # Get and validate contract
    contract = get_script_contract()
    
    # Access paths using contract
    input_data_path = contract.expected_input_paths["input_data"]
    output_data_path = contract.expected_output_paths["output_data"]
    
    # Rest of your script...

if __name__ == "__main__":
    main()
```

### Contract Enforcer Pattern

For advanced validation, use the contract enforcer pattern:

```python
# your_script.py
import os
from src.pipeline_script_contracts.contract_utils import ContractEnforcer

def get_script_contract():
    from ..pipeline_script_contracts.your_script_contract import YOUR_SCRIPT_CONTRACT
    return YOUR_SCRIPT_CONTRACT

def main():
    contract = get_script_contract()
    
    with ContractEnforcer(contract) as enforcer:
        # All paths and environment variables are validated
        input_path = enforcer.get_input_path("input_data")
        output_path = enforcer.get_output_path("output_data")
        
        # Process data...

if __name__ == "__main__":
    main()
```

## Contract Validation

### Automated Validation

We have tools to validate script contract compliance:

```python
from src.pipeline_script_contracts import ScriptContractValidator

# Validate a script against its contract
validator = ScriptContractValidator('src/pipeline_scripts')
report = validator.validate_script('your_script.py')

if not report.is_compliant:
    print("Errors:", report.errors)
    print("Missing inputs:", report.missing_inputs)
    print("Missing outputs:", report.missing_outputs)
```

### Common Validation Issues

1. **Missing Input/Output Paths**: The script uses paths not declared in the contract
2. **Undeclared Environment Variables**: The script accesses environment variables not declared in the contract
3. **Directory/File Path Conflicts**: The script tries to create a file where SageMaker creates a directory
4. **Path Construction Issues**: Path construction logic in the script doesn't match the contract

## Contract Examples

### Processing Script Contract

```python
PREPROCESSING_CONTRACT = ScriptContract(
    entry_point="preprocess.py",
    expected_input_paths={
        "raw_data": "/opt/ml/processing/input/data",
        "config": "/opt/ml/processing/input/config"
    },
    expected_output_paths={
        "processed_data": "/opt/ml/processing/output/data",
        "metadata": "/opt/ml/processing/output/metadata"
    },
    required_env_vars=[
        "LABEL_COLUMN",
        "TARGET_SIZE"
    ],
    optional_env_vars={
        "DEBUG_MODE": "False",
        "RANDOM_SEED": "42"
    },
    framework_requirements={
        "pandas": ">=1.3.0",
        "scikit-learn": ">=1.0.0"
    }
)
```

### Training Script Contract

```python
TRAINING_CONTRACT = ScriptContract(
    entry_point="train.py",
    expected_input_paths={
        "training_data": "/opt/ml/input/data/train",
        "validation_data": "/opt/ml/input/data/validation",
        "hyperparameters": "/opt/ml/input/config/hyperparameters.json"
    },
    expected_output_paths={
        "model": "/opt/ml/model",
        "metrics": "/opt/ml/output/metrics"
    },
    required_env_vars=[
        "NUM_EPOCHS",
        "LEARNING_RATE"
    ],
    framework_requirements={
        "tensorflow": "==2.8.0",
        "numpy": ">=1.20.0"
    }
)
```

## Best Practices

1. **Use Explicit Logical Names**: Choose descriptive logical names for inputs/outputs
2. **Maintain 1:1 Alignment**: Ensure each input/output path in the script has a corresponding entry in the contract
3. **Validate Early**: Use the validation tools during development, not just at integration time
4. **Document Requirements**: Use the contract to document all requirements for script execution
5. **Consider File vs. Directory**: Be careful about path handling for file outputs
6. **Avoid Hardcoding**: Use the contract paths in the script instead of hardcoding paths
7. **Test Contract Compliance**: Include contract compliance in unit tests

By following these guidelines, your script contracts will provide a robust interface between your processing scripts and the pipeline infrastructure.



-----------
##  Recommended Notes

- [[Script Contract Design]]
- [[Base Script Contract]]