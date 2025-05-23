---
tags:
  - code
  - code_snippet
  - aws/lambda
  - aws/s3
keywords: 
topics: 
language: python
date of note: 2024-04-02
---

## Code Snippet Summary

>[!important]
>Given S3 URL (e.g.  *"s3://my-bucket/prefix/filename.csv"*), return both *bucket name* as well as *prefix* (subdirectory and filename)
>
>In the code below, we complete following steps
>- **Parse URL** using `urllib.parse.urlparse` method
>- *Call S3 service client* using AWS SDK `boto3`
>- Return result of **`list_objects_v2`** operation with *successive service calls*. Using `get_paginator` to obtain `Paginator` to achieve successive call. 
>- **Iterate** over all returned results via `PageIterator` returned by calling **`paginate()` method**
>- For each response dictionary, 
>	- check the `'Contents'` field to obtain a  list of *folder/filenames* (`Key`)
>	- collect filename if *all* filenames under `key` ends with `'.csv'` 

- [[AWS S3 Parse Path]]

## Code

```python
import os
import boto3
from urllib.parse import urlparse


def get_filepath_from_s3(s3uri):
    parsed_url = urlparse(s3uri)
    bucket = parsed_url.netloc
    prefix = parsed_url.path[1:]
    
    s3 = boto3.client('s3')
    
    files_list = []
    for p in s3.get_paginator("list_objects_v2").paginate(Bucket=bucket, Prefix=prefix):
        for e in p['Contents']:
            if all(x in e['Key'] for x in ['.csv']):
                print("e: ",e['Key'])
                files_list.append(e['Key'])
    return bucket, files_list
```

