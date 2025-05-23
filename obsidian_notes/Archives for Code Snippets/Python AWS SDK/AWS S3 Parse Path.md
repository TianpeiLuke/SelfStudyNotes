---
tags:
  - code
  - code_snippet
  - aws/s3
  - python/aws_python_sdk
keywords: 
topics: 
language: python
date of note: 2025-05-21
---

## Code Snippet Summary

>[!important]
>Given a S3 path `s3://bucket/key`, parse it into
>- bucket
>- key


## Code

```python
import boto3
from botocore.exceptions import ClientError
from pathlib import Path
import logging
from typing import Union, Tuple
from urllib.parse import urlparse

logger = logging.getLogger(__name__)
```

### Parse S3 Path

```python
def parse_s3_path(s3_path: str) -> Tuple[str, str]:
    """
    Parse S3 path into bucket and key.
    
    Args:
        s3_path: Full S3 path (s3://bucket/path/to/file)
        
    Returns:
        Tuple containing bucket and key
        
    Raises:
        ValueError: If path is not a valid S3 path
    """
    try:
        if s3_path.startswith('s3://'):
            parsed = urlparse(s3_path)
            bucket = parsed.netloc
            key = parsed.path.lstrip('/')
        else:
            parts = s3_path.split('/')
            bucket = parts[0]
            key = '/'.join(parts[1:])
            
        return bucket, key
    except Exception as e:
        raise ValueError(f"Invalid S3 path: {s3_path}. Error: {str(e)}")
```





-----------
##  Recommended Notes

- [[AWS S3 Check if S3 File Exist]]
- [[AWS S3 Wait for S3 File]]
- [[AWS S3 Upload Local Directory to S3]]