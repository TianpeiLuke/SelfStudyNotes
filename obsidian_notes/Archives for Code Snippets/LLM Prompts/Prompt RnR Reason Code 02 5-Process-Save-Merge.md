---
tags:
  - code
  - code_snippet
  - prompt
  - large_language_models
  - python/aws_cdk
  - python/multithread
  - parallel_computing
keywords: 
topics: 
language: python
date of note: 2025-03-27
---

## Code Snippet Summary

![[Prompt RnR Reason Code 02 0-Main#^602eda]]

>[!important]
>This step following the steps before
>- Prompt [[Prompt RnR Reason Code 02 0-Main]]
>- Invoke [[Invoke Bedrock with Exponential Backoff]]
>- Parse [[Prompt RnR Reason Code 02 1-Parse]]
>- Batch Processing [[Prompt RnR Reason Code 02 2-Batch Processing]]
>- Partition Output into Chunks and Save [[Prompt RnR Reason Code 02 3-Save Chunks]]
>
>This step, we include both batch processing and partition save into one function

## Code

### Process, Save and Merge Chunks

```python
from pathlib import Path
import pandas as pd
import pyarrow as pa
import pyarrow.parquet as pq
from datetime import datetime
from typing import List, Union, Optional
from tqdm import tqdm
import os
```

```python
def process_and_merge_results(
    df: pd.DataFrame,
    base_dir: str,
    batch_size: int = 10,
    partition_cols: List[str] = None
) -> pd.DataFrame:
    """
    Complete workflow to process data, save batches, and merge results
    """
    try:
        # Create directories with timestamp to avoid conflicts
        timestamp = datetime.now().strftime('%Y%m%d_%H%M%S')
        batch_dir = os.path.join(base_dir, "batches", timestamp)
        merged_dir = os.path.join(base_dir, "merged")
        
        os.makedirs(batch_dir, exist_ok=True)
        os.makedirs(merged_dir, exist_ok=True)
        
        # Process batches
        processed_df = batch_process_dataframe(
            df=df,
            batch_size=batch_size,
            max_workers=5,
            max_retries=5
        )
        
        # Save batch results
        batch_id = datetime.now().strftime('%Y%m%d')
        saved_path = save_batch_results(
            df=processed_df,
            base_dir=batch_dir,
            batch_id=batch_id,
            partition_cols=partition_cols
        )
        print(f"Batch saved to: {saved_path}")
        
        # Wait a moment to ensure file system sync
        time.sleep(1)
        
        # Merge all results
        merged_df = merge_batch_results(
            base_dir=batch_dir,
            output_dir=merged_dir,
            pattern="batch_*.parquet",
            partition_cols=partition_cols
        )
        
        return merged_df
        
    except Exception as e:
        print(f"Error in processing workflow: {str(e)}")
        raise
```

- [[Prompt RnR Reason Code 02 2-Batch Processing]]
- [[Prompt RnR Reason Code 02 3-Save Chunks]]
- [[Prompt RnR Reason Code 02 4-Merge Chunks]]






-----------
##  Recommended Notes

- [[RnR Flag Definitions]]
- [[Example DNR]]