- `urllib.parse.urlparse`: Parse a URL into six components, returning a 6-item [named tuple](https://docs.python.org/3/glossary.html#term-named-tuple). [reference](https://docs.python.org/3/library/urllib.parse.html#urllib.parse.urlparse)
	- This corresponds to the **general structure of a URL**: **`scheme://netloc/path;parameters?query#fragment`**.
	- `urlparse("scheme://netloc/path;parameters?query#fragment")` will return `ParseResult(scheme='scheme', netloc='netloc', path='/path;parameters', params='', query='query', fragment='fragment')`
	- Each tuple item is a string, possibly empty.
	- For S3 URL `"S3://bucket-name/folder/filename"`, `scheme="S3"`, `netloc="bucket-name"`, `path="/folder/filename"` thus `prefix = path[1:] = "folder/filename"`

- `boto3.client()`: return client service instance [reference](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/core/boto3.html#boto3.client)
	- `boto3.client('s3')`: return S3 client service [reference](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/s3.html)
		- **`s3.get_paginator()`**: [guide](https://boto3.amazonaws.com/v1/documentation/api/latest/guide/paginators.html)
			- Some AWS operations return results that are *incomplete* and *require subsequent requests* in order to *attain* the entire result set. The process of *sending subsequent requests* to *continue* where a previous request left off is called **pagination**.
			- For example, the `list_objects` operation of Amazon S3 returns up to **1000 objects** at a time, and you must send subsequent requests with the appropriate `Marker` in order to retrieve the next _page_ of results.
			- *Paginators* are created via the `get_paginator()` method of a boto3 client.
			- The `get_paginator()` method accepts an *operation name* and returns a reusable `Paginator` object.
			- `paginate()` method: You must call the `paginate` method of a *Paginator* in order to **iterate over the pages of API operation results**.
				- This method returns an **iterable `PageIterator`.**
				- This method accepts a `Prefix` parameter used to filter the paginated results by *prefix* server-side before sending them to the client.
				- The return value is a **dictionary**. Check [ListUsers](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/iam/paginator/ListUsers.html#) for the returned dictionary value. 
				  
		- `s3.client.list_objects_v2` Returns some or all (**up to 1,000**) of the objects in a bucket with each request. You can use the request parameters as selection criteria to return a subset of the objects in a bucket. [reference](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/s3/client/list_objects_v2.html)
			- The following operations are related to `ListObjectsV2`:
				- [GetObject](https://docs.aws.amazon.com/AmazonS3/latest/API/API_GetObject.html)
				- [PutObject](https://docs.aws.amazon.com/AmazonS3/latest/API/API_PutObject.html)
				- [CreateBucket](https://docs.aws.amazon.com/AmazonS3/latest/API/API_CreateBucket.html)
			- The **response** syntax  
>[!info]
>The **Response Syntax** as the return of `list_objects_v2` operations
> ```python
> {
>     'IsTruncated': True|False,
>     'Contents': [
>         {
>             'Key': 'string',
>             'LastModified': datetime(2015, 1, 1),
>             'ETag': 'string',
>             'ChecksumAlgorithm': [
>                 'CRC32'|'CRC32C'|'SHA1'|'SHA256',
>             ],
>             'Size': 123,
>             'StorageClass': 'STANDARD'|'REDUCED_REDUNDANCY'|'GLACIER'|'STANDARD_IA'|'ONEZONE_IA'|'INTELLIGENT_TIERING'|'DEEP_ARCHIVE'|'OUTPOSTS'|'GLACIER_IR'|'SNOW'|'EXPRESS_ONEZONE',
>             'Owner': {
>                 'DisplayName': 'string',
>                 'ID': 'string'
>             },
>             'RestoreStatus': {
>                 'IsRestoreInProgress': True|False,
>                 'RestoreExpiryDate': datetime(2015, 1, 1)
>             }
>         },
>     ],
>     'Name': 'string',
>     'Prefix': 'string',
>     'Delimiter': 'string',
>     'MaxKeys': 123,
>     'CommonPrefixes': [
>         {
>             'Prefix': 'string'
>         },
>     ],
>     'EncodingType': 'url',
>     'KeyCount': 123,
>     'ContinuationToken': 'string',
>     'NextContinuationToken': 'string',
>     'StartAfter': 'string',
>     'RequestCharged': 'requester'
> }
> ```
> 


>[!example]
>Use `paginator.parginate()` to iterate over all objects
> ```python
> import boto3
> 
> # Create a client
> client = boto3.client('s3', region_name='us-west-2')
> 
> # Create a reusable Paginator
> paginator = client.get_paginator('list_objects_v2')
> 
> # Create a PageIterator from the Paginator
> page_iterator = paginator.paginate(Bucket='my-bucket', Prefix='foo/baz')
> 
> for page in page_iterator:
>     print(page['Contents'])
> ```

>[!example]
>List all parquet files under a given bucket and prefix
>
> ```python
> s3_client = boto3.client('s3') 
> 
> # List all objects with the given prefix
> def list_s3_files(bucket, prefix):
>     paginator = s3.get_paginator('list_objects_v2')
>     pages = paginator.paginate(Bucket=bucket, Prefix=prefix)
>     
>     files = []
>     for page in pages:
>         if 'Contents' in page:
>             for obj in page['Contents']:
>                 if obj['Key'].endswith('.parquet'):
>                     files.append(obj['Key'])
>     return files
> ```
> 




-----------
##  Recommended Notes

- `urllib` package [reference](https://docs.python.org/3/library/urllib.parse.html)
	- `urllib.parse.urlparse`:  [reference](https://docs.python.org/3/library/urllib.parse.html#urllib.parse.urlparse)
- **AWS SDK `boto3`** package [guide](https://boto3.amazonaws.com/v1/documentation/api/latest/guide/quickstart.html)
	- Core reference [link](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/core/index.html)
	- S3 client service [reference](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/s3.html)
	- Paginators [guide](https://boto3.amazonaws.com/v1/documentation/api/latest/guide/paginators.html)
	- `s3.client.list_objects_v2` [reference](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/s3/client/list_objects_v2.html)
- [AWS Command Line Interface (CLI)](https://aws.amazon.com/cli/)
- [AWS CLI Command Reference](https://docs.aws.amazon.com/cli/latest/)
	- S3 service [reference](https://docs.aws.amazon.com/cli/latest/reference/s3/)
		- [available command](https://docs.aws.amazon.com/cli/latest/reference/s3/#available-commands)
