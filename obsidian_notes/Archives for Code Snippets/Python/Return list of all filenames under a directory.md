---
tags:
  - code
  - code_snippet
  - python/os
keywords: 
topics: 
language: python
date of note: 2024-04-02
---

## Code Snippet Summary

>[!important] 
>Given the folder, return a list of filenames under that folder.

## Code



```python
import os

def get_filenames(directory): 
	filenames = [] 
	for root, dirs, files in os.walk(directory): 
		for filename in files: 
			filenames.append(os.path.join(root, filename)) 
	return filenames
```

- `os.walk()`: Generate the file names in a directory tree by walking the tree either top-down or bottom-up. [reference](https://docs.python.org/3/library/os.html#os.walk)
	- For each directory in the tree rooted at directory _top_ (including _top_ itself), it yields a **3-tuple `(dirpath, dirnames, filenames)`**.
		- **`dirpath`** is a string, the *path* to the directory.
		- **`dirnames`** is a list of the names of the *subdirectories* in *dirpath* (including symlinks to directories, and excluding `'.'` and `'..'`). 
		- **`filenames`** is a list of the names of the non-directory files in *dirpath*.
	- Note that the names in the lists contain no path components. To get a full path (which begins with _top_) to a file or directory in _dirpath_, do `os.path.join(dirpath, name)`.
	- `topdown`: 
		- If optional argument _topdown_ is `True` or not specified, the triple for a directory is generated *before* the triples for any of its *subdirectories* (directories are generated **top-down**). 
		- If _topdown_ is `False`, the triple for a directory is generated *after* the triples for all of its subdirectories (directories are generated **bottom-up**).

>[!info] 
>If we just want to return the filenames under the `directory` root-level
> ```python
> import os
> 
> filenames = next(os.walk(mypath), (None, None, []))[2]  # [] if no file
> 
> # or
> 
> f = []
> for (dirpath, dirnames, filenames) in os.walk(mypath):
>     f.extend(filenames)
>     break
> ```


### implementation 2

```python
import os

onlyfiles = [f for f in os.listdir(mypath) if os.path.isfile(os.path.join(mypath, f))]
```

- `os.listdir(path)`:  Return a list containing the *names of the entries* in the directory given by _path_. [reference](https://docs.python.org/3/library/os.html#os.listdir)
	-  The list is in arbitrary order, and does not include the special entries `'.'` and `'..'` even if they are present in the directory.

- `os.path` module [reference](https://docs.python.org/3/library/os.path.html#module-os.path)
	- `os.path.exists(path)`: Return `True` if _path_ refers to an existing path or an open file descriptor. Returns `False` for broken symbolic links. [reference](https://docs.python.org/3/library/os.path.html#os.path.exists)
	- `os.path.isfile(path)`: Return `True` if _path_ is an [`existing`](https://docs.python.org/3/library/os.path.html#os.path.exists "os.path.exists") regular file. [reference](https://docs.python.org/3/library/os.path.html#os.path.isfile)
	- `os.path.join(path, ...)`: Join one or more path segments intelligently.  [reference](https://docs.python.org/3/library/os.path.html#os.path.join) 
		- The return value is the concatenation of _path_ and all members of *paths*, with *exactly one directory separator* following each non-empty part, *except the last*.
		- That is, the result will only end in a separator if the last part is either empty or ends in a separator. 
		- If a segment is an absolute path (which on Windows requires both a drive and a root), then all previous segments are ignored and joining continues from the absolute path segment.

### implementation  3

```python
import os

search_dir = "/mydir/"
os.chdir(search_dir)
files = filter(os.path.isfile, os.listdir(search_dir))
files = [os.path.join(search_dir, f) for f in files] # add path to each file
files.sort(key=lambda x: os.path.getmtime(x))
```

- use `filter()` to filter non-files (via `os.path.isfile()` function) in the returns of `os.listdir(my_dir)`
- add the folder path to the filename to form the full path
- sort by creation time
### Using `glob`

```python
import glob
import os

search_dir = "/mydir/"
# remove anything from the list that is not a file (directories, symlinks)
# thanks to J.F. Sebastion for pointing out that the requirement was a list 
# of files (presumably not including directories)  
files = list(filter(os.path.isfile, glob.glob(search_dir + "*")))
files.sort(key=lambda x: os.path.getmtime(x))
```

- use `filter()` to filter non-files (via `os.path.isfile()` function) in the returns of `glob.glob(search_dir + "*")`


-----------
##  Recommended Notes

- `os` package: miscellaneous operating system interfaces [reference](https://docs.python.org/3/library/os.html)
	- `os.walk()`: [reference](https://docs.python.org/3/library/os.html#os.walk)
	- `os.listdir()`:  [reference](https://docs.python.org/3/library/os.html#os.listdir)
- `os.path` module [reference](https://docs.python.org/3/library/os.path.html#module-os.path)
	- `os.path.exists(path)` [reference](https://docs.python.org/3/library/os.path.html#os.path.exists)
	- `os.path.isfile(path)` [reference](https://docs.python.org/3/library/os.path.html#os.path.isfile)
	- `os.path.join(path, ...)` [reference](https://docs.python.org/3/library/os.path.html#os.path.join)
- Stack Overflow:
	- [How do I list all files of a directory?](https://stackoverflow.com/questions/3207219/how-do-i-list-all-files-of-a-directory)
	- [How do you get a directory listing sorted by creation date in python?](https://stackoverflow.com/questions/168409/how-do-you-get-a-directory-listing-sorted-by-creation-date-in-python)