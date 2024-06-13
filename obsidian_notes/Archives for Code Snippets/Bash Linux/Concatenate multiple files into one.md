---
tags:
  - code
  - code_snippet
  - linux/cat
keywords: 
topics: 
language: linux
date of note: 2024-04-26
---

## Code Snippet Summary

>[!important]
>Assume a set of files in one directory, **concatenate all of these** files into one

## Code

- Assume the name following a same format `prefix_xx`
- file has the same suffix `.csv`

```bash
cat prefix_*.csv > new_file.csv
```

### Remove Header first and then Concatenate

- Use `sed` command, `"1 d"` means *to delete the first row*
- `>>` append the data into the end of file

```bash
cat input1.csv > combined.csv
cat input2.csv | sed "1 d" >> combined.csv
cat input3.csv | sed "1 d" >> combined.csv
```


-----------
##  Recommended Notes

- [[Linux] How to combine different csv files using command prompt in Linux operating system](https://www.zyxware.com/articles/4116/linux-how-to-combine-different-csv-files-using-command-prompt-in-linux-operating)
- [[Working with CSVs on the Command Line]]