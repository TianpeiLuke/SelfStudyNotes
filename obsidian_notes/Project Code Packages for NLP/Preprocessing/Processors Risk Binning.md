---
tags:
  - code
  - code_snippet
  - python
  - python/processor
keywords: 
topics: 
language: python
date of note: 2025-05-28
---

## Code Snippet Summary

>[!important]
>Develop a **binning processor**
>- Transform *categorical value* into numerical via **risk table mapping**
>- Assume $$C(f_{1}, l)$$ be the count of co-occurence of feature-label pair $(f_{1}, l)$ for $l\in \mathcal{Y} := \left\{ 0,1 \right\}$
>	- Assume $N$ as the count of all samples
>- Additional parameters
>	- smooth factor $\alpha$
>	- default risk $p_{1} \in (0,1]$, which is the *marginal label probability* $$p_{1} = \frac{C(1)}{C(0) + C(1)}$$
>- Formula for **risk-table binning** $$b(f_{1}) :=  \frac{C(f_{1}, 1) + \alpha \cdot  N \cdot p_{1}}{\sum_{l\in \mathcal{Y}}C(f_{1}, l) + \alpha \cdot N}$$ 
>	- when both $C(f_{1}, 1), \sum_{l\in \mathcal{Y}}C(f_{1}, l) \to \infty$, it converges to histogram $$b(f_{1}) \to \hat{p}(1| f_{1})  = \frac{C(f_{1}, 1)}{C(f_{1}, 0) + C(f_{1}, 1)}$$
>	- when  $\sum_{l\in \mathcal{Y}}C(f_{1}, l) \to 0$, it converges to default risk $$b(f_{1}) \to \frac{\alpha \cdot p_{1}}{\alpha} = p_{1}$$

- [[Risk Value Mapping of Categorical Field]]

## Code

```python
import pandas as pd
import numpy as np
from typing import Dict, List, Tuple, Optional, Union, Any
from pathlib import Path
import json
```


```python
from .processors import Processor
```

- [[Processors ver 2.0]]

### Binning Processor

