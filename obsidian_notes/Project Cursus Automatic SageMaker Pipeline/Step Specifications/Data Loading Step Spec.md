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


## Code

```python
from ..pipeline_deps.base_specifications import StepSpecification, DependencySpec, OutputSpec, DependencyType, NodeType
from ..pipeline_registry.step_names import get_spec_step_type
```

### Training

```python
# Cradle Data Loading Training Step Specification
DATA_LOADING_TRAINING_SPEC = StepSpecification(
    step_type=get_spec_step_type("CradleDataLoading") + "_Training",
    node_type=NodeType.SOURCE,
    dependencies=[
        # Note: CradleDataLoading is typically the first step in a pipeline
        # and doesn't depend on other pipeline steps - it loads data from external sources
    ],
    outputs=[
        OutputSpec(
            logical_name="DATA",
            output_type=DependencyType.PROCESSING_OUTPUT,
            property_path="properties.ProcessingOutputConfig.Outputs['DATA'].S3Output.S3Uri",
            data_type="S3Uri",
            description="Training data output from Cradle data loading",
            semantic_keywords=["training", "train", "data", "input", "raw", "dataset", "model_training", "source"]
        ),
        OutputSpec(
            logical_name="METADATA",
            output_type=DependencyType.PROCESSING_OUTPUT,
            property_path="properties.ProcessingOutputConfig.Outputs['METADATA'].S3Output.S3Uri",
            data_type="S3Uri",
            description="Training metadata output from Cradle data loading",
            semantic_keywords=["training", "train", "metadata", "schema", "info", "description", "model_training"]
        ),
        OutputSpec(
            logical_name="SIGNATURE",
            output_type=DependencyType.PROCESSING_OUTPUT,
            property_path="properties.ProcessingOutputConfig.Outputs['SIGNATURE'].S3Output.S3Uri",
            data_type="S3Uri",
            description="Training signature output from Cradle data loading",
            semantic_keywords=["training", "train", "signature", "validation", "checksum", "model_training"]
        )
    ]
)
```


- [[Builder MODS Cradle Data Loading Step]]
- [[Config for Cradle Data Loading Step]]


-----------
##  Recommended Notes


- [[Step Specification Design as Declarative Pipeline Architecture]]
- [[Specification Registry Design]]
- [[Config-Driven vs Specification-Driven Design]]
