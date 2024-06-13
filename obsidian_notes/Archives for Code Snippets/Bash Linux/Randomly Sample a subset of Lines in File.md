---
tags:
  - code
  - code_snippet
  - linux/shuf
keywords: 
topics: 
language: bash
date of note: 2024-04-26
---

## Code Snippet Summary

>[!important]
>*Randomly select* a subset of lines in a very large files


## Code

### Use `shuf`

```bash
shuf -n 1000 file
```

- It will use **reservoir sampling** when appropriate, meaning it shouldn't run out of memory and is using a fast algorithm

### Use `awk`

- **If you don't need "exactly" n sampled lines** you can **sample a ratio** like this:
- The following code show _approximately_ 1% of the non-blank lines,

```bash
cat input.txt | awk 'BEGIN {srand()} !/^$/ { if (rand() <= .01) print $0}' > sample.txt
```


-----------
##  Recommended Notes

- [GNU Coreutils](https://www.gnu.org/software/coreutils/manual/coreutils.html#toc_Operating-on-sorted-files)


- UNIX Stack Exchange
	- [How to randomly sample a subset of a file](https://unix.stackexchange.com/questions/108581/how-to-randomly-sample-a-subset-of-a-file)