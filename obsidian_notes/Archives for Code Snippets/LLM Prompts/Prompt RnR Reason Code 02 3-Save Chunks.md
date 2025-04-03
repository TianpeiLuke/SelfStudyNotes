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
>
>In this step, we save the formatted output from `BSMAnalysis` in [[Prompt RnR Reason Code 02 1-Parse]] into `parquet` files
>- Instead of saving one file, we split the output into chunks
>- Save chunks according to `partition`


## Code
### Run and Save Chunks to Parquet

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

- Save Batch
- Partition by `[reason, org]`

```python
def save_batch_results(
    df: pd.DataFrame,
    base_dir: str,
    batch_id: str,
    partition_cols: List[str] = None,
    compression: str = 'snappy'
) -> str:
    """
    Save batch results to parquet with proper handling of complex types
    
    Args:
        df: DataFrame to save
        base_dir: Base directory for saving results
        batch_id: Identifier for this batch
        partition_cols: Columns to partition by
        compression: Compression codec to use
    """
    try:
        save_path = Path(base_dir)
        save_path.mkdir(parents=True, exist_ok=True)
        
        # Create filename with timestamp
        timestamp = datetime.now().strftime('%Y%m%d_%H%M%S')
        filename = f"batch_{batch_id}_{timestamp}.parquet"
        final_path = save_path / filename
        
        # Convert list columns to strings
        df = df.copy()
        for col in df.select_dtypes(include=['object']).columns:
            if isinstance(df[col].iloc[0], list):
                df[col] = df[col].apply(lambda x: ';'.join(str(item) for item in x) if isinstance(x, list) else x)
        
        # Save to parquet
        if partition_cols:
            table = pa.Table.from_pandas(df)
            pq.write_to_dataset(
                table,
                root_path=str(final_path).replace('.parquet', ''),
                partition_cols=partition_cols,
                compression=compression
            )
        else:
            df.to_parquet(
                final_path,
                compression=compression,
                index=True
            )
        
        return str(final_path)
    
    except Exception as e:
        print(f"Error saving batch {batch_id}: {str(e)}")
        raise
```

### Merge Chunks

- [[Prompt RnR Reason Code 02 4-Merge Chunks]]



-----------
##  Recommended Notes

- [[RnR Flag Definitions]]
- [[2025-03-29 Example DNR]]