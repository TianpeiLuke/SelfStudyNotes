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


```python
def wait_for_s3_file(
    s3_path: str,
    timeout_seconds: int = 300,
    check_interval_seconds: int = 10,
    check_content: bool = False
) -> bool:
    """
    Wait for a file to appear in S3 with timeout.
    
    Args:
        s3_path: S3 path to check
        timeout_seconds: How long to wait before giving up
        check_interval_seconds: How often to check
        check_content: Whether to verify file has content
        
    Returns:
        bool: True if file exists within timeout, False otherwise
    """
    import time
    
    start_time = time.time()
    while (time.time() - start_time) < timeout_seconds:
        try:
            exists, _ = check_s3_file_exists(s3_path, check_content)
            if exists:
                return True
        except Exception as e:
            logger.warning(f"Error checking file: {str(e)}")
            
        time.sleep(check_interval_seconds)
        
    return False

```

- [[AWS S3 Check if S3 File Exist]]

### Usage

```python
# Usage examples
def main():
    # Setup logging
    logging.basicConfig(level=logging.INFO)
    
    # Example paths
    s3_path = "s3://my-bucket/path/to/file.txt"
    
    # Simple check
    try:
        exists, metadata = check_s3_file_exists(s3_path)
        if exists:
            print(f"File exists! Metadata: {metadata}")
        else:
            print("File does not exist")
    except Exception as e:
        print(f"Error checking file: {str(e)}")
        
    # Wait for file with timeout
    if wait_for_s3_file(s3_path, timeout_seconds=60):
        print("File appeared within timeout")
    else:
        print("File did not appear within timeout")

if __name__ == "__main__":
    main()

```




-----------
##  Recommended Notes

