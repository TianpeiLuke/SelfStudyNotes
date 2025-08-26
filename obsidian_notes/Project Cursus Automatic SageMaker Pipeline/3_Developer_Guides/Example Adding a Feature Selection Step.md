---
tags:
  - project
  - documentation
  - design_principles
  - aws/sagemaker_pipeline
aliases: 
date of note: 2025-07-16
---
This document provides a complete example of adding a new step to the pipeline. We'll implement a `FeatureSelectionStep` that selects the most important features from preprocessed data.

## Step Overview

Our new step will:
1. Take preprocessed data as input
2. Select the most important features using various methods (correlation, mutual information, etc.)
3. Output the reduced feature set and feature importance metadata

This step will fit between data preprocessing and model training in the pipeline.

## Prerequisites

First, let's ensure we have all the required information:

- **Task Description**: A step that selects the most important features from preprocessed data
- **Processing Script**: `feature_selection.py` script that implements the feature selection logic
- **Step Name**: `FeatureSelection`
- **Node Type**: `INTERNAL` (has both inputs and outputs)
- **SageMaker Component Type**: `ProcessingStep`

## Step 1: Create the Script Contract

First, let's create the script contract that defines the interface between our script and the SageMaker container environment.

**File**: `src/pipeline_script_contracts/feature_selection_contract.py`

```python
from .base_script_contract import ScriptContract

FEATURE_SELECTION_CONTRACT = ScriptContract(
    entry_point="feature_selection.py",
    expected_input_paths={
        "input_data": "/opt/ml/processing/input/data",
        "config": "/opt/ml/processing/input/config"
    },
    expected_output_paths={
        "selected_features": "/opt/ml/processing/output/features",
        "feature_importance": "/opt/ml/processing/output/importance"
    },
    required_env_vars=[
        "SELECTION_METHOD",
        "N_FEATURES",
        "TARGET_COLUMN"
    ],
    optional_env_vars={
        "MIN_IMPORTANCE": "0.01",
        "RANDOM_SEED": "42",
        "DEBUG_MODE": "False"
    },
    framework_requirements={
        "pandas": ">=1.3.0",
        "scikit-learn": ">=1.0.0",
        "numpy": ">=1.20.0"
    },
    description="Contract for feature selection script that reduces feature dimensionality"
)
```

## Step 2: Create the Step Specification

Now, let's create the step specification that defines how our step connects with other steps in the pipeline.

**File**: `src/pipeline_step_specs/feature_selection_spec.py`

