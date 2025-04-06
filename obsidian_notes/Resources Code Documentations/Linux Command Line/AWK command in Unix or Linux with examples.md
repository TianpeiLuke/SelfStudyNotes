---
tags:
  - blog_post
  - excerpt
  - code_package
  - bash/awk
aliases: 
keywords:
  - csv
  - linux
topics:
  - command_line_script
language: bash
date of note: 2024-04-26
name: AWK command in Unix/Linux with examples
version: 
year: 2019
---

>[!quote]
> **Awk** is a **scripting language** used for **manipulating data and generating reports**.The awk command programming language requires no compiling, and allows the user to use variables, numeric functions, string functions, and logical operators.
> 
> Awk is a utility that enables a programmer to **write tiny but effective programs** in the form of statements that *define text patterns* that are to be *searched* for *in each line of a document* and the *action* that is to be taken when *a match* is found within a line. Awk is mostly used for **pattern scanning** and **processing**. It searches one or more files to see if they contain lines that matches with the specified patterns and then performs the associated actions.
> 
> Awk is abbreviated from the names of the developers – Aho, Weinberger, and Kernighan.

>[!important]
> **WHAT CAN WE DO WITH AWK ?**
> 
> **1. AWK Operations:**  
> (a) Scans a file line by line  
> (b) Splits each input line into fields  
> (c) Compares input line/fields to pattern  
> (d) Performs action(s) on matched lines
> 
> **2. Useful For:**  
> (a) Transform data files  
> (b) Produce formatted reports
> 
> **3. Programming Constructs:**  
> (a) Format output lines  
> (b) Arithmetic and string operations  
> (c) Conditionals and loops
> 
  
  
## Syntax 

```bash
awk options 'selection _criteria {action }' input-file > output-file
```

**Options:**

- `-f` program-file : Reads the AWK program source from the file 
                  program-file, instead of from the 
                  first command line argument.
- `-F fs`            : Use fs for the input field separator


**Sample Commands**

>[!example]
Consider the following text file as the input file for all cases below.
> ```bash
> cat > employee.txt 
> ```

```plain
ajay manager account 45000
sunil clerk account 25000
varun manager sales 50000
amit manager account 47000
tarun peon sales 15000
deepak clerk sales 23000
sunil peon sales 13000
satvik director purchase 80000 
```

### Default behavior of Awk 

By default Awk prints every line of data from the specified file.

```bash
awk '{print}' employee.txt
```

**Output:**

```plain
ajay manager account 45000
sunil clerk account 25000
varun manager sales 50000
amit manager account 47000
tarun peon sales 15000
deepak clerk sales 23000
sunil peon sales 13000
satvik director purchase 80000 
```

In the above example, no pattern is given. So the actions are applicable to all the lines. Action print without any argument prints the whole line by default, so it prints all the lines of the file without failure.

### Print the lines which matches with the given pattern.

```bash
awk '/manager/ {print}' employee.txt 
```

**Output:**

```plain
ajay manager account 45000
varun manager sales 50000
amit manager account 47000 
```

In the above example, the awk command prints all the line which matches with the ‘manager’.

### Spliting a Line Into Fields

>[!quote]
>For each record i.e line, the `awk` command splits the record *delimited* by **whitespace** character *by default* and stores it in the **`$n` variables**. If the line has 4 words, it will be stored in $1, $2, $3 and $4 respectively. Also, **`$0` represents the whole line**.

```bash
awk '{print $1,$4}' employee.txt 
```

**Output:**

```plain
ajay 45000
sunil 25000
varun 50000
amit 47000
tarun 15000
deepak 23000
sunil 13000
satvik 80000
```

In the above example, `$1` and `$4` represents Name and Salary fields respectively.

## Built In Variables In Awk

>[!info]
>Awk’s **built-in variables** include the field variables—`$1`, `$2`, `$3`, and so on (`$0` is the entire line) — that break a line of text into individual words or pieces called fields.
> 
> - **`NR`:** NR command keeps a **current count** of **the number of input records**. Remember that records are usually **lines**. Awk command performs *the pattern/action statements* **once** for *each record* in a file.
> 
> - **`NF`:** NF command keeps a **count of the number of fields** *within the current input record*.
> 
> - **`FS`:** FS command contains **the field separator character** which is used to divide fields on the input line. *The default is “white space”*, meaning space and tab characters. FS can be reassigned to another character (typically in **BEGIN**) to change the field separator.
> 
> - **`RS`:** RS command stores the current **record separator character**. Since, by default, an input line is the input record, *the default record separator* character is **a newline**.
> 
> - **`OFS`:** OFS command stores **the output field separator**, which separates the fields when Awk *prints* them. *The default is a blank space*. Whenever print has several parameters *separated with commas*, it will *print the value of OFS in between* each parameter.
> 
> - **`ORS`:** ORS command stores **the output record separator**, which separates *the output lines* when Awk *prints* them. *The default is a newline character*. print automatically outputs the contents of ORS *at the end* of whatever it is given to print.

