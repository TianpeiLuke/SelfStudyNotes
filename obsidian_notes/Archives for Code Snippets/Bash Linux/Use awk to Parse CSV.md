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
>Provide some examples that use `awk` to parse csv file

## Code

### Count the number of Columns

![[Count Number of Columns in CSV file#^48d329]]

- [[Count Number of Columns in CSV file]]

### Extract Specific Column

>[!example] 
> Prints the second column of every row in the CSV file:
> 
> ```bash
> awk -F, '{print $2}' file.csv
> ```
> 

- The command splits each line using commas.
- `$2` refers to the second field, which is printed for every line.

- [[Extract Columns in CSV and Ignore delimiter in double quotes]]


### Filter Rows Based on a Column Value

>[!example] 
> Prints rows where the third column matches a specific value (e.g., `"someValue"`):
> ```bash
> awk -F, '$3 == "someValue" {print}' file.csv
> ```
> 

- The condition `$3 == "someValue"` checks if the third field equals `"someValue"`.
- Only rows that meet the condition are printed.


### Sum a Numeric Column (Skipping the Header)

> [!example]
> Sums the values in the fourth column, ignoring the header row:
> ```bash
> awk -F, 'NR > 1 {sum += $4} END {print sum}' file.csv
> ```
>  

- `NR > 1` skips the header.
- `sum += $4` adds the value of the fourth column for each subsequent line.
- `END {print sum}` outputs the total sum after processing all rows.


### Handling Quoted Fields with GNU AWK (gawk) Using FPAT

> [!example]
> For CSV files with fields enclosed in quotes (which may contain commas), you can use GNU AWK's `FPAT`:
> ```bash
> gawk 'BEGIN { FPAT = "([^,]+)|(\"[^\"]+\")" } { print $1, $2, $3 }' file.csv
> ```

- `FPAT` defines a *field pattern* that matches either a *sequence* of *non-comma characters* or *a quoted string*.
- This approach helps correctly parse fields that *contain commas within quotes*.
- The command prints the first three fields for each row.


### Process Header Row and Print Selected Columns

> [!example]
> Stores the header fields and then prints the first and third columns for the remaining rows:
> ```bash
> awk -F, 'NR==1 {for (i=1; i<=NF; i++) header[i]=$i; next} {print $1, $3}' file.csv
> ```
> 

- For the header row (`NR==1`), the `for` loop stores each header value in an array.
- `next` skips to the next record after processing the header.
- For subsequent rows, the command prints the first and third columns.





-----------
##  Recommended Notes

- GNU `awk` [User Guide](https://www.gnu.org/software/gawk/manual/gawk.html#General-Introduction)

- [[AWK command in Unix or Linux with examples]]
- [[sed and awk pocket reference chapter 1]]
- [[sed and awk pocket reference chapter 2]]

- Blog: 
	- [Using AWK to Filter Rows](https://www.tim-dennis.com/data/tech/2016/08/09/using-awk-filter-rows.html)
	- [8 Powerful Awk Built-in Variables – FS, OFS, RS, ORS, NR, NF, FILENAME, FNR](https://www.thegeekstuff.com/2010/01/8-powerful-awk-built-in-variables-fs-ofs-rs-ors-nr-nf-filename-fnr/?ref=vidupdatez.com/image)
	- [AWK command in Unix/Linux with examples](https://www.geeksforgeeks.org/awk-command-unixlinux-examples/)

- Stack Overflow:
	- [What's the most robust way to efficiently parse CSV using awk?](https://stackoverflow.com/questions/45420535/whats-the-most-robust-way-to-efficiently-parse-csv-using-awk)
	- [How to make awk ignore the field delimiter inside double quotes? [duplicate]](https://stackoverflow.com/questions/29642102/how-to-make-awk-ignore-the-field-delimiter-inside-double-quotes)