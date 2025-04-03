---
tags:
  - code
  - code_snippet
  - prompt
  - large_language_models
  - python/aws_cdk
  - python/multithread
  - parallel_computing
  - aws/s3
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
>- [[Prompt RnR Reason Code 02 5-Process-Save-Merge]]
>	- Batch Processing [[Prompt RnR Reason Code 02 2-Batch Processing]]
>	- Partition Output into Chunks and Save [[Prompt RnR Reason Code 02 3-Save Chunks]]
>
>This step, we upload both partitioned files and folders as well as merged files to S3
>- Output S3 organization

```text
s3://buyer-seller-messaging-reversal/llm_processed_data/
└── YYYYMMDD/
    ├── batches/
    │   └── timestamp/
    │       └── batch files
    ├── merged/
    │   └── timestamp/
    │       └── merged files
    ├── stats/
    │   └── statistics files
    └── summary/
        └── summary files
```


## Code

### Upload folders and subfolders to S3

```python
import boto3
from botocore.exceptions import ClientError
import os
from datetime import datetime
```

### Upload file to S3

```python
def upload_to_s3(
    file_path: Union[str, Path],
    bucket: str,
    s3_prefix: str,
    content_type: str = 'application/octet-stream'
) -> bool:
    """
    Upload a file to S3
    
    Args:
        file_path: Local file path
        bucket: S3 bucket name
        s3_prefix: S3 object prefix (folder structure)
        content_type: File content type
    """
    try:
        s3_client = boto3.client('s3')
        file_path = Path(file_path)
        
        # Create S3 key (path)
        s3_key = f"{s3_prefix}/{file_path.name}"
        
        # Upload file
        s3_client.upload_file(
            str(file_path),
            bucket,
            s3_key,
            ExtraArgs={'ContentType': content_type}
        )
        
        print(f"Successfully uploaded {file_path.name} to s3://{bucket}/{s3_key}")
        return True
        
    except Exception as e:
        print(f"Error uploading to S3: {str(e)}")
        return False
```


### Upload Directory


```python
def upload_directory_to_s3(
    local_dir: Union[str, Path],
    bucket: str,
    s3_prefix: str
) -> List[str]:
    """
    Upload all files in a directory to S3
    
    Args:
        local_dir: Local directory path
        bucket: S3 bucket name
        s3_prefix: S3 object prefix (folder structure)
    """
    uploaded_files = []
    local_dir = Path(local_dir)
    
    try:
        for file_path in local_dir.rglob('*'):
            if file_path.is_file():
                # Create relative path for S3
                relative_path = file_path.relative_to(local_dir)
                s3_key = f"{s3_prefix}/{relative_path}"
                
                # Upload file
                if upload_to_s3(file_path, bucket, s3_prefix):
                    uploaded_files.append(s3_key)
                    
        return uploaded_files
        
    except Exception as e:
        print(f"Error uploading directory to S3: {str(e)}")
        return uploaded_files
```

- [[AWS S3 Upload Local Directory to S3]]

### Modified Process + Save + Merge

- [[Prompt RnR Reason Code 02 5-Process-Save-Merge]]

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
        
        # Local directories
        batch_dir = os.path.join(base_dir, "batches", timestamp)
        merged_dir = os.path.join(base_dir, "merged", timestamp)
        
        # S3 prefixes
        s3_batch_prefix = f"llm_processed_data/{current_date}/batches/{timestamp}"
        s3_merged_prefix = f"llm_processed_data/{current_date}/merged/{timestamp}"
        
        os.makedirs(batch_dir, exist_ok=True)
        os.makedirs(merged_dir, exist_ok=True)
        
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
        
        # Upload to S3
        if s3_bucket:
            upload_to_s3(
                batch_path,
                s3_bucket,
                s3_batch_prefix
            )
        
        # Merge results
        merged_df = merge_batch_results(
            base_dir=batch_dir,
            output_dir=merged_dir,
            partition_cols=partition_cols
        )
        
        # Upload merged results to S3
        if s3_bucket:
            for file in Path(merged_dir).glob("*.parquet"):
                upload_to_s3(
                    file,
                    s3_bucket,
                    s3_merged_prefix
                )
        
        return merged_df
        
    except Exception as e:
        print(f"Error in processing workflow: {str(e)}")
        raise
```


### Example

```python
try:
    # Set up parameters
    base_dir = f"/home/ec2-user/SageMaker/data/llm_results/"
    s3_bucket = "buyer-seller-messaging-reversal"
    partition_cols = ['category', 'org']
    
    # Process and upload
    merged_results = process_and_merge_results(
        df=fn_df.sample(200),
        base_dir=base_dir,
        s3_bucket=s3_bucket,
        batch_size=10,
        partition_cols=partition_cols
    )
    
    # Print summary
    print("\nProcessing Summary:")
    print("-" * 50)
    print(f"Total rows processed: {len(merged_results)}")
    print("\nCategory Distribution:")
    print(merged_results['category'].value_counts())
    
    # Optional: Save local summary
    summary_df = pd.DataFrame({
        'category': merged_results['category'].value_counts().index,
        'count': merged_results['category'].value_counts().values,
        'avg_confidence': [
            merged_results[merged_results['category'] == cat]['confidence_score'].mean()
            for cat in merged_results['category'].value_counts().index
        ]
    })
    
    timestamp = datetime.now().strftime('%Y%m%d_%H%M%S')
    summary_path = os.path.join(base_dir, "summary", f"results_summary_{timestamp}.csv")
    os.makedirs(os.path.dirname(summary_path), exist_ok=True)
    summary_df.to_csv(summary_path, index=False)
    
    # Upload summary to S3
    upload_to_s3(
        summary_path,
        s3_bucket,
        f"llm_processed_data/{datetime.now().strftime('%Y%m%d')}/summary"
    )

except Exception as e:
    print(f"Processing failed: {str(e)}")

```





-----------
##  Recommended Notes

- [[RnR Flag Definitions]]
- [[2025-03-29 Example DNR]]