```python
from typing import Dict, List, Optional

from ..pipeline_deps.base_specifications import StepSpecification, NodeType, DependencySpec, OutputSpec, DependencyType
from ..pipeline_registry.step_names import get_spec_step_type

def _get_feature_selection_contract():
    """Get the script contract for this step."""
    from ..pipeline_script_contracts.feature_selection_contract import FEATURE_SELECTION_CONTRACT
    return FEATURE_SELECTION_CONTRACT

FEATURE_SELECTION_SPEC = StepSpecification(
    step_type=get_spec_step_type("FeatureSelection"),
    node_type=NodeType.INTERNAL,
    script_contract=_get_feature_selection_contract(),
    dependencies={
        "input_data": DependencySpec(
            logical_name="input_data",
            dependency_type=DependencyType.PROCESSING_OUTPUT,
            required=True,
            compatible_sources=["TabularPreprocessing", "DataLoading"],
            semantic_keywords=["data", "processed", "tabular", "features"],
            data_type="S3Uri",
            description="Preprocessed tabular data for feature selection"
        ),
        "config": DependencySpec(
            logical_name="config",
            dependency_type=DependencyType.PROCESSING_OUTPUT,
            required=False,
            compatible_sources=["ConfigGeneration", "DataLoading"],
            semantic_keywords=["config", "parameters", "settings"],
            data_type="S3Uri",
            description="Optional configuration for feature selection"
        )
    },
    outputs={
        "selected_features": OutputSpec(
            logical_name="selected_features",
            output_type=DependencyType.PROCESSING_OUTPUT,
            property_path="properties.ProcessingOutputConfig.Outputs['selected_features'].S3Output.S3Uri",
            aliases=["features", "reduced_features", "feature_subset"],
            data_type="S3Uri",
            description="Selected subset of features with reduced dimensionality"
        ),
        "feature_importance": OutputSpec(
            logical_name="feature_importance",
            output_type=DependencyType.PROCESSING_OUTPUT,
            property_path="properties.ProcessingOutputConfig.Outputs['feature_importance'].S3Output.S3Uri",
            aliases=["importance", "feature_rankings"],
            data_type="S3Uri",
            description="Feature importance scores and rankings"
        )
    }
)

# Job type variants
FEATURE_SELECTION_TRAINING_SPEC = FEATURE_SELECTION_SPEC

# For calibration data
FEATURE_SELECTION_CALIBRATION_SPEC = StepSpecification(
    step_type=get_spec_step_type("FeatureSelection"),
    node_type=NodeType.INTERNAL,
    script_contract=_get_feature_selection_contract(),
    dependencies={
        "input_data": DependencySpec(
            logical_name="input_data",
            dependency_type=DependencyType.PROCESSING_OUTPUT,
            required=True,
            compatible_sources=["TabularPreprocessing_Calibration", "DataLoading_Calibration"],
            semantic_keywords=["data", "processed", "calibration", "features"],
            data_type="S3Uri",
            description="Preprocessed calibration data for feature selection"
        ),
        "config": DependencySpec(
            logical_name="config",
            dependency_type=DependencyType.PROCESSING_OUTPUT,
            required=False,
            compatible_sources=["ConfigGeneration", "DataLoading"],
            semantic_keywords=["config", "parameters", "settings"],
            data_type="S3Uri",
            description="Optional configuration for feature selection"
        )
    },
    outputs={
        "selected_features": OutputSpec(
            logical_name="selected_features",
            output_type=DependencyType.PROCESSING_OUTPUT,
            property_path="properties.ProcessingOutputConfig.Outputs['selected_features'].S3Output.S3Uri",
            aliases=["features", "calibration_features", "feature_subset"],
            data_type="S3Uri",
            description="Selected subset of calibration features with reduced dimensionality"
        ),
        "feature_importance": OutputSpec(
            logical_name="feature_importance",
            output_type=DependencyType.PROCESSING_OUTPUT,
            property_path="properties.ProcessingOutputConfig.Outputs['feature_importance'].S3Output.S3Uri",
            aliases=["importance", "feature_rankings"],
            data_type="S3Uri",
            description="Feature importance scores and rankings for calibration data"
        )
    }
)

def get_feature_selection_spec(job_type: str = None):
    """Get the appropriate specification based on job type."""
    if job_type and job_type.lower() == "calibration":
        return FEATURE_SELECTION_CALIBRATION_SPEC
    else:
        return FEATURE_SELECTION_TRAINING_SPEC  # Default to training
```

## Step 3: Register the Step Name

Now, let's register our step in the central registry.

**File to Update**: `src/pipeline_registry/step_names.py`

```python
STEP_NAMES = {
    # ... existing steps ...
    
    "FeatureSelection": {
        "config_class": "FeatureSelectionConfig",
        "builder_step_name": "FeatureSelectionStepBuilder",
        "spec_type": "FeatureSelection",
        "description": "Selects the most important features from preprocessed data"
    },
}
```

## Step 4: Create the Step Configuration

Let's create the configuration class for our step.

**File**: `src/pipeline_steps/config_feature_selection.py`

