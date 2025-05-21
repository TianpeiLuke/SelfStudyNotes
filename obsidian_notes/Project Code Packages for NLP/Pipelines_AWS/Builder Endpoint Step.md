---
tags:
  - code
  - code_snippet
  - python/aws_python_sdk
  - aws/sagemaker
  - aws/step_function
keywords: 
topics: 
language: python
date of note: 2025-05-20
---

## Code Snippet Summary

>[!important]
>**Builder** Class for the following steps
>- Create Model
>- Configure Endpoint
>- Launch Endpoint

- [[Design Pattern Builder Pattern]]

### Previous Step

- [[Builder Model Step]]

## Code

```python
from sagemaker.workflow.steps import EndpointConfigStep, EndpointStep
from sagemaker.workflow.parameters import ParameterString
from sagemaker.workflow.properties import Properties

from typing import Optional
import logging

logger = logging.getLogger(__name__)
```

### Load Model Config

- [[Model Config for Training Step]]

### Builder

```python
class PytorchEndpointStepBuilder:
    """Builder for SageMaker EndpointConfigStep and EndpointStep."""

    def __init__(
        self,
        config: ModelConfig,  # ModelConfig with inference_instance_type, pipeline_name, etc.
        model_step_properties: Properties,
    ):
        self.config = config
        self.model_step_properties = model_step_properties

    def _sanitize_name(self, name: str, max_len: int = 63) -> str:
        sanitized = ''.join(c if c.isalnum() else '-' for c in name)
        return '-'.join(filter(None, sanitized.split('-')))[:max_len]

    def create_endpoint_steps(self) -> Tuple[EndpointConfigStep, EndpointStep]:
        """
        Create EndpointConfigStep and EndpointStep using the pipeline name.
    
        Returns:
            Tuple containing EndpointConfigStep and EndpointStep.
        """
        # Use default base name if pipeline_name is missing
        if hasattr(self.config, "pipeline_name") and self.config.pipeline_name:
            sanitized_pipeline_name = self._sanitize_name(self.config.pipeline_name, max_len=60)
            endpoint_config_name = f"{sanitized_pipeline_name}-config"
            endpoint_name = f"{sanitized_pipeline_name}-endpoint"
            endpoint_config_step_name = f"{sanitized_pipeline_name}-CreateEndpointConfig"
            endpoint_step_name = f"{sanitized_pipeline_name}-DeployEndpoint"
        else:
            logger.warning("pipeline_name not found in config. Using default step names.")
            endpoint_config_name = "default-endpoint-config"
            endpoint_name = "default-endpoint"
            endpoint_config_step_name = "DefaultCreateEndpointConfig"
            endpoint_step_name = "DefaultDeployEndpoint"

        # Define pipeline parameters
        endpoint_config_param = ParameterString(
            "EndpointConfigName", default_value=endpoint_config_name
        )
        endpoint_name_param = ParameterString(
            "EndpointName", default_value=endpoint_name
        )

        # Create EndpointConfigStep
        endpoint_config_step = EndpointConfigStep(
            name=endpoint_config_step_name[:80],
            model_name=self.model_step_properties.ModelName,
            instance_type=self.config.inference_instance_type,
            endpoint_config_name=endpoint_config_param
        )

        # Create EndpointStep
        endpoint_step = EndpointStep(
            name=endpoint_step_name[:80],
            endpoint_name=endpoint_name_param,
            endpoint_config_name=endpoint_config_step.properties.EndpointConfigName
        )

        return endpoint_config_step, endpoint_step
```



-----------
##  Recommended Notes


- [[AWS Step Functions - One-Step Processing Workflow]]

