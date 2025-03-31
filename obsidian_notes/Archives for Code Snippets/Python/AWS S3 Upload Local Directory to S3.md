---
tags:
  - code
  - code_snippet
  - aws/s3
  - python/aws_cdk
keywords: 
topics: 
language: python
date of note: 2025-03-30
---

## Code Snippet Summary

>[!important]
>Upload an entire folder and all subsequent structures into S3

## Code

### Upload Directory

```python
import os 
from datetime import datetime
from pathlib import Path
import pandas as pd
from typing import List, Union, Optional
```


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




-----------
##  Recommended Notes

- [[RnR Flag Definitions]]
- [[Example DNR]]





-----------
##  Recommended Notes

