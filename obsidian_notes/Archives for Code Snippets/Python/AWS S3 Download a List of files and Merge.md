---
tags:
  - code
  - code_snippet
  - aws/s3
  - python/aws_cdk
keywords: 
topics: 
language: python
date of note: 2025-03-24
---

## Code Snippet Summary

>[!important]
>Assume a list of `.parquet` files in bucket `buckename`


## Code

```python
import boto3 
import pandas as pd 
import os 
from tqdm import tqdm 
```

- bucket
- prefix
- local folder

```python
# S3 configuration 
bucket_name = "bucket" 
prefix = "folder" 
local_dir = "local_dir" 
# Create local directory if it doesn't exist 
os.makedirs(local_dir, exist_ok=True) 
```

- Call s3 client using `boto3`

```python
# Initialize S3 client
s3_client = boto3.client('s3')
```

- List of all object under given prefix
	- [[AWS - retrieve the S3 bucket and file from S3 URL]]
	- call `get_paginator`

```python
# List all objects with the given prefix
def list_s3_files(bucket, prefix):
    paginator = s3_client.get_paginator('list_objects_v2')
    pages = paginator.paginate(Bucket=bucket, Prefix=prefix)
    
    files = []
    for page in pages:
        if 'Contents' in page:
            for obj in page['Contents']:
                if obj['Key'].endswith('.parquet'):
                    files.append(obj['Key'])
    return files

```

- Download file one by one, 
	- load into `pandas.DataFrame`
	- concatenate dataframe
	- delete downloaded file

```python
# Download files
def download_files(files):
    dataframes = []
    for file in tqdm(files, desc="Downloading and processing files"):
        local_file = os.path.join(local_dir, os.path.basename(file))
        
        # Download the file
        s3_client.download_file(bucket_name, file, local_file)
        
        # Read the parquet file
        df = pd.read_parquet(local_file)
        dataframes.append(df)
        
        # Remove the local file to save space
        os.remove(local_file)
        
    return dataframes
```

- Main file

```python
# Main execution
try:
    # Get list of all parquet files
    print("Listing S3 files...")
    s3_files = list_s3_files(bucket_name, prefix)
    
    if not s3_files:
        print("No parquet files found!")
        exit()
    
    print(f"Found {len(s3_files)} parquet files")
    
    # Download and process files
    print("Downloading and processing files...")
    dfs = download_files(s3_files)
    
    # Concatenate all dataframes
    print("Concatenating dataframes...")
    final_df = pd.concat(dfs, ignore_index=True)
    
    # Save the final concatenated file
    output_file = os.path.join(local_dir, "concatenated_file.parquet")
    print(f"Saving final file to {output_file}")
    final_df.to_parquet(output_file, index=False)
    
    print(f"Successfully processed {len(s3_files)} files")
    print(f"Final dataframe shape: {final_df.shape}")

except Exception as e:
    print(f"An error occurred: {str(e)}")

```





-----------
##  Recommended Notes

