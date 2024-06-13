---
tags:
  - code
  - code_snippet
  - bash
keywords: 
topics: 
language: bash
date of note: 2024-04-24
---

## Code Snippet Summary

>[!important]
>Check if a File is Empty


## Code

### Using the `` `test` `` command or `` `[` ``

>[!example]
> To check if a file is empty using **`[`**, you can use the **`-s`** option, which **checks the size** of the file:
> ```bash
> #!/usr/bin/env bash
> 
> FILENAME=myfile.txt
> 
> # Check if the file is empty
> if [ ! -s "${FILENAME}" ]; then
>     echo "File is empty"
> else
>     echo "File is not empty"
> fi
> ```

- The `` `test` `` command (which is an **alias** for the **`[` command**) is a simple and widely-available utility for performing various **tests on files** and other objects in Bash.

### Using the `wc` command

>[!example]
>- The **`wc`** (**word count**) command is another utility that can be used to check if *a file is empty* in Bash. 
>- To **check the number of lines** in a file, you can use the **`-l`** option:
> ```bash
> #!/usr/bin/env bash
> 
> FILENAME=myfile.txt
> 
> # Check if file has any lines
> if [ $(wc -l < "${FILENAME}") -eq 0 ]; then
>     echo "File $FILENAME is empty"
> else
>     echo "File $FILENAME is not empty"
> fi
> ```

- This will pass the contents of the file to the **`wc`** command as standard input, and the **`-l`** option will count the number of lines. 
- If the number of lines is zero, the file is considered empty.

### Using the `grep` command

>[!example]
>- The **`grep`** command is a powerful tool for **searching and processing** *text files*. 
>- To check if a file is empty using `grep`, you can use the **`-q`** option, which causes grep to *run quietly* and return *an exit code*:
> ```bash
> #!/usr/bin/env bash
> 
> FILENAME=myfile.txt
> 
> if grep -q . "${FILENAME}"; then
>     echo "File is not empty"
> else
>     echo "File is empty"
> fi
> ```

- This will search the file for *any character* (**.** is a regular expression that matches any character) and return a *zero exit code* if a match is *found*, or a *non-zero exit code* if the file is *empty*.

### Using the `find` command

>[!example]
>- The **`find`** command is a utility for **searching and processing** *files and directories*. 
>- To check if a file is empty using `find`, you can use the `-empty` option, which *matches files that are empty*:
> ```bash
> #!/usr/bin/env bash
> 
> FILENAME=myfile.txt
> if find . -type f -empty -name "${FILENAME}"; then
>     echo "File is empty"
> else
>     echo "File is not empty"
> fi
> ```

- This will search the current directory **(.)** for *files* **`-type f`** that are empty **`-empty`** and have the name **“myfile.txt”** (`-name “myfile.txt”`). 
- If a **match is found**, the find command will return a **zero exit code**, indicating that the *file is empty*. 
- If **no match is found**, the find command will return a **non-zero exit code**, indicating that the file is **not empty**.

### Using the `stat` command

>[!example]
> - The **`stat`** command is a utility for **displaying information** about *files and filesystems*. 
> - To check if a file is empty using `stat`, you can use the **`-c` option** to **display the size** of the file in *bytes:*
> ```bash
> #!/usr/bin/env bash
> 
> FILENAME=myfile.txt
> if [ $(stat -c %s "${FILENAME}") -eq 0 ]; then
>     echo "File is empty"
> else
>     echo "File is not empty"
> fi
> ```

- This will *pass the size of the file* to the **`[`** command, which will **compare it to zero**. 
- If the *size is zero*, the file is considered *empty*. 
- If the *size is non-zero*, the file is considered *not empty*.


-----------
##  Recommended Notes

- [5 Ways to check if a file is empty in Bash](https://tecadmin.net/bash-script-check-if-file-is-empty-or-not/)
- [Bash: Test If File Exists](https://www.shellhacks.com/bash-test-if-file-exists/)

- [[Use grep to show matched lines with keyword]]