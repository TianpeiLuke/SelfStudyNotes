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

### Parse Path

- [[AWS S3 Parse Path]]

### Check if S3 File Exist

```python
def check_s3_file_exists(
    s3_path: Union[str, Path],
    check_content: bool = False
) -> Tuple[bool, dict]:
    """
    Check if a file exists in S3 and optionally verify it has content.
    
    Args:
        s3_path: S3 path to check (can be string or Path object)
        check_content: If True, also verify file has non-zero size
        
    Returns:
        Tuple of (exists: bool, metadata: dict)
        
    Example:
        >>> exists, metadata = check_s3_file_exists('s3://my-bucket/path/to/file.txt')
        >>> if exists:
        >>>     print(f"File exists! Size: {metadata.get('ContentLength', 0)} bytes")
    """
    s3_path = str(s3_path)
    try:
        # Parse S3 path
        bucket, key = parse_s3_path(s3_path)
        
        # Initialize S3 client
        s3_client = boto3.client('s3')
        
        try:
            # Try to get object metadata
            response = s3_client.head_object(Bucket=bucket, Key=key)
            
            # Check if file has content if required
            if check_content:
                content_length = response.get('ContentLength', 0)
                if content_length == 0:
                    logger.warning(f"File exists but is empty: {s3_path}")
                    return False, response
                    
            logger.info(f"File exists in S3: {s3_path}")
            return True, response
            
        except ClientError as e:
            error_code = e.response.get('Error', {}).get('Code', '')
            
            if error_code == '404':
                logger.info(f"File does not exist in S3: {s3_path}")
                return False, {}
            elif error_code == '403':
                logger.error(f"Access denied to S3 path: {s3_path}")
                raise PermissionError(f"Access denied to S3 path: {s3_path}")
            else:
                logger.error(f"Error checking S3 file: {str(e)}")
                raise
                
    except Exception as e:
        logger.error(f"Unexpected error checking S3 file {s3_path}: {str(e)}")
        raise
```


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

- [[AWS S3 Wait for S3 File]]



-----------
##  Recommended Notes