```python
from typing import List, Optional
from .config_base import BasePipelineConfig

class FeatureSelectionConfig(BasePipelineConfig):
    """Configuration for Feature Selection step."""
    
    def __init__(
        self,
        region: str,
        pipeline_s3_loc: str,
        selection_method: str = "mutual_info",
        n_features: int = 20,
        target_column: str = "target",
        min_importance: float = 0.01,
        job_type: str = "training",
        instance_type: str = "ml.m5.xlarge",
        instance_count: int = 1,
        volume_size_gb: int = 30,
        max_runtime_seconds: int = 3600,
        debug_mode: bool = False,
        random_seed: int = 42
    ):
        """Initialize FeatureSelection configuration.
        
        Args:
            region: AWS region
            pipeline_s3_loc: S3 location for pipeline artifacts
            selection_method: Method to use for feature selection ('mutual_info', 'correlation', 'tree_based')
            n_features: Number of features to select
            target_column: Name of the target/label column
            min_importance: Minimum importance threshold for features
            job_type: Type of job (training, calibration)
            instance_type: SageMaker instance type
            instance_count: Number of instances
            volume_size_gb: EBS volume size in GB
            max_runtime_seconds: Maximum runtime in seconds
            debug_mode: Enable debug mode
            random_seed: Random seed for reproducibility
        """
        super().__init__(region, pipeline_s3_loc)
        
        # Step-specific configuration
        self.selection_method = selection_method
        self.n_features = n_features
        self.target_column = target_column
        self.min_importance = min_importance
        self.job_type = job_type
        
        # SageMaker resource configuration
        self.instance_type = instance_type
        self.instance_count = instance_count
        self.volume_size_gb = volume_size_gb
        self.max_runtime_seconds = max_runtime_seconds
        
        # Optional parameters
        self.debug_mode = debug_mode
        self.random_seed = random_seed
    
    def get_script_contract(self):
        """Return the script contract for this step."""
        from ..pipeline_script_contracts.feature_selection_contract import FEATURE_SELECTION_CONTRACT
        return FEATURE_SELECTION_CONTRACT
        
    def get_script_path(self):
        """Return the path to the feature selection script."""
        return "feature_selection.py"
        
    def get_image_uri(self):
        """Return the image URI for the processor."""
        return "123456789012.dkr.ecr.{}.amazonaws.com/feature-selection:latest".format(self.region)
```

## Step 5: Create the Step Builder

Now, let's implement the builder class that creates the SageMaker step.

**File**: `src/pipeline_steps/builder_feature_selection.py`

