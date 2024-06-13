---
tags:
  - code
  - code_snippet
  - bash/awk
keywords: 
topics: 
language: bash
date of note: 2024-04-25
---

## Code Snippet Summary

>[!important]
>Extract a given column in a csv file

## Code

### Use `awk` command

- Extract the 2nd column in the csv file. 
- Change `$2` to be `$n` for n-th column
- The delimiter is defined using regular expression `\"*,\"*` 
	- this says: match `,` when word before it ends with `"` and words after it begins with `"`

```bash
awk -F "\"*,\"*" '{print $2}' textfile.csv
awk -F, '{print $2}' textfile.csv
```

- Another way is to use `FS`: 
	- `FS` **(Field Separator)** is the variable whose value is dafaulted to space. So `awk` by default splits at space for any line.
	- using `BEGIN` (**Execute before taking input**) we can set this field to anything we want...

```bash
awk 'BEGIN {FS = ","}; {print $2}' textfile.csv
```


### Use `cut` command

- Use `cat` to show entire file
- Use `cud -d ','` to chunk based on delimiter `','`
- `-f2` return 2nd chunk as the 2nd column

```bash
cat textfile.csv | cut -d ',' -f2
```

- It will fail if text in one column field contains `,` 





-----------
##  Recommended Notes

- GNU `awk` [User Guide](https://www.gnu.org/software/gawk/manual/gawk.html#General-Introduction)

- [[AWK command in Unix or Linux with examples]]
- [[sed and awk pocket reference chapter 1]]
- [[sed and awk pocket reference chapter 2]]
- [[Use awk to Parse CSV]]

- Blog: 
	- [Using AWK to Filter Rows](https://www.tim-dennis.com/data/tech/2016/08/09/using-awk-filter-rows.html)

- Stack Overflow:
	- [How to extract one column of a csv file](https://stackoverflow.com/questions/19602181/how-to-extract-one-column-of-a-csv-file)
	- [Print every nth column of a file](https://stackoverflow.com/questions/22354082/print-every-nth-column-of-a-file)
	- [Printing column separated by comma using Awk command line](https://stackoverflow.com/questions/26842504/printing-column-separated-by-comma-using-awk-command-line)