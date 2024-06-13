---
tags:
  - code
  - code_snippet
  - bash/awk
keywords: 
topics: 
language: bash
date of note: 2024-04-26
---

## Code Snippet Summary

>[!important]
>Count the number of unique values (i.e. **frequency count**) in a column in csv file


## Code

>[!example]
get the frequency count in column 2
> ```bash
> awk -F, '{print $2}' * | sort | uniq -c | sort -nr
> ```

- `awk -F, '{print $2}'` select the 2nd column in csv file
- send the output via pipe
- `sort` command sort the column; [reference](https://man7.org/linux/man-pages/man1/sort.1.html)
- `uniq` command *report or omit repeated lines*
	- **`-c`**: prefix lines by the number of occurrences
- `sort -nr` : [reference](https://man7.org/linux/man-pages/man1/sort.1.html)
	- **`-n`**: compare according to string numerical value
	- **`-r`**: reverse the result of comparisons


-----------
##  Recommended Notes

- Linux `sort` [reference](https://man7.org/linux/man-pages/man1/sort.1.html)
- Linux `uniq` [reference](https://man7.org/linux/man-pages/man1/uniq.1.html)
- GNU `awk` [User Guide](https://www.gnu.org/software/gawk/manual/gawk.html#General-Introduction)

- [[AWK command in Unix or Linux with examples]]
- [[Working with CSVs on the Command Line]]
- [[sed and awk pocket reference chapter 1]]
- [[sed and awk pocket reference chapter 2]]

- Stack Overflow:
	- [Getting the count of unique values in a column in bash](https://stackoverflow.com/questions/4921879/getting-the-count-of-unique-values-in-a-column-in-bash)