```python
from typing import Dict, List, Any, Optional

from sagemaker.processing import ScriptProcessor, ProcessingInput, ProcessingOutput
from sagemaker.workflow.steps import ProcessingStep

from ..pipeline_deps.base_specifications import StepSpecification
from ..pipeline_script_contracts.base_script_contract import ScriptContract
from .builder_step_base import StepBuilderBase
from .config_feature_selection import FeatureSelectionConfig
from ..pipeline_step_specs.feature_selection_spec import get_feature_selection_spec

class FeatureSelectionStepBuilder(StepBuilderBase):
    """Builder for Feature Selection processing step."""
    
    def __init__(
        self, 
        config, 
        sagemaker_session=None, 
        role=None, 
        notebook_root=None,
        registry_manager=None,
        dependency_resolver=None
    ):
        # Get job type if available
        job_type = getattr(config, 'job_type', 'training')
        
        # Get the appropriate specification based on job type
        spec = get_feature_selection_spec(job_type)
        
        super().__init__(
            config=config,
            spec=spec,
            sagemaker_session=sagemaker_session,
            role=role,
            notebook_root=notebook_root,
            registry_manager=registry_manager,
            dependency_resolver=dependency_resolver
        )
        self.config: FeatureSelectionConfig = config
    
    def _get_inputs(self, inputs: Dict[str, Any]) -> List[ProcessingInput]:
        """Get inputs for the processor using the specification and contract."""
        # Use the specification-driven approach to generate inputs
        return self._get_spec_driven_processor_inputs(inputs)
    
    def _get_outputs(self, outputs: Dict[str, Any]) -> List[ProcessingOutput]:
        """Get outputs for the processor using the specification and contract."""
        # Use the specification-driven approach to generate outputs
        return self._get_spec_driven_processor_outputs(outputs)
    
    def _get_processor(self):
        """Create and return a SageMaker processor."""
        return ScriptProcessor(
            role=self.role,
            image_uri=self.config.get_image_uri(),
            command=["python3"],
            instance_count=self.config.instance_count,
            instance_type=self.config.instance_type,
            volume_size_in_gb=self.config.volume_size_gb,
            max_runtime_in_seconds=self.config.max_runtime_seconds,
            sagemaker_session=self.sagemaker_session
        )
    
    def _get_processor_env_vars(self) -> Dict[str, str]:
        """Get environment variables for the processor."""
        env_vars = {
            "SELECTION_METHOD": self.config.selection_method,
            "N_FEATURES": str(self.config.n_features),
            "TARGET_COLUMN": self.config.target_column,
            "MIN_IMPORTANCE": str(self.config.min_importance),
            "RANDOM_SEED": str(self.config.random_seed),
            "DEBUG_MODE": str(self.config.debug_mode).lower()
        }
        return env_vars
    
    def create_step(self, **kwargs) -> ProcessingStep:
        """Create the processing step.
        
        Args:
            **kwargs: Additional keyword arguments for step creation.
                     Should include 'dependencies' list if step has dependencies.
        """
        # Extract inputs from dependencies using the resolver
        dependencies = kwargs.get('dependencies', [])
        extracted_inputs = self.extract_inputs_from_dependencies(dependencies)
        
        # Get processor inputs and outputs
        inputs = self._get_inputs(extracted_inputs)
        outputs = self._get_outputs({})
        
        # Create processor
        processor = self._get_processor()
        
        # Set environment variables
        env_vars = self._get_processor_env_vars()
        
        # Create and return the step
        step_name = kwargs.get('step_name', 'FeatureSelection')
        step = processor.run(
            inputs=inputs,
            outputs=outputs,
            container_arguments=[],
            container_entrypoint=["python3", self.config.get_script_path()],
            job_name=self._generate_job_name(step_name),
            wait=False,
            environment=env_vars
        )
        
        # Store specification in step for future reference
        setattr(step, '_spec', self.spec)
        
        return step
```

## Step 6: Update Required Registry Files

Now, let's update the necessary registry files to expose our components.

**File**: `src/pipeline_steps/__init__.py`

```python
# Add to existing imports
from .builder_feature_selection import FeatureSelectionStepBuilder
```

**File**: `src/pipeline_step_specs/__init__.py`

```python
# Add to existing imports
from .feature_selection_spec import FEATURE_SELECTION_SPEC, get_feature_selection_spec
```

**File**: `src/pipeline_script_contracts/__init__.py`

```python
# Add to existing imports
from .feature_selection_contract import FEATURE_SELECTION_CONTRACT
```

## Step 7: Create the Processing Script

Let's create the feature selection script that implements the business logic.

**File**: `src/pipeline_scripts/feature_selection.py`

