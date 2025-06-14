---
tags:
  - code
  - code_snippet
  - aws/sagemaker_pipeline
  - python/pydantic
keywords: 
topics: 
language: python
date of note: 2025-06-03
---

## Code Snippet Summary

>[!important]


- [[Config for XGBoost Training Step]]
## Code

### Import

```python
from pydantic import BaseModel, Field, model_validator
from typing import List, Optional, Dict, Any, Union
```



```python
from .hyperparameters_base import ModelHyperparameters
```

- [[Hyperparameter for Training Step]]

### Main

```python
class XGBoostModelHyperparameters(ModelHyperparameters):
    """
    Hyperparameters for the XGBoost model training,
    extending the base ModelHyperparameters.
    """
    # Override model_class from base
    model_class: str = Field(default="xgboost", description="Model class identifier, set to XGBoost.")

    # General Parameters
    booster: str = Field(default="gbtree", description="Specify which booster to use: gbtree, gblinear or dart.")
    # silent: Optional[int] = Field(default=None, description="0 means print running messages, 1 means silent mode. Deprecated, use verbosity.")
    # nthread: Optional[int] = Field(default=None, description="Number of parallel threads used to run XGBoost. (Usually set by SageMaker)")
    # disable_default_eval_metric: Optional[int] = Field(default=None, description="Flag to disable default metric. Set to >0 to disable.")
    verbosity: int = Field(
        default=1,
        description="Verbosity of printing messages. Valid values: 0 (silent), 1 (warning), 2 (info), 3 (debug)"
    )

    # Booster Parameters
    eta: float = Field(default=0.3, ge=0.0, le=1.0, description="Step size shrinkage used in update to prevents overfitting. Alias: learning_rate.")
    gamma: float = Field(default=0.0, ge=0.0, description="Minimum loss reduction required to make a further partition on a leaf node of the tree. Alias: min_split_loss.")
    max_depth: int = Field(default=6, ge=0, description="Maximum depth of a tree. 0 means no limit (not recommended).")
    min_child_weight: float = Field(default=1.0, ge=0.0, description="Minimum sum of instance weight (hessian) needed in a child.")
    max_delta_step: float = Field(default=0.0, description="Maximum delta step we allow each tree's weight estimation to be. If 0, no constraint.")
    subsample: float = Field(default=1.0, gt=0.0, le=1.0, description="Subsample ratio of the training instances.")
    colsample_bytree: float = Field(default=1.0, gt=0.0, le=1.0, description="Subsample ratio of columns when constructing each tree.")
    colsample_bylevel: float = Field(default=1.0, gt=0.0, le=1.0, description="Subsample ratio of columns for each level.")
    colsample_bynode: float = Field(default=1.0, gt=0.0, le=1.0, description="Subsample ratio of columns for each split.")
    lambda_xgb: float = Field(default=1.0, ge=0.0, description="L2 regularization term on weights. Alias: reg_lambda.")
    alpha_xgb: float = Field(default=0.0, ge=0.0, description="L1 regularization term on weights. Alias: reg_alpha.")
    tree_method: str = Field(default="auto", description="The tree construction algorithm used in XGBoost. (e.g. 'auto', 'exact', 'approx', 'hist', 'gpu_hist')")
    sketch_eps: Optional[float] = Field(default=None, ge=0.0, le=1.0, description="For tree_method 'approx'. Approximately (1 / sketch_eps) buckets are made.")
    scale_pos_weight: float = Field(default=1.0, description="Control the balance of positive and negative weights, useful for unbalanced classes.")
    # updater: Optional[str] = Field(default=None, description="A comma separated string defining the sequence of tree updaters to run.")
    # refresh_leaf: Optional[int] = Field(default=None, description="Refresh updater behavior.")
    # process_type: Optional[str] = Field(default=None, description="Boosting process to run.")
    # grow_policy: Optional[str] = Field(default=None, description="Controls how new nodes are added to the tree. ('depthwise', 'lossguide')")
    # max_leaves: Optional[int] = Field(default=None, description="Maximum number of nodes to be added. Only relevant for 'lossguide' grow_policy.")
    # max_bin: Optional[int] = Field(default=None, description="For tree_method 'hist'. Maximum number of discrete bins to bucket continuous features.")
    # predictor: Optional[str] = Field(default=None, description="The type of predictor algorithm to use. ('cpu_predictor', 'gpu_predictor')")
    num_parallel_tree: Optional[int] = Field(default=None, ge=1, description="Number of parallel trees constructed during each iteration. Used for random forests.")

    # Learning Task Parameters
    objective: str = Field(default="reg:squarederror", description="Specify the learning task and the corresponding learning objective.")
    base_score: Optional[float] = Field(default=None, description="The initial prediction score of all instances, global bias.")
    eval_metric: Optional[Union[str, List[str]]] = Field(default=None, description="Evaluation metric(s) for validation data.")
    seed: Optional[int] = Field(default=None, description="Random number seed.")
    
    # SageMaker Specific or Common Control Parameters for XGBoost
    num_round: int = Field(default=100, ge=1, description="The number of rounds for boosting.")
    early_stopping_rounds: Optional[int] = Field(default=None, ge=1, description="Activates early stopping. Validation metric needs to improve at least once in every early_stopping_rounds round(s). Requires at least one item in eval_metric.")
    # csv_weights: Optional[int] = Field(default=None, description="[0 or 1] To consider weights in CSV input data. (SageMaker specific interpretation)")
    # Note: 'num_class' is inherited from ModelHyperparameters. It's used when objective is multi:softmax or multi:softprob.

    class Config(ModelHyperparameters.Config): # Inherit Config from base
        pass # No changes needed for this example, but can be extended

    @model_validator(mode='after')
    def validate_xgboost_hyperparameters(self) -> 'XGBoostModelHyperparameters':
        # Call base validator if needed, or add XGBoost specific cross-field validations
        # super().validate_base_hyperparameters() # If you want to call it explicitly

        if self.objective.startswith("multi:") and (self.num_classes is None or self.num_classes < 2):
            raise ValueError(
                f"For multiclass objective '{self.objective}', 'num_classes' must be provided and be >= 2. "
                f"Current num_classes: {self.num_classes}"
            )
        
        if self.early_stopping_rounds is not None and not self.eval_metric:
            raise ValueError("'early_stopping_rounds' requires 'eval_metric' to be set.")

        # You can add more XGBoost specific validations here.
        # For example, certain tree_methods might require specific other parameters.
        if self.tree_method == "gpu_hist" and self.device == -1: # Assuming device from base means CPU
             print(f"Warning: tree_method is '{self.tree_method}' but base 'device' might indicate CPU. Ensure SageMaker instance is GPU for gpu_hist.")

        # Validate relationship between inherited 'learning_rate' and 'eta'
        # This is more of a design choice: do you want both, or enforce one?
        # For now, we assume 'eta' is the primary one for XGBoost.
        # If self.learning_rate is set and eta is also set, which one takes precedence?
        # SageMaker XGBoost uses 'eta'.
        if hasattr(self, 'learning_rate') and self.learning_rate != 3e-05 and self.eta == 0.3: # Check if learning_rate was changed from its base default while eta is at its xgb default
            print(f"Warning: Inherited 'learning_rate' ({self.learning_rate}) is set. "
                  f"XGBoost uses 'eta' ({self.eta}). Ensure you are using 'eta' for XGBoost learning rate control.")

        return self
```



-----------
##  Recommended Notes


- [[Hyperparameter for Pytorch Training Step]]
- [[Data Class with Pydantic]]