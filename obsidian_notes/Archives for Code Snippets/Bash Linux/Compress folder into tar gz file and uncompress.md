---
tags:
  - code
  - code_snippet
  - linux/tar
  - bash/tar
keywords: 
topics: 
language: bash
date of note: 2024-04-04
---

## Code Snippet Summary

>[!important]
> Task: 
>- **compress** a folder into `tar.gz` via `tar` and `gzip` 
>- **uncompress** a `tar.gz` back into folder

## Code

```bash
tar -czf name_of_archive_file.tar.gz name_of_directory_to_tar
```

- **`tar`**: 
	- Adding `-` before the options (**`czf`**) is optional with `tar`. The effect of `czf` is as follows:
		- **`c`** — **create an archive file** (as opposed to **extract**, which is `x`)
		- **`f`** — **filename** of the archive file
		- **`z`** — **filter** archive through **`gzip`** (remove this option to create a `.tar` file)

- If you want to `tar` the current directory, use `.` to designate that.

- to uncompress 
```bash
tar -xvzf community_images.tar.gz
```

- `tar` collected all the files into one package, `community_images.tar`. The gzip program applied compression, hence the `gz` extension. So the command does a couple things:
	- `f`: this must be the last flag of the command, and the tar **f**ile must be immediately after. It tells tar the name and path of the compressed file.
	- `z`: tells tar to decompress the archive using g**z**ip
	- `x`: tar can collect files or **extract** them. `x` does the latter.
	- `v`: makes tar talk a lot. **V**erbose output shows you all the files being extracted.

- To extract into a **c**ustom folder, add the `-C` option with a folder name of your choice:

```bash
tar -xvzf community_images.tar.gz -C some_custom_folder_name
```

### Exclude Certain Files

```bash
tar --exclude='*.pyc' --exclude='*.pyo' --exclude='__pycache__' --exclude='*~' --exclude='.*' -czf name_of_archive_file.tar.gz name_of_directory_to_tar
```

```bash
tar --exclude="*__pycache__*" --exclude="*.pyc" --exclude="*/.pytest_cache/*" --exclude="*.temp" --exclude="*temp*" --exclude="*.tmp" --exclude="*.DS_Store" --exclude="*.coverage" --exclude="*.hypothesis" --exclude="*/.eggs/*" --exclude="*.egg-info" --exclude="*/__pycache__" --exclude="*/.pytest_cache" -czvf ../cursus.tar.gz ./src ./test ./slipbox
```


```bash
tar -czf ../cursus.tar.gz --exclude="*/__pycache__" --exclude="*.pyc" --exclude="*/.pytest_cache" --exclude="*/__pytest__" --exclude="*/.coverage" --exclude="*/dist" --exclude="*/build" --exclude="*.egg-info" --exclude="*/.eggs" --exclude=".tox" --exclude="*/.hypothesis" --exclude="*/.cache" --exclude="*/.mypy_cache" --exclude="*/htmlcov" --exclude=".venv" --exclude=".git" .
```


### Check Content

- [[Check the Compressed File content]]


-----------
##  Recommended Notes

- Stack Exchange [Compress a folder with tar?](https://unix.stackexchange.com/questions/46969/compress-a-folder-with-tar)
- Stack Exchange [What command do I need to unzip/extract a .tar.gz file?](https://askubuntu.com/questions/25347/what-command-do-i-need-to-unzip-extract-a-tar-gz-file)