```python
#!/usr/bin/env python3

import os
import json
import logging
import argparse
import numpy as np
import pandas as pd
from typing import Dict, List, Tuple
from sklearn.feature_selection import (
    mutual_info_classif, 
    f_classif, 
    SelectKBest,
    SelectFromModel
)
from sklearn.ensemble import RandomForestClassifier

# Configure logging
logging.basicConfig(level=logging.INFO, format='%(asctime)s - %(levelname)s - %(message)s')
logger = logging.getLogger(__name__)

def get_script_contract():
    """Get the contract for this script."""
    from src.pipeline_script_contracts.feature_selection_contract import FEATURE_SELECTION_CONTRACT
    return FEATURE_SELECTION_CONTRACT

def parse_args():
    """Parse command line arguments."""
    parser = argparse.ArgumentParser()
    parser.add_argument('--debug', action='store_true', help='Enable debug mode')
    return parser.parse_args()

def read_input_data(input_path: str) -> pd.DataFrame:
    """Read input data from the specified path."""
    try:
        logger.info(f"Reading input data from {input_path}")
        
        # Check if directory exists
        if not os.path.exists(input_path):
            raise ValueError(f"Input path does not exist: {input_path}")
            
        # List files in directory
        files = [os.path.join(input_path, f) for f in os.listdir(input_path) 
                if f.endswith('.csv') or f.endswith('.parquet')]
        
        if not files:
            raise ValueError(f"No CSV or Parquet files found in {input_path}")
        
        # Read the first file
        file_path = files[0]
        logger.info(f"Reading file: {file_path}")
        
        if file_path.endswith('.csv'):
            df = pd.read_csv(file_path)
        elif file_path.endswith('.parquet'):
            df = pd.read_parquet(file_path)
        else:
            raise ValueError(f"Unsupported file format: {file_path}")
        
        logger.info(f"Read {len(df)} rows and {len(df.columns)} columns")
        return df
        
    except Exception as e:
        logger.error(f"Error reading input data: {str(e)}")
        raise

def read_config(config_path: str) -> Dict:
    """Read configuration from the specified path if available."""
    try:
        if not os.path.exists(config_path):
            logger.info(f"Config path does not exist: {config_path}. Using default configuration.")
            return {}
            
        config_files = [os.path.join(config_path, f) for f in os.listdir(config_path) 
                      if f.endswith('.json')]
        
        if not config_files:
            logger.info(f"No JSON config files found in {config_path}. Using default configuration.")
            return {}
        
        config_file = config_files[0]
        logger.info(f"Reading config from: {config_file}")
        
        with open(config_file, 'r') as f:
            config = json.load(f)
            
        logger.info(f"Loaded configuration: {config}")
        return config
        
    except Exception as e:
        logger.warning(f"Error reading config: {str(e)}. Using default configuration.")
        return {}

def select_features_mutual_info(
    X: pd.DataFrame, 
    y: pd.Series, 
    n_features: int, 
    random_state: int
) -> Tuple[List[str], pd.DataFrame]:
    """Select features using mutual information."""
    logger.info(f"Selecting {n_features} features using mutual information")
    
    # Handle categorical features
    categorical_cols = X.select_dtypes(include=['object', 'category']).columns.tolist()
    X_processed = X.copy()
    
    for col in categorical_cols:
        X_processed[col] = X_processed[col].astype('category').cat.codes
    
    # Apply mutual information
    selector = SelectKBest(mutual_info_classif, k=min(n_features, X.shape[1]))
    selector.fit(X_processed, y)
    
    # Get selected features and importance scores
    feature_idx = selector.get_support(indices=True)
    feature_names = X.columns[feature_idx].tolist()
    importance_scores = selector.scores_[feature_idx]
    
    # Create importance DataFrame
    importance_df = pd.DataFrame({
        'feature': feature_names,
        'importance': importance_scores
    }).sort_values('importance', ascending=False)
    
    logger.info(f"Selected {len(feature_names)} features")
    return feature_names, importance_df

def select_features_correlation(
    X: pd.DataFrame, 
    y: pd.Series, 
    n_features: int
) -> Tuple[List[str], pd.DataFrame]:
    """Select features using ANOVA F-value."""
    logger.info(f"Selecting {n_features} features using correlation (F-value)")
    
    # Handle categorical features
    categorical_cols = X.select_dtypes(include=['object', 'category']).columns.tolist()
    X_processed = X.copy()
    
    for col in categorical_cols:
        X_processed[col] = X_processed[col].astype('category').cat.codes
    
    # Apply F-test
    selector = SelectKBest(f_classif, k=min(n_features, X.shape[1]))
    selector.fit(X_processed, y)
    
    # Get selected features and importance scores
    feature_idx = selector.get_support(indices=True)
    feature_names = X.columns[feature_idx].tolist()
    importance_scores = selector.scores_[feature_idx]
    
    # Create importance DataFrame
    importance_df = pd.DataFrame({
        'feature': feature_names,
        'importance': importance_scores
    }).sort_values('importance', ascending=False)
    
    logger.info(f"Selected {len(feature_names)} features")
    return feature_names, importance_df

def select_features_tree_based(
    X: pd.DataFrame, 
    y: pd.Series, 
    n_features: int, 
    random_state: int
) -> Tuple[List[str], pd.DataFrame]:
    """Select features using tree-based feature importance."""
    logger.info(f"Selecting {n_features} features using tree-based method")
    
    # Handle categorical features
    categorical_cols = X.select_dtypes(include=['object', 'category']).columns.tolist()
    X_processed = X.copy()
    
    for col in categorical_cols:
        X_processed[col] = X_processed[col].astype('category').cat.codes
    
    # Train a random forest
    model = RandomForestClassifier(n_estimators=100, random_state=random_state)
    model.fit(X_processed, y)
    
    # Create a selector based on importance threshold
    selector = SelectFromModel(model, threshold=-np.inf, max_features=n_features)
    selector.fit(X_processed, y)
    
    # Get selected features and importance scores
    feature_idx = selector.get_support(indices=True)
    feature_names = X.columns[feature_idx].tolist()
    importance_scores = model.feature_importances_[feature_idx]
    
    # Create importance DataFrame
    importance_df = pd.DataFrame({
        'feature': feature_names,
        'importance': importance_scores
    }).sort_values('importance', ascending=False)
    
    logger.info(f"Selected {len(feature_names)} features")
    return feature_names, importance_df

def filter_by_importance(
    feature_names: List[str], 
    importance_df: pd.DataFrame, 
    min_importance: float
) -> Tuple[List[str], pd.DataFrame]:
    """Filter features by minimum importance threshold."""
    logger.info(f"Filtering features with importance >= {min_importance}")
    
    filtered_df = importance_df[importance_df['importance'] >= min_importance]
    filtered_features = filtered_df['feature'].tolist()
    
    logger.info(f"Filtered from {len(feature_names)} to {len(filtered_features)} features")
    return filtered_features, filtered_df

def write_outputs(
    df: pd.DataFrame, 
    feature_names: List[str], 
    importance_df: pd.DataFrame, 
    output_features_path: str, 
    output_importance_path: str
):
    """Write selected features and importance scores to output paths."""
    try:
        # Create output directories
        os.makedirs(output_features_path, exist_ok=True)
        os.makedirs(output_importance_path, exist_ok=True)
        
        # Select features from original DataFrame
        selected_df = df[feature_names + [df.columns[-1]]]  # Include target column
        
        # Write selected features
        features_file = os.path.join(output_features_path, 'selected_features.parquet')
        logger.info(f"Writing selected features to {features_file}")
        selected_df.to_parquet(features_file, index=False)
        
        # Write feature list as JSON
        feature_list_file = os.path.join(output_features_path, 'feature_list.json')
        with open(feature_list_file, 'w') as f:
            json.dump(feature_names, f)
            
        # Write importance scores
        importance_file = os.path.join(output_importance_path, 'feature_importance.csv')
        logger.info(f"Writing importance scores to {importance_file}")
        importance_df.to_csv(importance_file, index=False)
        
        # Write importance visualization
        importance_viz_file = os.path.join(output_importance_path, 'importance_plot.json')
        with open(importance_viz_file, 'w') as f:
            viz_data = {
                'features': importance_df['feature'].tolist(),
                'importance': importance_df['importance'].tolist()
            }
            json.dump(viz_data, f)
            
    except Exception as e:
        logger.error(f"Error writing outputs: {str(e)}")
        raise

def main():
    """Main entry point for the script."""
    args = parse_args()
    
    try:
        # Get and validate contract
        contract = get_script_contract()
        
        # Set log level
        if args.debug or os.environ.get("DEBUG_MODE", "False").lower() == "true":
            logging.getLogger().setLevel(logging.DEBUG)
            logger.debug("Debug mode enabled")
        
        # Get paths from contract
        input_data_path = contract.expected_input_paths["input_data"]
        config_path = contract.expected_input_paths["config"]
        output_features_path = contract.expected_output_paths["selected_features"]
        output_importance_path = contract.expected_output_paths["feature_importance"]
        
        # Get parameters from environment variables
        selection_method = os.environ["SELECTION_METHOD"]
        n_features = int(os.environ["N_FEATURES"])
        target_column = os.environ["TARGET_COLUMN"]
        min_importance = float(os.environ.get("MIN_IMPORTANCE", "0.01"))
        random_seed = int(os.environ.get("RANDOM_SEED", "42"))
        
        logger.info(f"Parameters: method={selection_method}, n_features={n_features}, target={target_column}")
        
        # Read input data
        df = read_input_data(input_data_path)
        
        # Read config if available
        config = read_config(config_path)
        
        # Override parameters from config if provided
        if config:
            selection_method = config.get("selection_method", selection_method)
            n_features = config.get("n_features", n_features)
            target_column = config.get("target_column", target_column)
            min_importance = config.get("min_importance", min_importance)
            
        # Prepare features and target
        if target_column not in df.columns:
            raise ValueError(f"Target column '{target_column}' not found in data columns: {df.columns}")
            
        X = df.drop(columns=[target_column])
        y = df[target_column]
        
        # Select features based on method
        if selection_method == "mutual_info":
            feature_names, importance_df = select_features_mutual_info(X, y, n_features, random_seed)
        elif selection_method == "correlation":
            feature_names, importance_df = select_features_correlation(X, y, n_features)
        elif selection_method == "tree_based":
            feature_names, importance_df = select_features_tree_based(X, y, n_features, random_seed)
        else:
            raise ValueError(f"Unknown selection method: {selection_method}")
        
        # Filter by importance threshold
        if min_importance > 0:
            feature_names, importance_df = filter_by_importance(feature_names, importance_df, min_importance)
        
        # Write outputs
        write_outputs(df, feature_names, importance_df, output_features_path, output_importance_path)
        
        logger.info(f"Feature selection complete. Selected {len(feature_names)} features.")
        
    except Exception as e:
        logger.error(f"Feature selection failed: {str(e)}")
        raise

if __name__ == "__main__":
    main()
```

