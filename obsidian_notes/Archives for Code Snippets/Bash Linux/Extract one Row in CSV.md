---
tags:
  - code
  - code_snippet
  - bash/sed
  - bash/awk
keywords: 
topics: 
language: bash
date of note: 2024-04-26
---

## Code Snippet Summary

>[!important]
>Extract a row in a file given the row number


## Code

### Use `sed`

```bash
sed 'NUMq;d' file
```

- `sed` = Stream EDitor
- `NUM` is the number of the line you want to print;
- The command string:
    - `NUMq` = will *quit immediately* when the line number is `NUM` ; this is to prevent reading an entire large file
    - `d` will *delete the line* instead of printing it; this is inhibited on the last line because the `q` causes the rest of the script to be skipped when quitting.
- `file` = the file name

>[!example]
If you have `NUM` in a variable, you will want to use double quotes instead of single:
> ```bash
> sed "${NUM}q;d" file
> ```

- another way is to use `-n`

>[!example]
>- Print the 2nd line
> ```bash
> sed -n '2p' < file.txt
> ```
>- Print 10th to 33rd line 
> ```bash
> sed -n '10,33p' < file.txt
> ```
>- Print 1st and 3rd line
> ```bash
> sed -n '1p;3p' < file.txt
> ```


- Similar to VIM command in [[VIM Cheat Sheet#2. Vim commands for movement]]

### Use `awk`

```bash
 awk 'NR == 2 {print; exit}' file.txt
```

- `NR` is the current row number count
- in this command, when row number is `2`, the command print the line and quit
- `{print; exit}` is necessary if the total number of lines is large. So we do not want to keep reading when hitting the line number.

### Use `head` and `tail`

```bash
head -50000000 myfile.ascii | tail -1
```

- `head -n` choose the top `n` lines
- `tail -1` choose the bottom `1` line
- combine together, it first return all `50000000` lines and then choose the last line, which is the 50000000th line.



-----------
##  Recommended Notes

- GNU `awk` [User Guide](https://www.gnu.org/software/gawk/manual/gawk.html#General-Introduction)

- [[AWK command in Unix or Linux with examples]]
- [[Working with CSVs on the Command Line]]
- [[sed and awk pocket reference chapter 1]]
- [[sed and awk pocket reference chapter 2]]

- Ask Ubuntu:
	- [Bash tool to get nth line from a file](https://stackoverflow.com/questions/6022384/bash-tool-to-get-nth-line-from-a-file)

- Stack Overflow
	- [cut or awk command to print first field of first row](https://stackoverflow.com/questions/22190902/cut-or-awk-command-to-print-first-field-of-first-row)