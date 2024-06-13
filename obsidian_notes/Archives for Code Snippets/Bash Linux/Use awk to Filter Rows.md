---
tags:
  - code
  - code_snippet
  - bash/awk
keywords: 
topics: 
language: bash
date of note: 2024-04-24
---

## Code Snippet Summary

>[!important]
>Use `awk` to filter rows in csv file

## Code



### Printing Fields

```bash
awk '{print $1 $2}' pos_cut.txt
```

- Notice that there’s no formatting of the output. There are many ways to *format and structure* the output in **AWK**. Checkout the [printing](https://www.gnu.org/software/gawk/manual/gawk.html#Printing) section on the AWK user guide for more information on this.

### Searching

- **AWK** to **search** for a specific thing – a number we know exists in the dataset. Note that if you specify what fields to print out, 
- AWK will *print the whole line* that **matches the search** by default.

```bash
awk '/2410626/' pos_cut.txt
```

- Search Syntax is close to VIM [[Search all occurrences of a keyword]]
- Instead of matching a unique number, we could have matched on a **string pattern** or **regular expression**. In that case, AWK would return *every line that matches the pattern*. 
- In our case above, that number occurs once in the data file, but we could have used a *regular expression* or a *range pattern* instead. 
- For more on finding patterns in AWK, check out the [Patterns, Actions and Variables](https://www.gnu.org/software/gawk/manual/gawk.html#Patterns-and-Actions) section of the AWK guide.

### Filtering Rows Based on Field Values

```bash
awk '{ if ($7 == 6) { print } }' pos_cut1-5.txt | head
```

- we use the keyword `if` and then a **conditional expression**, `($7 == 6)`, based on the *column variable*, `$7` we want to test on. 
	- **The dollar sign** here denotes we are working with **a variable** and in this case, AWK knows that `$7` means the *7th field* in our dataset. 
	- Likewise, `$6` would mean the 6th field and so on. 
	- `\=\=` is often used in programming languages to test for equality because a single `\=` is often used for object assignment.
- As we go **line-by-line** in this file, *if* the value in column 7 is equal to 6 then *the match is true* and the line is included in the output. 
- then we use **piping**, using the `|` operator, the results to `head` to keep the output concise for this blog.
- Check out the documentation on using [control statements](https://www.gnu.org/software/gawk/manual/gawk.html#Statements) in AWK for more ways you can use conditionals to make decisions.

>[!example]
>Only print rows when the *8-th column* value is greater than or equal to 11000000
> ```bash
> awk '{ if($8 >= 11000000) { print }}' pos_cut.txt | head
> ```


```bash
awk -F "\t" '{ if(($7 == 6) && ($8 >= 11000000)) { print } }' pos_cut.txt | tail
```

- We are using the boolean **and** `&&` here (other operators are `||` for **or** and `!` for **not**) to combine our two conditional statements. 
- Now let’s add our second column `$8` condition (<=25000000) to our if statement.

```bash
awk -F "\t" '{ if(($7 == 6) && ($8 >= 11000000 && $8 <= 25000000)) { print } }' pos_cut.txt
```

- You can also put an AWK program in it’s **own file** and run with `awk -f source-file`. 
- There are many more features in the [AWK language](https://www.gnu.org/software/gawk/manual/gawk.html) I didn’t discuss in this blog.




-----------
##  Recommended Notes

- GNU `awk` [User Guide](https://www.gnu.org/software/gawk/manual/gawk.html#General-Introduction)
	- [Field-Splitting Summary](https://www.gnu.org/software/gawk/manual/gawk.html#Field_002dSplitting-Summary)

- [[AWK command in Unix or Linux with examples]]
- [[sed and awk pocket reference chapter 1]]
- [[sed and awk pocket reference chapter 2]]


- Blog: 
	- [Using AWK to Filter Rows](https://www.tim-dennis.com/data/tech/2016/08/09/using-awk-filter-rows.html)