```python
class BinningProcessor(Processor):
    """
    A processor that performs risk-based binning on a specified categorical variable.
    The 'process' method (called via __call__) handles single values.
    The 'transform' method handles pandas Series or DataFrames.
    """
    
    def __init__(
        self, 
        column_name: str,
        label_name: str, 
        smooth_factor: float = 0.0,
        count_threshold: int = 0,
        risk_tables: Optional[Dict] = None
    ):
        """
        Initialize BinningProcessor.
        
        Args:
            column_name: Name of the categorical column to be binned.
            label_name: Name of label/target variable (expected to be binary 0 or 1).
            smooth_factor: Smoothing factor for risk calculation (0 to 1).
            count_threshold: Minimum count for considering a category's calculated risk.
            risk_tables: Optional pre-computed risk tables.
        """
        super().__init__() # Initialize base Processor
        self.processor_name = 'binning_processor'
        # Lists primary public methods for potential introspection
        
        if not isinstance(column_name, str) or not column_name:
            raise ValueError("column_name must be a non-empty string.")
        self.column_name = column_name
        self.label_name = label_name
        self.smooth_factor = smooth_factor
        self.count_threshold = count_threshold
        
        self.is_fitted = False
        if risk_tables:
            self._validate_risk_tables(risk_tables)
            self.risk_tables = risk_tables
            self.is_fitted = True
        else:
            self.risk_tables = {}

    def get_name(self) -> str: # Implementation for base class compatibility
        return self.processor_name

    def _validate_risk_tables(self, risk_tables: Dict) -> None:
        if not isinstance(risk_tables, dict):
            raise ValueError("Risk tables must be a dictionary.")
        if "bins" not in risk_tables or "default_bin" not in risk_tables:
            raise ValueError("Risk tables must contain 'bins' and 'default_bin' keys.")
        if not isinstance(risk_tables["bins"], dict):
            raise ValueError("Risk tables 'bins' must be a dictionary.")
        if not isinstance(risk_tables["default_bin"], (int, float, np.floating, np.integer)):
            raise ValueError(f"Risk tables 'default_bin' must be a number, got {type(risk_tables['default_bin'])}.")

    def set_risk_tables(self, risk_tables: Dict) -> None:
        self._validate_risk_tables(risk_tables)
        self.risk_tables = risk_tables
        self.is_fitted = True

    def fit(self, data: pd.DataFrame) -> 'BinningProcessor':
        if not isinstance(data, pd.DataFrame):
            raise TypeError("fit() requires a pandas DataFrame.")
        if self.label_name not in data.columns:
            raise ValueError(f"Label variable '{self.label_name}' not found in input data.")
        if self.column_name not in data.columns:
            raise ValueError(f"Column to bin '{self.column_name}' not found in input data.")
            
        filtered_data = data[data[self.label_name] != -1].dropna(subset=[self.label_name, self.column_name])
        
        if filtered_data.empty:
            # Handle case with no valid data for fitting
            print(f"Warning: Filtered data for column '{self.column_name}' is empty during fit. "
                  "Risk tables will be empty, default_bin will be 0.5 or NaN if no labels at all.")
            # Attempt to get a global mean if any data existed before filtering for column_name
            overall_label_mean = data[self.label_name][data[self.label_name] != -1].mean()
            self.risk_tables = {
                "bins": {}, 
                "default_bin": 0.5 if pd.isna(overall_label_mean) else float(overall_label_mean)
            }
            self.is_fitted = True
            return self

        default_risk = float(filtered_data[self.label_name].mean())
        smooth_samples = int(len(filtered_data) * self.smooth_factor)
        
        cross_tab_result = pd.crosstab(
            index=filtered_data[self.column_name].astype(str),
            columns=filtered_data[self.label_name].astype(int), 
            margins=True,
            margins_name="_count_",
            dropna=False
        )
        
        positive_label_col = 1
        negative_label_col = 0

        if positive_label_col not in cross_tab_result.columns:
            cross_tab_result[positive_label_col] = 0
        if negative_label_col not in cross_tab_result.columns:
            cross_tab_result[negative_label_col] = 0
        
        calc_df = cross_tab_result[cross_tab_result.index != '_count_'].copy()

        if calc_df.empty : 
             self.risk_tables = {"bins": {}, "default_bin": default_risk}
             self.is_fitted = True
             return self

        calc_df["risk"] = calc_df.apply(
            lambda x: x[positive_label_col] / (x[positive_label_col] + x[negative_label_col])
            if (x[positive_label_col] + x[negative_label_col]) > 0 else 0.0,
            axis=1
        )
        
        calc_df["_category_count_"] = cross_tab_result.loc[calc_df.index, "_count_"]

        calc_df["smooth_risk"] = calc_df.apply(
            lambda x: (
                (x["_category_count_"] * x["risk"] + smooth_samples * default_risk)
                / (x["_category_count_"] + smooth_samples)
                if (x["_category_count_"] >= self.count_threshold and (x["_category_count_"] + smooth_samples) > 0)
                else default_risk
            ),
            axis=1
        )
        
        self.risk_tables = {
            "bins": dict(zip(calc_df.index.astype(str), calc_df["smooth_risk"])),
            "default_bin": default_risk
        }
        
        self.is_fitted = True
        return self

    def process(self, input_value: Any) -> float:
        """
        Process a single input value (for the configured 'column_name'), 
        mapping it to its binned risk value.
        This method is called when the processor instance is called as a function.
        """
        if not self.is_fitted:
            raise RuntimeError("BinningProcessor must be fitted or initialized with risk tables before processing.")
        str_value = str(input_value)
        return self.risk_tables["bins"].get(str_value, self.risk_tables["default_bin"])

    def transform(self, data: Union[pd.DataFrame, pd.Series, Any]) -> Union[pd.DataFrame, pd.Series, float]:
        """
        Transform data using the computed risk tables.
        - If data is a DataFrame, transforms the 'column_name' Series within it.
        - If data is a Series, transforms the Series (assumed to be the target column).
        - If data is a single value, uses the 'process' method.
        """
        if not self.is_fitted:
            raise RuntimeError("BinningProcessor must be fitted or initialized with risk tables before transforming.")
            
        if isinstance(data, pd.DataFrame):
            if self.column_name not in data.columns:
                raise ValueError(f"Column '{self.column_name}' not found in input DataFrame for transform operation.")
            output_data = data.copy()
            output_data[self.column_name] = data[self.column_name].astype(str).map(self.risk_tables["bins"]).fillna(self.risk_tables["default_bin"])
            return output_data
        elif isinstance(data, pd.Series):
            return data.astype(str).map(self.risk_tables["bins"]).fillna(self.risk_tables["default_bin"])
        else: 
            return self.process(data) # Consistent with __call__

    def get_risk_tables(self) -> Dict:
        if not self.is_fitted:
            raise RuntimeError("BinningProcessor has not been fitted or initialized with risk tables.")
        return self.risk_tables

    def save_risk_tables(self, output_dir: Union[Path, str]) -> None:
        if not self.is_fitted:
            raise RuntimeError("Cannot save risk tables before fitting or initialization with risk tables.")
        output_dir_path = Path(output_dir)
        output_dir_path.mkdir(parents=True, exist_ok=True)
        
        pkl_file = output_dir_path / f"{self.processor_name}_{self.column_name}_risk_tables.pkl"
        json_file = output_dir_path / f"{self.processor_name}_{self.column_name}_risk_tables.json"

        with open(pkl_file, 'wb') as f_pkl:
            pd.to_pickle(self.risk_tables, f_pkl)
        
        json_serializable_tables = {
            "bins": {str(k): float(v) for k, v in self.risk_tables.get("bins", {}).items()},
            "default_bin": float(self.risk_tables.get("default_bin", 0.0))
        }
        with open(json_file, 'w') as f_json:
            json.dump(json_serializable_tables, f_json, indent=2)
        # print(f"Risk tables for column '{self.column_name}' saved to {output_dir_path}")

    def load_risk_tables(self, filepath: Union[Path, str]) -> None:
        filepath_path = Path(filepath)
        if not filepath_path.exists():
            raise FileNotFoundError(f"Risk table file not found: {filepath_path}")
        with open(filepath_path, 'rb') as f:
            loaded_tables = pd.read_pickle(f)
        self._validate_risk_tables(loaded_tables)
        self.risk_tables = loaded_tables
        self.is_fitted = True
        # print(f"Risk tables loaded from {filepath_path}")
```

