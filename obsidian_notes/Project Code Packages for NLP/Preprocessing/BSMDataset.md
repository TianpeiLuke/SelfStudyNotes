---
tags:
  - code
  - code_snippet
  - reversal_reclassification
  - buyer_seller_messaging
keywords: 
topics: 
language: python
date of note: 2025-04-09
---

## Code Snippet Summary

>[!important]
>Create a Dataset that load Processors as pipeline to do preprocess for each field
>- Child from `torch.utils.data.Dataset`
>- Dataset load from .csv, .tsv, or .parquet file
>- Dataset also load from `pandas.DataFrame`
>- Allow injection of Composite Processor as pipeline
>- Connect to Dataloader


## Code

```python
import os
import re
import numpy as np
import pandas as pd
import csv
from bs4 import BeautifulSoup
from typing import Union, List, Tuple, Dict, Set, Pattern, Optional
from collections.abc import Callable
from torch.utils.data import Dataset, IterableDataset, DataLoader
import torch
```

```python
from .processors import Processor
```

- [[Processors ver 2.0]]

### Definition

```python
class BSMDataset(Dataset):
    def __init__(self,
                 config: Dict[str, Union[str, List[str], int]],
                 file_dir: Optional[str] = None,
                 filename: Optional[str] = None,
                 dataframe: Optional[pd.DataFrame] = None,
                 processor_pipelines: Optional[Dict[str, Processor]] = None) -> None:
        """
        Initializes the BSMDataset with configuration and an optional dictionary of field-specific
        processing pipelines (composed via the __rshift__ operator).
        Args:
            config: Configuration dictionary (e.g. text_name, label_name, full_field_list).
            file_dir: Directory of data file.
            filename: Data file name.
            dataframe: Alternatively, a pandas DataFrame.
            processor_pipelines: Dictionary mapping field names to a composed Processor instance.
        """
        self.config = config
        self.header = self.config.get('header', 0)
        self.label_name = self.config.get('label_name', None)
        self.text_name = self.config.get('text_name', None)
        self.full_field_list = self.config.get('full_field_list', None)
        self.cat_field_list = self.config.get('cat_field_list', None)
        self.tab_field_list = self.config.get('tab_field_list', None)
        self.need_language_detect = self.config.get('need_language_detect', False)
        self.processor_pipelines = processor_pipelines if processor_pipelines is not None else {}
        self.DataReader = None

        if file_dir and filename:
            self.file_dir = file_dir
            self.filename = filename
            self.processed_filename = os.path.splitext(filename)[0] + "-processed" + os.path.splitext(filename)[1]
            ext = os.path.splitext(filename)[1]
            if ext == '.tsv':
                self.sep = '\t'
            elif ext == '.csv':
                self.sep = ','
            elif ext == '.parquet':
                self.sep = 'parquet'
            else:
                self.sep = ','
            self.load_data()
        elif dataframe is not None and isinstance(dataframe, pd.DataFrame):
            self.load_dataframe(dataframe)
        else:
            raise TypeError('Please provide either file directory/filename or a valid pandas.DataFrame.')

    def load_data(self, **kwargs):
        file_path = os.path.join(self.file_dir, self.filename)
        if self.sep == 'parquet':
            self.DataReader = pd.read_parquet(file_path)
        else:
            if self.full_field_list is None:
                self.DataReader = pd.read_csv(file_path, sep=self.sep, index_col=None)
            else:
                self.DataReader = pd.read_csv(file_path, header=0, names=self.full_field_list, sep=self.sep, index_col=None)

    def load_dataframe(self, dataframe):
        if dataframe is not None and isinstance(dataframe, pd.DataFrame):
            if self.full_field_list and len(self.full_field_list) == len(dataframe.columns):
                dataframe.columns = self.full_field_list
            self.DataReader = dataframe
        else:
            raise TypeError('Input must be a pandas.DataFrame.')

    def __len__(self):
        return len(self.DataReader)

    def add_pipeline(self, field_name: str, processor_pipeline: Processor):
        """
        Adds a processing pipeline (composed via __rshift__) for the given field.
        For example, for a 'dialogue' field, you might build a pipeline:
            pipeline = HTMLNormalizerProcessor() >> EmojiRemoverProcessor() >>
                       TextNormalizationProcessor() >> DialogueSplitterProcessor() >>
                       DialogueChunkerProcessor(tokenizer, max_tokens=512) >>
                       TokenizationProcessor(tokenizer, add_special_tokens=True)
        and then add it via: add_pipeline("dialogue", pipeline)
        """
        if isinstance(field_name, str) and isinstance(processor_pipeline, Processor):
            self.processor_pipelines[field_name] = processor_pipeline
        else:
            raise TypeError("Field name must be a string and processor_pipeline must be an instance of Processor.")

    def __getitem__(self, idx):
        if torch.is_tensor(idx):
            idx = idx.tolist()
        row = self.DataReader.iloc[idx, :].to_dict()
        # For each field with a pipeline, process the raw field data.
        for field_name, pipeline in self.processor_pipelines.items():
            if field_name in row:
                processed = pipeline(row[field_name])
                row[field_name + '_processed'] = processed
        return row
```




-----------
##  Recommended Notes

