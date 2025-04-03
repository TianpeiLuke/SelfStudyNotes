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

### Fixed Directory 

```python
def process_and_merge_results(
    df: pd.DataFrame,
    base_dir: str,
    s3_bucket: str,
    batch_size: int = 10,
    partition_cols: List[str] = None
) -> pd.DataFrame:
    """Complete workflow with improved error handling"""
    try:
        timestamp = datetime.now().strftime('%Y%m%d_%H%M%S')
        current_date = datetime.now().strftime('%Y%m%d')
        
        
        # CHANGE 1: Normalize base directory path
        base_dir = os.path.abspath(os.path.expanduser(base_dir))
        
        # Local directories
        batch_dir = os.path.join(base_dir, "batches", timestamp)
        merged_dir = os.path.join(base_dir, "merged", timestamp)
        
        # CHANGE 2: Add stats directory
        stats_dir = os.path.join(base_dir, "stats", timestamp)        
        
        # S3 prefixes
        s3_batch_prefix = f"llm_processed_data/{current_date}/batches/{timestamp}"
        s3_merged_prefix = f"llm_processed_data/{current_date}/merged/{timestamp}"
        # CHANGE 3: Add stats prefix
        s3_stats_prefix = f"llm_processed_data/{current_date}/stats/{timestamp}"
        
        
        # CHANGE 4: Create all directories at once
        for dir_path in [batch_dir, merged_dir, stats_dir]:
            os.makedirs(dir_path, exist_ok=True)

        # CHANGE 5: Add informative print statements
        print(f"\nProcessing {len(df)} rows in batches of {batch_size}")
        print(f"Using directories:")
        print(f"Batch dir: {batch_dir}")
        print(f"Merged dir: {merged_dir}")
            
        # Process batches
        processed_df = batch_process_dataframe(
            df=df,
            batch_size=batch_size,
            max_workers=5,
            max_retries=5
        )
        
        # Save and upload batch results
        batch_path = save_batch_results(
            df=processed_df,
            base_dir=batch_dir,
            batch_id=current_date,
            partition_cols=partition_cols
        )
        
        # CHANGE 6: Add file existence check and error handling
        if os.path.exists(batch_path):
            print(f"Batch file created successfully at: {batch_path}")
            
            if s3_bucket:
                print("\nUploading batch results to S3...")
                upload_success = upload_to_s3(
                    batch_path,
                    s3_bucket,
                    s3_batch_prefix
                )
                if upload_success:
                    print("Batch upload completed successfully")
                else:
                    print("Warning: Batch upload failed")
        else:
            print(f"Warning: Expected batch file not found at {batch_path}")
        
        # CHANGE 7: Add progress message
        print("\nMerging results...")
        merged_df = merge_batch_results(
            base_dir=batch_dir,
            output_dir=merged_dir,
            pattern="batch_*.parquet",  # CHANGE 8: Add explicit pattern
            partition_cols=partition_cols
        )
        
        # CHANGE 9: Improved S3 upload handling
        if s3_bucket:
            print("\nUploading merged results to S3...")
            merged_files = list(Path(merged_dir).glob("*.parquet"))
            print(f"Found {len(merged_files)} files to upload")
            
            for file in merged_files:
                if os.path.exists(file):
                    upload_to_s3(
                        file,
                        s3_bucket,
                        s3_merged_prefix
                    )
                else:
                    print(f"Warning: Merged file not found: {file}")
        
        # CHANGE 10: Move summary creation here and add error handling
        summary_df = pd.DataFrame({
            'category': merged_df['category'].value_counts().index,
            'count': merged_df['category'].value_counts().values,
            'avg_confidence': [
                merged_df[merged_df['category'] == cat]['confidence_score'].mean()
                for cat in merged_df['category'].value_counts().index
            ]
        })
        
        # CHANGE 11: Save summary to stats directory
        summary_path = os.path.join(stats_dir, f"results_summary_{timestamp}.csv")
        os.makedirs(os.path.dirname(summary_path), exist_ok=True)
        summary_df.to_csv(summary_path, index=False)
        
        
        # CHANGE 12: Upload summary with better error handling
        if s3_bucket and os.path.exists(summary_path):
            upload_to_s3(
                summary_path,
                s3_bucket,
                f"llm_processed_data/{current_date}/summary"
            )
        
        # CHANGE 13: Enhanced summary printing
        print("\nProcessing Summary:")
        print("-" * 50)
        print(f"Total rows processed: {len(merged_df)}")
        print("\nCategory Distribution:")
        print(merged_df['category'].value_counts())
        print(f"\nResults saved to:")
        print(f"- Local: {merged_dir}")
        print(f"- S3: s3://{s3_bucket}/{s3_merged_prefix}")
        
        return merged_df
        
    except Exception as e:
        print(f"Error in processing workflow: {str(e)}")
        raise
```




-----------
##  Recommended Notes

- [[RnR Flag Definitions]]
- [[2025-03-29 Example DNR]]