- [[Binning and Pivot Table - Count Frequency of Pairs of Features]]

### Usage

```python
COLUMN_TO_BIN = "some_categorical_field" 
TARGET_COLUMN = "target_column"

# Dummy training_data for Example 4 
dummy_training_data = pd.DataFrame({ 
	COLUMN_TO_BIN: ["category1", "category2", "category1", "category3", "category2", "category1"], 
	TARGET_COLUMN: [0, 1, 0, 1, 1, 0],
	"other_feature": [10, 20, 30, 40, 50, 60] 
})

# Example 1: Using pre-computed risk tables
risk_tables = {
    "bins": {
        "category1": 0.1,
        "category2": 0.2,
        "category3": 0.3
    },
    "default_bin": 0.15
}

binning_processor_ex1 = BinningProcessor( 
	column_name=COLUMN_TO_BIN, # <<< ADDED/MODIFIED 
	label_name=TARGET_COLUMN, 
	risk_tables=risk_tables_data # Provide pre-computed risk tables 
	)

# Example 2: Setting risk tables after initialization
binning_processor = BinningProcessor( 
	column_name=COLUMN_TO_BIN, # <<< ADDED/MODIFIED 
	label_name=TARGET_COLUMN 
	)
binning_processor.set_risk_tables(risk_tables)

# Example 3: Loading risk tables from file
binning_processor = BinningProcessor(	
	column_name=COLUMN_TO_BIN, # <<< ADDED/MODIFIED 
	label_name=TARGET_COLUMN 
	)
binning_processor.load_risk_tables(Path("path/to/risk_tables.pkl"))

# Example 4: Fitting from data (original functionality)
binning_processor = BinningProcessor(
	column_name=COLUMN_TO_BIN,
    label_name=TARGET_COLUMN,
    smooth_factor=0.1,
    count_threshold=10
)
binning_processor.fit(training_data)

# Using with BSMDataset
dataset = BSMDataset(config=config, dataframe=data)
dataset.add_pipeline(COLUMN_TO_BIN, binning_processor)
```

- [[BSMDataset]]


-----------
##  Recommended Notes



- [[Binning - Partition a field into bins and show the size of each bin]]
- [[Binning]]

- [[Binning as Categorical Feature Transformation]]
- Wikipedia
	- [Data binning](https://en.wikipedia.org/wiki/Data_binning)

- Resources
	- [Optimal Binning](https://gnpalencia.org/optbinning/tutorials/tutorial_binary.html)
	- Weight of Evidence (WoE)
	- Information Value (IV)