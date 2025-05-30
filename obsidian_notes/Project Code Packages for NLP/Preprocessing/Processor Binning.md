---
tags:
  - code
  - code_snippet
  - python/processor
  - feature_engineering
keywords: 
topics: 
language: 
date of note: 2025-05-29
---

## Code Snippet Summary

>[!important]


- [[Binning as Feature Categorization]]
## Code

```python
import pandas as pd
import numpy as np
from typing import List, Union, Dict, Optional
from pathlib import Path
import json 
```

```python
from .processors import Processor
```

### Numerical Binning


```python
class NumericalBinningProcessor(Processor):
    """
    A processor that performs numerical binning on a specified column using
    either equal-width or quantile strategies, outputting categorical bin labels.
    """
    
    def __init__(
        self, 
        column_name: str,
        n_bins: int = 5,
        strategy: str = 'quantile', # 'quantile' or 'equal-width'
        bin_labels: Optional[Union[List[str], bool]] = None, # List of labels, True for default "Bin_X", False for interval
        output_column_name: Optional[str] = None, # Optional: name for the new binned column
        handle_missing_value: Optional[str] = "as_is", # How to handle NaNs: "as_is" (becomes NaN), or a specific string label
        handle_out_of_range: Optional[str] = "boundary_bins" # "boundary_bins" (assign to min/max bin), or a specific string label
    ):
        """
        Initialize NumericalBinningProcessor.
        
        Args:
            column_name: Name of the numerical column to be binned.
            n_bins: Number of bins to create.
            strategy: Binning strategy. Must be 'quantile' or 'equal-width'.
            bin_labels: Optional.
                - If a list of strings, these are used as bin labels (length must equal n_bins).
                - If True, default labels "Bin_0", "Bin_1", ... are used.
                - If False, interval notation from pd.cut is used as labels.
                - If None (default), default labels "Bin_0", "Bin_1", ... are used.
            output_column_name: Optional name for the new column containing binned values.
                                If None, the original column is replaced (if input is DataFrame).
            handle_missing_value: How to label NaN input values.
                                  "as_is" (default): output will be NaN.
                                  string: use this string as the label for NaNs.
            handle_out_of_range: How to label values outside the fitted range.
                                 "boundary_bins" (default): assign to the lowest or highest bin.
                                 string: use this string as the label for out-of-range values.
                                 (Note: "boundary_bins" is implicitly handled by pd.cut with include_lowest=True
                                 and by how edges are defined. For explicit label, further logic is needed if
                                 pd.cut itself doesn't place it in a boundary bin and results in NaN).
        """
        super().__init__()
        self.processor_name = 'numerical_binning_processor'
        self.function_name_list = ['process', 'transform', 'fit']
        
        if not isinstance(column_name, str) or not column_name:
            raise ValueError("column_name must be a non-empty string.")
        self.column_name = column_name

        if not isinstance(n_bins, int) or n_bins <= 0:
            raise ValueError("n_bins must be a positive integer.")
        self.n_bins_requested = n_bins # Store originally requested n_bins

        if strategy not in ['quantile', 'equal-width']:
            raise ValueError("strategy must be either 'quantile' or 'equal-width'.")
        self.strategy = strategy

        if bin_labels is not None and not isinstance(bin_labels, (list, bool)):
            raise ValueError("bin_labels must be a list of strings, boolean, or None.")
        # Validation of bin_labels length against n_bins is deferred to fit(),
        # as actual n_bins might change due to data distribution.
        self.bin_labels_config = bin_labels
        
        self.output_column_name = output_column_name if output_column_name else f"{self.column_name}_binned"

        if not isinstance(handle_missing_value, str):
            raise ValueError("handle_missing_value must be a string (e.g., 'as_is', 'Missing').")
        self.handle_missing_value = handle_missing_value

        if not isinstance(handle_out_of_range, str):
            raise ValueError("handle_out_of_range must be a string (e.g., 'boundary_bins', 'OutOfRange').")
        self.handle_out_of_range = handle_out_of_range


        self.bin_edges_: Optional[np.ndarray] = None
        self.actual_labels_: Optional[Union[List[str], bool]] = None
        self.n_bins_actual_: Optional[int] = None # Actual number of bins created
        self.min_fitted_value_: Optional[float] = None
        self.max_fitted_value_: Optional[float] = None
        self.is_fitted = False

    def fit(self, data: pd.DataFrame) -> 'NumericalBinningProcessor':
        """
        Fit the binning processor to the data to determine bin edges and actual labels.
        
        Args:
            data: Training DataFrame containing the numerical 'column_name'.
        """
        if not isinstance(data, pd.DataFrame):
            raise TypeError("fit() requires a pandas DataFrame.")
        if self.column_name not in data.columns:
            raise ValueError(f"Column '{self.column_name}' not found in input data for fitting.")
        
        column_data = data[self.column_name].dropna()
        if column_data.empty:
            raise ValueError(f"Column '{self.column_name}' has no valid data after dropping NaNs for fitting.")
        if not pd.api.types.is_numeric_dtype(column_data):
            raise ValueError(f"Column '{self.column_name}' must be numeric for binning.")

        self.min_fitted_value_ = column_data.min()
        self.max_fitted_value_ = column_data.max()

        current_strategy = self.strategy # Allow fallback
        n_bins_to_try = self.n_bins_requested

        if current_strategy == 'quantile':
            try:
                if column_data.nunique() < n_bins_to_try:
                    print(f"Warning: Column '{self.column_name}' has fewer unique values ({column_data.nunique()}) "
                          f"than requested n_bins ({n_bins_to_try}). Quantile binning might result in fewer bins.")
                _, self.bin_edges_ = pd.qcut(column_data, n_bins_to_try, retbins=True, duplicates='drop')
            except ValueError as e: 
                print(f"Warning: Quantile binning failed for column '{self.column_name}' with {n_bins_to_try} bins (reason: {e}). "
                      f"Falling back to equal-width binning.")
                current_strategy = 'equal-width' 
        
        if current_strategy == 'equal-width': 
            if self.min_fitted_value_ == self.max_fitted_value_:
                 if n_bins_to_try == 1:
                    self.bin_edges_ = np.array([self.min_fitted_value_ - 0.5, self.max_fitted_value_ + 0.5]) \
                                      if self.min_fitted_value_ is not None else np.array([-np.inf, np.inf])
                 else: 
                    print(f"Warning: Column '{self.column_name}' has a single unique value. Creating one bin.")
                    self.bin_edges_ = np.array([self.min_fitted_value_ - 0.5, self.max_fitted_value_ + 0.5]) \
                                      if self.min_fitted_value_ is not None else np.array([-np.inf, np.inf])
            else:
                _, self.bin_edges_ = pd.cut(column_data, bins=n_bins_to_try, retbins=True, include_lowest=True, right=True)
        
        self.bin_edges_ = np.unique(self.bin_edges_)
        
        self.n_bins_actual_ = len(self.bin_edges_) - 1
        if self.n_bins_actual_ <= 0: 
            raise ValueError(f"Could not create valid bins for column '{self.column_name}'. "
                             f"Actual bins created: {self.n_bins_actual_}. Check data distribution.")

        if self.n_bins_actual_ != self.n_bins_requested:
            print(f"Warning: Number of bins for column '{self.column_name}' was adjusted from {self.n_bins_requested} "
                  f"to {self.n_bins_actual_} due to data distribution or strategy constraints.")

        if isinstance(self.bin_labels_config, list):
            if len(self.bin_labels_config) == self.n_bins_actual_:
                self.actual_labels_ = self.bin_labels_config
            else:
                print(f"Warning: Provided bin_labels length ({len(self.bin_labels_config)}) "
                      f"does not match the actual number of bins ({self.n_bins_actual_}). Using default labels.")
                self.actual_labels_ = [f"Bin_{i}" for i in range(self.n_bins_actual_)]
        elif self.bin_labels_config is True or self.bin_labels_config is None:
            self.actual_labels_ = [f"Bin_{i}" for i in range(self.n_bins_actual_)]
        elif self.bin_labels_config is False: 
            self.actual_labels_ = False 
            
        self.is_fitted = True
        return self

    def process(self, input_value: Union[int, float, np.number]) -> Optional[str]:
        """
        Process a single numerical input value, mapping it to its categorical bin label.
        
        Args:
            input_value: Single numerical value to process.
            
        Returns:
            Categorical bin label as a string, or a pre-configured label for NaN/OutOfRange, or None.
        """
        if not self.is_fitted:
            raise RuntimeError("NumericalBinningProcessor must be fitted before processing.")
        
        if pd.isna(input_value):
            return self.handle_missing_value if self.handle_missing_value != "as_is" else None
        
        value_series = pd.Series([input_value])
        
        binned_result = pd.cut(
            value_series, 
            bins=self.bin_edges_, 
            labels=self.actual_labels_, 
            include_lowest=True, 
            right=True
        )
        
        binned_label = binned_result[0]

        if pd.isna(binned_label): 
            if self.handle_out_of_range != "boundary_bins": 
                if self.min_fitted_value_ is not None and self.max_fitted_value_ is not None and \
                   (input_value < self.min_fitted_value_ or input_value > self.max_fitted_value_):
                    return self.handle_out_of_range
            return None 
            
        return str(binned_label)


    def transform(self, data: Union[pd.DataFrame, pd.Series]) -> Union[pd.DataFrame, pd.Series]:
        """
        Transform numerical data into categorical bins.
        
        Args:
            data: Input data (DataFrame or Series) to transform.
                  If DataFrame, operates on 'self.column_name'.
                  If Series, operates on the Series directly.
            
        Returns:
            Transformed data with binned categories.
            If input is DataFrame, a new column (or replaced original) with binned values.
            If input is Series, a new Series with binned values.
        """
        if not self.is_fitted:
            raise RuntimeError("NumericalBinningProcessor must be fitted before transforming.")

        if isinstance(data, pd.DataFrame):
            if self.column_name not in data.columns:
                raise ValueError(f"Column '{self.column_name}' not found in input DataFrame for transform.")
            
            series_to_bin = data[self.column_name]
            output_df = data.copy()
            
            binned_series = pd.cut(
                series_to_bin,
                bins=self.bin_edges_,
                labels=self.actual_labels_,
                include_lowest=True,
                right=True
            )

            if self.handle_missing_value != "as_is":
                binned_series[series_to_bin.isna()] = self.handle_missing_value
            
            if self.handle_out_of_range != "boundary_bins":
                out_of_range_mask = series_to_bin.notna() & binned_series.isna()
                if self.min_fitted_value_ is not None and self.max_fitted_value_ is not None:
                     # More precise out-of-range check based on fitted values
                    true_out_of_range = (series_to_bin < self.min_fitted_value_) | (series_to_bin > self.max_fitted_value_)
                    out_of_range_mask = out_of_range_mask | (series_to_bin.notna() & true_out_of_range)
                binned_series[out_of_range_mask] = self.handle_out_of_range
            
            # Ensure the output is string type if labels were strings, or category if intervals
            output_type = str if self.actual_labels_ is not False else 'category'
            output_df[self.output_column_name] = binned_series.astype(output_type)
            
            return output_df

        elif isinstance(data, pd.Series):
            series_to_bin = data
            binned_series = pd.cut(
                series_to_bin,
                bins=self.bin_edges_,
                labels=self.actual_labels_,
                include_lowest=True,
                right=True
            )
            if self.handle_missing_value != "as_is":
                binned_series[series_to_bin.isna()] = self.handle_missing_value
            if self.handle_out_of_range != "boundary_bins":
                out_of_range_mask = series_to_bin.notna() & binned_series.isna()
                if self.min_fitted_value_ is not None and self.max_fitted_value_ is not None:
                    true_out_of_range = (series_to_bin < self.min_fitted_value_) | (series_to_bin > self.max_fitted_value_)
                    out_of_range_mask = out_of_range_mask | (series_to_bin.notna() & true_out_of_range)
                binned_series[out_of_range_mask] = self.handle_out_of_range
            
            output_type = str if self.actual_labels_ is not False else 'category'
            return binned_series.astype(output_type)
        else:
            raise TypeError("Transform input must be a pandas DataFrame or Series.")

    def get_params(self) -> Dict:
        """Get processor parameters."""
        return {
            "column_name": self.column_name,
            "n_bins_requested": self.n_bins_requested,
            "n_bins_actual": self.n_bins_actual_,
            "strategy": self.strategy,
            "bin_labels_config": self.bin_labels_config,
            "output_column_name": self.output_column_name,
            "handle_missing_value": self.handle_missing_value,
            "handle_out_of_range": self.handle_out_of_range,
            "bin_edges": self.bin_edges_.tolist() if self.bin_edges_ is not None else None,
            "actual_labels": self.actual_labels_ if isinstance(self.actual_labels_, list) else str(self.actual_labels_),
            "min_fitted_value": self.min_fitted_value_,
            "max_fitted_value": self.max_fitted_value_
        }

    def save_params(self, output_dir: Union[str, Path]) -> None:
        """Save fitted parameters (bin_edges, labels, etc.) to a JSON file."""
        if not self.is_fitted:
            raise RuntimeError("Processor must be fitted before saving parameters.")
        
        output_dir_path = Path(output_dir)
        output_dir_path.mkdir(parents=True, exist_ok=True)
        
        params_to_save = self.get_params()
        
        filepath = output_dir_path / f"{self.processor_name}_{self.column_name}_params.json"
        with open(filepath, 'w') as f:
            json.dump(params_to_save, f, indent=4)
        print(f"Parameters for '{self.column_name}' saved to {filepath}")

    @classmethod
    def load_params(cls, source: Union[str, Path, Dict]) -> 'NumericalBinningProcessor':
        """
        Load parameters from a JSON file or a dictionary and initialize a new processor instance.
        
        Args:
            source: Filepath (str or Path) to the JSON parameter file, or a Dict containing the parameters.
        """
        params: Dict
        if isinstance(source, dict):
            params = source
            print(f"Parameters loaded directly from dictionary for column '{params.get('column_name', 'Unknown')}'.")
        elif isinstance(source, (str, Path)):
            filepath_path = Path(source)
            if not filepath_path.exists():
                raise FileNotFoundError(f"Parameter file not found: {filepath_path}")
            with open(filepath_path, 'r') as f:
                params = json.load(f)
            print(f"Parameters loaded from file {filepath_path}")
        else:
            raise TypeError("source must be a filepath (str or Path) or a dictionary.")
        
        required_keys = ["column_name", "n_bins_requested", "strategy", "bin_edges", "actual_labels"]
        if not all(key in params for key in required_keys):
            missing = [key for key in required_keys if key not in params]
            raise ValueError(f"Loaded parameters are missing required keys: {missing}")

        processor = cls(
            column_name=params["column_name"],
            n_bins=params["n_bins_requested"],
            strategy=params["strategy"],
            bin_labels=params.get("bin_labels_config"),
            output_column_name=params.get("output_column_name"),
            handle_missing_value=params.get("handle_missing_value", "as_is"),
            handle_out_of_range=params.get("handle_out_of_range", "boundary_bins")
        )
        
        processor.bin_edges_ = np.array(params["bin_edges"]) if params["bin_edges"] is not None else None
        
        loaded_actual_labels = params["actual_labels"]
        if isinstance(loaded_actual_labels, str) and loaded_actual_labels.lower() == 'false':
            processor.actual_labels_ = False
        elif loaded_actual_labels is None and isinstance(params.get("bin_labels_config"), bool) and not params.get("bin_labels_config"):
             # If original config was False for labels, and actual_labels stored as 'False' string or None
            processor.actual_labels_ = False
        else:
            processor.actual_labels_ = loaded_actual_labels

        processor.n_bins_actual_ = params.get("n_bins_actual")
        processor.min_fitted_value_ = params.get("min_fitted_value")
        processor.max_fitted_value_ = params.get("max_fitted_value")
        
        if processor.bin_edges_ is not None:
            processor.is_fitted = True
        
        return processor
```



## Relate Processor

- [[Processor Risk Table Mapping]]


-----------
##  Recommended Notes


- [[Binning - Partition a field into bins and show the size of each bin]]