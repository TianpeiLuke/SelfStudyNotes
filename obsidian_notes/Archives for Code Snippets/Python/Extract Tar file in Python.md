---
tags:
  - code
  - code_snippet
  - python/tarfile
keywords: 
topics: 
language: python
date of note: 2025-05-12
---

## Code Snippet Summary

>[!important]
>Extract Tarfile in Python


## Code

```python
import tarfile
import os
```

```python
# Decompress the tar.gz file
print(f"Decompressing {local_file_path}")
with tarfile.open(local_file_path, "r:gz") as tar:
    tar.extractall(path=local_folder)
print(f"Successfully decompressed {folder}/output.tar.gz")
        
# Optional: Remove the compressed file after extraction
os.remove(local_file_path)
print(f"Removed compressed file {local_file_path}")
```

- `tarfile`
	- [reference](https://docs.python.org/3/library/tarfile.html)
- `tarfile.open(_name=None_, _mode='r'_, _fileobj=None_, _bufsize=10240_, _**kwargs_)`
	- Return a [`TarFile`](https://docs.python.org/3/library/tarfile.html#tarfile.TarFile "tarfile.TarFile") object for the pathname _name_.


| mode            | action                                                                                                                                                                                             |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `'r' or 'r:*'`  | Open for reading with transparent compression (recommended).                                                                                                                                       |
| `'r:'`          | Open for reading exclusively without compression.                                                                                                                                                  |
| `'r:gz'`        | Open for reading with **gzip** *compression*.                                                                                                                                                      |
| `'r:bz2'`       | Open for reading with bzip2 compression.                                                                                                                                                           |
| `'r:xz'`        | Open for reading with lzma compression.                                                                                                                                                            |
| `'x'` or `'x:'` | Create a tarfile exclusively without compression. Raise a [`FileExistsError`](https://docs.python.org/3/library/exceptions.html#FileExistsError "FileExistsError") exception if it already exists. |
| `'x:gz'`        | Create a tarfile with gzip compression. Raise a [`FileExistsError`](https://docs.python.org/3/library/exceptions.html#FileExistsError "FileExistsError") exception if it already exists.           |
| `'x:bz2'`       | Create a tarfile with bzip2 compression. Raise a [`FileExistsError`](https://docs.python.org/3/library/exceptions.html#FileExistsError "FileExistsError") exception if it already exists.          |
| `'x:xz'`        | Create a tarfile with lzma compression. Raise a [`FileExistsError`](https://docs.python.org/3/library/exceptions.html#FileExistsError "FileExistsError") exception if it already exists.           |
| `'a' or 'a:'`   | Open for appending with no compression. The file is created if it does not exist.                                                                                                                  |
| `'w' or 'w:'`   | Open for uncompressed writing.                                                                                                                                                                     |
| `'w:gz'`        | Open for **gzip** compressed *writing*.                                                                                                                                                            |
| `'w:bz2'`       | Open for bzip2 compressed writing.                                                                                                                                                                 |
| `'w:xz'`        | Open for lzma compressed writing.                                                                                                                                                                  |





-----------
##  Recommended Notes


- [[Compress folder into tar gz file and uncompress]]