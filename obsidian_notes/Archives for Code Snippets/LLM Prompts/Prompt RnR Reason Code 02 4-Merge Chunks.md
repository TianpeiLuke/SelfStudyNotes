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
>In this step, we merge the partitioned output into one parquet file


## Code

- [[Prompt RnR Reason Code 02 3-Save Chunks]]
### Merge Chunks

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
def merge_batch_results(
    base_dir: str,
    output_dir: str,
    pattern: str = "batch_*.parquet",
    exclude_patterns: List[str] = None,
    partition_cols: List[str] = None,
    compression: str = 'snappy'
) -> pd.DataFrame:
    """
    Merge all batch results into a single parquet file
    """
    try:
        input_path = Path(base_dir)
        output_path = Path(output_dir)
        output_path.mkdir(parents=True, exist_ok=True)
        
        # Get list of batch files - search recursively and handle both file and directory cases
        files = []
        # Look for direct parquet files
        files.extend(list(input_path.glob(pattern)))
        # Look for partitioned directories
        files.extend(list(input_path.glob("batch_*")))
        
        if not files:
            print(f"Searching in: {input_path}")
            print(f"Current files in directory: {list(input_path.iterdir())}")
            raise ValueError(f"No files found matching pattern '{pattern}' in {input_path}")
            
        if exclude_patterns:
            for pattern in exclude_patterns:
                files = [f for f in files if pattern not in f.name]
        
        total_files = len(files)
        print(f"Found {total_files} batch files to merge")
        
        # Initialize progress bars
        pbar = tqdm(total=total_files, desc="Merging batches")
        
        # Process files
        dfs = []
        total_rows = 0
        errors = []
        
        for file in files:
            try:
                if file.is_file():
                    df = pd.read_parquet(file)
                else:  # Handle partitioned directories
                    df = pd.read_parquet(file)
                dfs.append(df)
                total_rows += len(df)
                pbar.update(1)
                print(f"Successfully read {file} with {len(df)} rows")
                
            except Exception as e:
                error_msg = f"Error reading {file}: {str(e)}"
                print(f"\nWarning: {error_msg}")
                errors.append(error_msg)
        
        if not dfs:
            raise ValueError("No data frames were successfully loaded")
            
        # Merge all DataFrames
        print("\nConcatenating results...")
        merged_df = pd.concat(dfs, ignore_index=True)
        
        # Save merged results
        timestamp = datetime.now().strftime('%Y%m%d_%H%M%S')
        final_path = output_path / f"merged_results_{timestamp}.parquet"
        
        print("Saving merged results...")
        if partition_cols:
            table = pa.Table.from_pandas(merged_df)
            pq.write_to_dataset(
                table,
                root_path=str(final_path).replace('.parquet', ''),
                partition_cols=partition_cols,
                compression=compression
            )
        else:
            merged_df.to_parquet(
                final_path,
                compression=compression,
                index=True
            )
        
        # Rest of the function remains the same...
        return merged_df
        
    except Exception as e:
        print(f"Critical error during merge: {str(e)}")
        raise
    finally:
        pbar.close()
```

### Add Stats as Summary 

```python
def merge_batch_results(
    base_dir: str,
    output_dir: str,
    pattern: str = "batch_*.parquet",
    exclude_patterns: List[str] = None,
    partition_cols: List[str] = None,
    compression: str = 'snappy'
) -> pd.DataFrame:
    """Merge all batch results into a single parquet file"""
    try:
        input_path = Path(base_dir)
        output_path = Path(output_dir)
        output_path.mkdir(parents=True, exist_ok=True)
        
        # Get list of unique batch files
        files = list(set(input_path.glob(pattern)))
        if not files:  # Try to find partitioned directories
            files = list(set(input_path.glob("batch_*")))
        
        if not files:
            raise ValueError(f"No files found matching pattern '{pattern}' in {input_path}")
        
        total_files = len(files)
        print(f"Found {total_files} batch files to merge")
        
        # Process files with progress bar
        pbar = tqdm(total=total_files, desc="Merging batches")
        dfs = []
        total_rows = 0
        errors = []
        
        for file in files:
            try:
                df = pd.read_parquet(file)
                dfs.append(df)
                total_rows += len(df)
                pbar.update(1)
                print(f"Successfully read {file} with {len(df)} rows")
            except Exception as e:
                error_msg = f"Error reading {file}: {str(e)}"
                print(f"\nWarning: {error_msg}")
                errors.append(error_msg)
        
        if not dfs:
            raise ValueError("No data frames were successfully loaded")
        
        # Merge results
        print("\nConcatenating results...")
        merged_df = pd.concat(dfs, ignore_index=True)
        
        # Save merged results
        timestamp = datetime.now().strftime('%Y%m%d_%H%M%S')
        final_path = output_path / f"merged_results_{timestamp}.parquet"
        
        print("Saving merged results...")
        if partition_cols:
            table = pa.Table.from_pandas(merged_df)
            pq.write_to_dataset(
                table,
                root_path=str(final_path).replace('.parquet', ''),
                partition_cols=partition_cols,
                compression=compression
            )
        else:
            merged_df.to_parquet(
                final_path,
                compression=compression,
                index=True
            )
        
        # Create statistics DataFrame
        stats_dict = {
            'metric': [
                'total_files',
                'files_processed',
                'total_rows',
                'error_count',
                'unique_categories',
                'avg_confidence',
                'processing_timestamp',
                'batch_directory',
                'output_directory'
            ],
            'string_value': [
                str(total_files),
                str(total_files - len(errors)),
                str(total_rows),
                str(len(errors)),
                str(merged_df['category'].nunique()),
                f"{merged_df['confidence_score'].mean():.4f}",
                timestamp,
                str(input_path),
                str(output_path)
            ]
        }
        
        # Create DataFrame with explicit string type
        stats_df = pd.DataFrame(stats_dict)
        
        # Save statistics
        stats_path = final_path.parent / f"merge_stats_{timestamp}.parquet"
        stats_df.to_parquet(
            stats_path,
            compression=compression,
            engine='pyarrow'
        )
        
        print("\nMerge Summary:")
        print("-" * 50)
        print(f"Total files processed: {total_files - len(errors)}/{total_files}")
        print(f"Total rows: {total_rows:,}")
        print(f"Categories found: {merged_df['category'].nunique()}")
        print(f"Average confidence score: {merged_df['confidence_score'].mean():.2f}")
        print(f"\nResults saved to: {final_path}")
        print(f"Statistics saved to: {stats_path}")
        
        if errors:
            print("\nErrors encountered:")
            for error in errors:
                print(f"- {error}")
        
        return merged_df
        
    except Exception as e:
        print(f"Critical error during merge: {str(e)}")
        raise
    finally:
        if 'pbar' in locals():
            pbar.close()
```





-----------
##  Recommended Notes

- [[RnR Flag Definitions]]
- [[Example DNR]]