**Examples:**

>[!example]
>Use of NR built-in variables (**Display Line Number**)
> ```bash
> awk '{print NR,$0}' employee.txt 
> ```

**Output:**

```plain
1 ajay manager account 45000
2 sunil clerk account 25000
3 varun manager sales 50000
4 amit manager account 47000
5 tarun peon sales 15000
6 deepak clerk sales 23000
7 sunil peon sales 13000
8 satvik director purchase 80000 
```

In the above example, the `awk` command with `NR` prints all the lines along with *the line number*.



>[!example]
>Use of NF built-in variables (**Display Last Field**)
> ```bash
> awk '{print $1,$NF}' employee.txt 
> ```

**Output:**

```plain
ajay 45000
sunil 25000
varun 50000
amit 47000
tarun 15000
deepak 23000
sunil 13000
satvik 80000 
```

In the above example `$1` represents Name and `$NF` represents Salary. We can get the Salary using `$NF` , where `$NF` represents last field.



>[!example]
>Another use of NR built-in variables (**Display Line From 3 to 6**)
> ```bash
> awk 'NR==3, NR==6 {print NR,$0}' employee.txt 
> ```

**Output:**

```plain
3 varun manager sales 50000
4 amit manager account 47000
5 tarun peon sales 15000
6 deepak clerk sales 23000 
```



## More Examples

**For the given text file:**

```bash
cat > geeksforgeeks.txt
```

```plain
A    B    C
Tarun    A12    1
Man    B6    2
Praveen    M42    3
```



>[!example]
> Print the first item along with the *row number(NR)* separated with ” – “ from each line 
> ```bash
> awk '{print NR "- " $1 }' geeksforgeeks.txt
> ```

```plain
1 - Tarun
2 – Manav    
3 - Praveen
```



>[!example]
>To return the second row/item
> ```bash
> awk '{print $2}' geeksforgeeks.txt
> ```

```plain
A12
B6
M42
```



>[!example]
>To print any *non empty line* if present
> ```bash
> awk 'NF > 0' geeksforgeeks.txt
> ```

```plain
0
```



>[!example]
>To find **the length of the longest line** present in the file:
> ```bash
> awk '{ if (length($0) > max) max = length($0) } END { print max }' geeksforgeeks.txt
> ```

```
13
```



>[!example]
>To **count the lines** in a file:
> ```bash
> awk 'END { print NR }' geeksforgeeks.txt
> ```

```plain
3
```



> [!example]
> Printing lines with *more than 10 characters*:
> ```bash
> awk 'length($0) > 10' geeksforgeeks.txt
> ```

```plain
Tarun    A12    1
Praveen    M42    3
```



>[!example]
To find/check for *any string* in *any column*:
> ```bash
> awk '{ if($3 == "B6") print $0;}' geeksforgeeks.txt
> ```



>[!example]
To print the **squares of first numbers from 1 to n** say 6:
> ```bash
> awk 'BEGIN { for(i=1;i<=6;i++) print "square of", i, "is",i*i; }'
> ```

```
square of 1 is 1
square of 2 is 4
square of 3 is 9
square of 4 is 16
square of 5 is 25
square of 6 is 36
```


>[!quote]
> This article is contributed by **Anshika Goyal** and **Praveen Negi**. If you like GeeksforGeeks and would like to contribute, you can also write an article using [contribute.geeksforgeeks.org](http://www.contribute.geeksforgeeks.org/) or mail your article to contribute@geeksforgeeks.org. See your article appearing on the GeeksforGeeks main page and help other Geeks.
> 
> Please write comments if you find anything incorrect, or you want to share more information about the topic discussed above.



-----------
##  Recommended Notes

- [8 Powerful Awk Built-in Variables – FS, OFS, RS, ORS, NR, NF, FILENAME, FNR](https://www.thegeekstuff.com/2010/01/8-powerful-awk-built-in-variables-fs-ofs-rs-ors-nr-nf-filename-fnr/)
- [awk - 10 examples to insert / remove / update fields of a CSV file](https://www.theunixschool.com/2012/11/awk-examples-insert-remove-update-fields.html)


----------
##  Citations

- Geeksforgeeks:
	- [AWK command in Unix/Linux with examples]([https://www.geeksforgeeks.org/awk-command-unixlinux-examples/](https://www.geeksforgeeks.org/awk-command-unixlinux-examples/))


- *code source*:
- *code package link*




