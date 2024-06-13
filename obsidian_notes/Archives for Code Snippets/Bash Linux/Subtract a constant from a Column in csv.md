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
>Subtract a constant number to a column in csv file


## Code

>[!example]
 >Subtract constant 10 from column 1
> ```bash
> awk '{print ($1 - 10)}' file
> ```
> or 
> ```bash
> awk '{$1 = $1 - 10; print}' file
> ```



>[!example]
>Subtract the value of the first row to every number in column 1
> ```bash
> awk '{
>        if(NR == 1) {
>            shift = $1
>        }
> 
>        print ($1 - shift)
> }' file
> ```
> or
> 
> ```bash
> awk 'NR == 1 {shift = $1} {$1 = $1 - shift; print}' file
> ```

- Recall that `NR` is the **number of records read so far**: 
	- one in the first record, two in the second, and so on.
	- `awk` increments `NR` and `FNR` each time it reads a record, instead of setting them to the absolute value of the number of records read.
- In above program, `NR == 1` means **the first row**
- `print ($1 - shift)` means print the 1st column minus `shift`


-----------
##  Recommended Notes

- GNU `awk` manual
	- [Nonconstant Field Numbers](https://www.gnu.org/software/gawk/manual/gawk.html#Nonconstant-Field-Numbers)




[[sed and awk pocket reference chapter 2]]

- Stack Overflow:
	- [How to subtract a constant number from a column](https://stackoverflow.com/questions/3376655/how-to-subtract-a-constant-number-from-a-column)

