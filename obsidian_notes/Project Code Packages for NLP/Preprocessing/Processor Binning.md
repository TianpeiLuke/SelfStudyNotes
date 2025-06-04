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
        strategy: str = 'quantile', 
        bin_labels: Optional[Union[List[str], bool]] = None, 
        output_column_name: Optional[str] = None, 
        handle_missing_value: Optional[str] = "as_is", 
        handle_out_of_range: Optional[str] = "boundary_bins" 
    ):
        super().__init__()
        self.processor_name = 'numerical_binning_processor'
        self.function_name_list = ['process', 'transform', 'fit']
        
        if not isinstance(column_name, str) or not column_name:
            raise ValueError("column_name must be a non-empty string.")
        self.column_name = column_name

        if not isinstance(n_bins, int) or n_bins <= 0:
            raise ValueError("n_bins must be a positive integer.")
        self.n_bins_requested = n_bins

        if strategy not in ['quantile', 'equal-width']:
            raise ValueError("strategy must be either 'quantile' or 'equal-width'.")
        self.strategy = strategy

        if bin_labels is not None and not isinstance(bin_labels, (list, bool)):
            raise ValueError("bin_labels must be a list of strings, boolean, or None.")
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
        self.n_bins_actual_: Optional[int] = None 
        self.min_fitted_value_: Optional[float] = np.nan # Initialize to nan
        self.max_fitted_value_: Optional[float] = np.nan # Initialize to nan
        self.is_fitted = False

    def fit(self, data: pd.DataFrame) -> 'NumericalBinningProcessor':
        if not isinstance(data, pd.DataFrame):
            raise TypeError("fit() requires a pandas DataFrame.")
        if self.column_name not in data.columns:
            raise ValueError(f"Column '{self.column_name}' not found in input data for fitting.")
        
        column_data = data[self.column_name].dropna()
        if column_data.empty:
            logger.warning(f"Column '{self.column_name}' has no valid data after dropping NaNs for fitting. "
                           "Processor will be fitted with a single default bin covering all values.")
            self.min_fitted_value_ = np.nan 
            self.max_fitted_value_ = np.nan
            self.bin_edges_ = np.array([-np.inf, np.inf]) 
            self.n_bins_actual_ = 1
            if isinstance(self.bin_labels_config, list) and len(self.bin_labels_config) == 1:
                self.actual_labels_ = self.bin_labels_config
            elif self.bin_labels_config is True or self.bin_labels_config is None:
                self.actual_labels_ = ["Bin_0"]
            elif self.bin_labels_config is False:
                self.actual_labels_ = False
            else: 
                logger.warning(f"Bin labels config '{self.bin_labels_config}' incompatible with single bin for empty/NaN data. Using default 'Bin_0'.")
                self.actual_labels_ = ["Bin_0"]
            self.is_fitted = True
            return self

        self.min_fitted_value_ = float(column_data.min())
        self.max_fitted_value_ = float(column_data.max())

        current_strategy = self.strategy
        n_bins_to_try = self.n_bins_requested

        if current_strategy == 'quantile':
            try:
                if column_data.nunique() < n_bins_to_try:
                    logger.warning(f"Column '{self.column_name}' has fewer unique values ({column_data.nunique()}) "
                                   f"than requested n_bins ({n_bins_to_try}). Quantile binning might result in fewer bins.")
                _, self.bin_edges_ = pd.qcut(column_data, n_bins_to_try, retbins=True, duplicates='drop')
            except ValueError as e: 
                logger.warning(f"Quantile binning failed for column '{self.column_name}' with {n_bins_to_try} bins (reason: {e}). "
                               f"Falling back to equal-width binning.")
                current_strategy = 'equal-width' 
        
        if current_strategy == 'equal-width': 
            if self.min_fitted_value_ == self.max_fitted_value_:
                 logger.warning(f"Column '{self.column_name}' has a single unique value ({self.min_fitted_value_}). Creating one bin encompassing this value.")
                 epsilon = 1e-9 if abs(self.min_fitted_value_) < 1e-9 else abs(self.min_fitted_value_ * 1e-6)
                 epsilon = max(epsilon, 1e-9) 
                 self.bin_edges_ = np.array([self.min_fitted_value_ - epsilon, self.max_fitted_value_ + epsilon])
            else:
                _, self.bin_edges_ = pd.cut(column_data, bins=n_bins_to_try, retbins=True, include_lowest=True, right=True)
        
        self.bin_edges_ = np.unique(self.bin_edges_)
        
        self.n_bins_actual_ = len(self.bin_edges_) - 1
        if self.n_bins_actual_ <= 0: 
            logger.warning(f"Could not create valid bins for column '{self.column_name}' (actual bins: {self.n_bins_actual_}). Defaulting to a single overarching bin.")
            self.bin_edges_ = np.array([-np.inf, np.inf])
            self.n_bins_actual_ = 1

        if self.n_bins_actual_ != self.n_bins_requested:
            logger.warning(f"Number of bins for column '{self.column_name}' was adjusted from {self.n_bins_requested} "
                           f"to {self.n_bins_actual_} due to data distribution or strategy constraints.")

        if isinstance(self.bin_labels_config, list):
            if len(self.bin_labels_config) == self.n_bins_actual_:
                self.actual_labels_ = self.bin_labels_config
            else:
                logger.warning(f"Provided bin_labels length ({len(self.bin_labels_config)}) "
                               f"does not match the actual number of bins ({self.n_bins_actual_}). Using default labels.")
                self.actual_labels_ = [f"Bin_{i}" for i in range(self.n_bins_actual_)]
        elif self.bin_labels_config is True or self.bin_labels_config is None:
            self.actual_labels_ = [f"Bin_{i}" for i in range(self.n_bins_actual_)]
        elif self.bin_labels_config is False: 
            self.actual_labels_ = False 
            
        self.is_fitted = True
        return self

    def process(self, input_value: Union[int, float, np.number]) -> Optional[str]:
        if not self.is_fitted:
            raise RuntimeError("NumericalBinningProcessor must be fitted before processing.")
        
        if pd.isna(input_value):
            return self.handle_missing_value if self.handle_missing_value != "as_is" else None
        
        val = float(input_value)

        is_out_of_fitted_range = False
        if not pd.isna(self.min_fitted_value_) and not pd.isna(self.max_fitted_value_):
            if val < self.min_fitted_value_ or val > self.max_fitted_value_:
                is_out_of_fitted_range = True
        
        if is_out_of_fitted_range and self.handle_out_of_range != "boundary_bins":
            return self.handle_out_of_range
        
        binned_series = pd.cut(
            pd.Series([val]), 
            bins=self.bin_edges_, 
            labels=self.actual_labels_, 
            include_lowest=True, 
            right=True
        )
        binned_label = binned_series[0]

        if pd.isna(binned_label): # Value didn't fall into any bin from pd.cut
            if self.handle_out_of_range == "boundary_bins" and isinstance(self.actual_labels_, list) and self.n_bins_actual_ > 0:
                if val <= self.bin_edges_[0]: # Catches values below or equal to the first edge
                    return str(self.actual_labels_[0])
                # For values > last edge, pd.cut with include_lowest=True and right=True on a single value
                # should place it in the last bin if labels are provided.
                # If it's still NaN, it implies it was truly outside even the last bin's extended range.
                # Or if only one bin [-inf, inf], it should be caught.
                # This explicit check for > last edge might be redundant if pd.cut handles it.
                # However, if labels=False, pd.cut can create an interval like (edge_n-1, edge_n],
                # and a value exactly on edge_n-1 might be an issue if not include_lowest on that specific interval.
                # For safety with "boundary_bins":
                if val >= self.bin_edges_[-1]: # Check if it's at or beyond the last edge
                     # If it's exactly on the last edge, pd.cut (right=True) includes it in the last bin.
                     # If it's greater, it should also be in the last bin conceptually for "boundary_bins".
                    return str(self.actual_labels_[-1])

            # If still NaN and not handled by boundary_bins logic above, or if not boundary_bins
            if is_out_of_fitted_range and self.handle_out_of_range != "boundary_bins": # Should have been caught earlier
                 return self.handle_out_of_range # Redundant but safe
            return None # Default for unbinnable values
            
        return str(binned_label)


    def transform(self, data: Union[pd.DataFrame, pd.Series]) -> Union[pd.DataFrame, pd.Series]:
        if not self.is_fitted:
            raise RuntimeError("NumericalBinningProcessor must be fitted before transforming.")

        output_data: Union[pd.DataFrame, pd.Series]
        series_to_bin: pd.Series

        if isinstance(data, pd.DataFrame):
            if self.column_name not in data.columns:
                raise ValueError(f"Column '{self.column_name}' not found in input DataFrame for transform.")
            series_to_bin = data[self.column_name].copy()
            output_data = data.copy()
        elif isinstance(data, pd.Series):
            series_to_bin = data.copy()
            output_data = series_to_bin 
        else:
            raise TypeError("Transform input must be a pandas DataFrame or Series.")

        original_nan_mask = series_to_bin.isna()

        binned_series_cat = pd.cut(
            series_to_bin.dropna(), # Apply cut only on non-NaN values first
            bins=self.bin_edges_,
            labels=self.actual_labels_,
            include_lowest=True,
            right=True
        )
        
        # Initialize final binned series with object dtype to allow various assignments
        final_binned_series = pd.Series(index=series_to_bin.index, dtype=object)
        final_binned_series[series_to_bin.notna()] = binned_series_cat

        # 1. Handle original NaNs
        if self.handle_missing_value != "as_is":
            final_binned_series[original_nan_mask] = self.handle_missing_value
        else:
            final_binned_series[original_nan_mask] = np.nan # Explicitly keep as NaN

        # 2. Handle out-of-range values (that were not NaN originally but might be NaN after cut, or outside fitted range)
        if not pd.isna(self.min_fitted_value_) and not pd.isna(self.max_fitted_value_):
            # Identify values that were originally numbers but are outside the fitted range
            true_out_of_range_mask = ~original_nan_mask & \
                                     ((series_to_bin < self.min_fitted_value_) | \
                                      (series_to_bin > self.max_fitted_value_))
        else: # No valid fit range, assume nothing is out of range based on fit
            true_out_of_range_mask = pd.Series([False] * len(series_to_bin), index=series_to_bin.index)

        if self.handle_out_of_range == "boundary_bins":
            if isinstance(self.actual_labels_, list) and self.n_bins_actual_ > 0:
                # Assign values below min_fitted to the first bin's label
                final_binned_series[~original_nan_mask & (series_to_bin < self.min_fitted_value_)] = self.actual_labels_[0]
                # Assign values above max_fitted to the last bin's label
                final_binned_series[~original_nan_mask & (series_to_bin > self.max_fitted_value_)] = self.actual_labels_[-1]
        else: # Custom string label for out-of-range
            final_binned_series[true_out_of_range_mask] = self.handle_out_of_range
        
        # Values that were numeric, within fitted range, but still NaN after cut (edge cases)
        # These are rare if bins cover the fitted range.
        still_nan_after_cut_mask = series_to_bin.notna() & final_binned_series.isna() & ~true_out_of_range_mask
        if self.handle_out_of_range == "boundary_bins" and isinstance(self.actual_labels_, list) and self.n_bins_actual_ > 0:
            # Attempt to place these into boundary bins as a last resort if they are near edges
            final_binned_series.loc[still_nan_after_cut_mask & (series_to_bin <= self.bin_edges_[0])] = self.actual_labels_[0]
            final_binned_series.loc[still_nan_after_cut_mask & (series_to_bin >= self.bin_edges_[-1])] = self.actual_labels_[-1]
        elif self.handle_out_of_range != "boundary_bins":
             final_binned_series.loc[still_nan_after_cut_mask] = self.handle_out_of_range


        # Determine final output type
        if self.actual_labels_ is False: # Interval notation
            # Convert to CategoricalDtype, NaNs will be pd.NA
            final_binned_series = pd.Series(final_binned_series, dtype='category')
            if self.handle_missing_value == "as_is":
                 final_binned_series = final_binned_series. όπου(original_nan_mask, pd.NA)

        else: # String labels
            # Convert to string, NaNs will become "nan" or the custom missing label
            # If handle_missing_value was "as_is", we want actual NaNs to become "nan" string
            # If it was a custom string, it's already set.
            final_binned_series = final_binned_series.astype(str)
            if self.handle_missing_value == "as_is":
                final_binned_series[original_nan_mask] = "nan" # Explicitly make it "nan" string for consistency

        if isinstance(output_data, pd.DataFrame):
            output_data[self.output_column_name] = final_binned_series
            return output_data
        else: 
            return final_binned_series


    def get_params(self) -> Dict:
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
        if not self.is_fitted:
            raise RuntimeError("Processor must be fitted before saving parameters.")
        
        output_dir_path = Path(output_dir)
        output_dir_path.mkdir(parents=True, exist_ok=True)
        params_to_save = self.get_params()
        filepath = output_dir_path / f"{self.processor_name}_{self.column_name}_params.json"
        with open(filepath, 'w') as f:
            json.dump(params_to_save, f, indent=4)
        logger.info(f"Parameters for '{self.column_name}' saved to {filepath}")

    @classmethod
    def load_params(cls, source: Union[str, Path, Dict]) -> 'NumericalBinningProcessor':
        params: Dict
        if isinstance(source, dict):
            params = source
            logger.info(f"Parameters loaded directly from dictionary for column '{params.get('column_name', 'Unknown')}'.")
        elif isinstance(source, (str, Path)):
            filepath_path = Path(source)
            if not filepath_path.exists():
                raise FileNotFoundError(f"Parameter file not found: {filepath_path}")
            with open(filepath_path, 'r') as f:
                params = json.load(f)
            logger.info(f"Parameters loaded from file {filepath_path}")
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
            processor.actual_labels_ = False
        else:
            processor.actual_labels_ = loaded_actual_labels

        processor.n_bins_actual_ = params.get("n_bins_actual")
        processor.min_fitted_value_ = params.get("min_fitted_value")
        processor.max_fitted_value_ = params.get("max_fitted_value")
        
        if processor.bin_edges_ is not None and processor.n_bins_actual_ is not None : 
            processor.is_fitted = True
        
        return processor
```



## Relate Processor

- [[Processor Risk Table Mapping]]


-----------
##  Recommended Notes


- [[Binning - Partition a field into bins and show the size of each bin]]