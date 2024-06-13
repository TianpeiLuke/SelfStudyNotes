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
>Extract given columns in csv file while *ignoring the delimiter in double quote string*

for example, we want to choose the column 1 and column 4 of the following data
```bash
"abc@xyz.com,www.example.com",field2,field3,field4
"def@xyz.com",field2,field3,field4
```

## Code

>[!quote]
> You are doing a couple of things wrong here:
> 
> 1. [You are using the shell to parse text.](https://unix.stackexchange.com/q/169716/22222) While this is possible, it is very inefficient. It is slow, hard to write, hard to read and very hard to do properly. The shell just isn't designed for this sort of thing.
>     
> 2. You are trying to parse a csv file *without a csv parser*. CSV is not a simple format. You can have fields that contain the delimiter as you do here. You can also have fields spanning multiple lines. Attempting to parse arbitrary CSV data with simple pattern matching is very, very complicated and extremely hard to get right.


### CSVKit package

```bash
csvcut --columns=1,4 file
```

- [CSVKit](https://github.com/onyxfish/csvkit), which can be installed by `pip install csvkit`


### Use `gawk`

```bash
gawk '{print $1 "," $4}' FPAT='("[^"]+")|[^,]+' test.csv
```

- With `gawk` (**GNU awk**) you can use the **`FPAT` special variable** to define **how a field looks like** instead of being limited to specify a delimiter:
- Here we say: 
	- A field is either a `"` followed by non `"` chars and a closing `"` -> `("[^"]+")` 
	- or `|` 
	- a sequence of non-comma chars -> `[^,]+`

>[!quote]
>- The value of **FPAT** should be a string that provides a **regular expression**. This regular expression **describes the contents of each field**.
>- the regexp used for FPAT **requires** that each field contain *at least one character*.


### Use `-csv`

```bash
awk --csv -v OFS=' ' '
    {
        printf $2  $4
    }
' file
```

- Updated to reflect the [release of GNU awk 5.3](https://groups.google.com/g/comp.lang.awk/c/zQtAPIbzFrc/m/H0uNeJG8BAAJ) for the [`--csv`](https://www.gnu.org/software/gawk/manual/gawk.html#Comma-Separated-Fields) option to enable CSV parsing (also available now in Kernighan's [One True Awk](https://github.com/onetrueawk/awk) so I expect the `gawk 5.3` scripts below will also work there but I don't have a copy of `onetrueawk` to test with)
- **If you have GNU awk 5.3 or later for [`--csv`](https://www.gnu.org/software/gawk/manual/gawk.html#Comma-Separated-Fields)** (or equivalently `-k`) and you neither have to retain the input quotes nor have a separator other than `,`
- `--csv` reads multi-line records and splits quoted fields correctly.



-----------
##  Recommended Notes

- GNU `awk` manual
	- [Nonconstant Field Numbers](https://www.gnu.org/software/gawk/manual/gawk.html#Nonconstant-Field-Numbers)
	- [Splitting-By-Content](http://www.gnu.org/software/gawk/manual/gawk.html#Splitting-By-Content)


- [[AWK command in Unix or Linux with examples]]
- [[sed and awk pocket reference chapter 2]]

- Stack Overflow:
	- [awk ignore quoted delimiters `echo 'a "b1 b2" c'| awk '{print $2}'`](https://stackoverflow.com/questions/56399404/awk-ignore-quoted-delimiters-echo-a-b1-b2-c-awk-print-2)
	- [Escaping separator within double quotes, in awk](https://stackoverflow.com/questions/7804673/escaping-separator-within-double-quotes-in-awk)
	- [Escaping commas inside double quotes as field separator in awk](https://unix.stackexchange.com/questions/496664/escaping-commas-inside-double-quotes-as-field-separator-in-awk)
	- [How to make awk ignore the field delimiter inside double quotes?](https://stackoverflow.com/questions/29642102/how-to-make-awk-ignore-the-field-delimiter-inside-double-quotes)
	- [What's the most robust way to efficiently parse CSV using awk?](https://stackoverflow.com/questions/45420535/whats-the-most-robust-way-to-efficiently-parse-csv-using-awk)