## Step 8: Create Unit Tests

Let's create unit tests for our step components.

**File**: `test/v2/pipeline_steps/test_builder_feature_selection.py`

```python
import unittest
from unittest.mock import MagicMock, patch

from src.pipeline_steps.builder_feature_selection import FeatureSelectionStepBuilder
from src.pipeline_steps.config_feature_selection import FeatureSelectionConfig
from src.pipeline_step_specs.feature_selection_spec import FEATURE_SELECTION_SPEC
from src.pipeline_deps.base_specifications import NodeType, DependencyType

class TestFeatureSelectionStepBuilder(unittest.TestCase):
    def setUp(self):
        self.config = FeatureSelectionConfig(
            region="us-west-2",
            pipeline_s3_loc="s3://bucket/prefix",
            selection_method="mutual_info",
            n_features=20,
            target_column="target"
        )
        self.builder = FeatureSelectionStepBuilder(self.config)
    
    def test_initialization(self):
        """Test that the builder initializes correctly with specification."""
        self.assertIsNotNone(self.builder.spec)
        self.assertEqual(self.builder.spec.step_type, FEATURE_SELECTION_SPEC.step_type)
        self.assertEqual(self.builder.spec.node_type, NodeType.INTERNAL)
    
    def test_get_inputs(self):
        """Test that inputs are correctly derived from dependencies."""
        # Mock input data
        inputs = {
            "input_data": "s3://bucket/input/data",
            "config": "s3://bucket/input/config"
        }
        
        # Get processing inputs
        processing_inputs = self.builder._get_inputs(inputs)
        
        # Verify inputs
        self.assertEqual(len(processing_inputs), 2)
        self.assertEqual(processing_inputs[0].source, "s3://bucket/input/data")
        self.assertEqual(processing_inputs[1].source
```


-----------
##  Recommended Notes


