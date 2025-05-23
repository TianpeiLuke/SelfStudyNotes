---
tags:
  - book
  - excerpt
  - linux
  - code_manual
aliases: 
keywords: 
topics: 
date of note: 2024-04-09
name: "Sed and Awk: Pocket Reference, 2nd Edition"
author:
  - Dale Dougherty
  - Arnold Robbins
publication: O’Reilly Media, Inc
year: 2002
---

# 1: Power Tools for Editing

## A Pattern-Matching Programming Language

>[!quote]
>Identifying awk as a programming language scares some people away from it. If you are one of them, consider ‘awk’ a different approach to problem solving, one
> in which you have a lot more control over what you want the computer to do.
> 
> `Sed` is easily seen as the flip side of **interactive editing**. A `sed` procedure corresponds closely enough to how you would apply the editing commands manually. *Sed limits you to the methods you use in a text editor*. *Awk offers a more general computational model for processing a file*.


> A typical *example* of an `awk` program is one that transforms data into a *formatted
> report.* The data might be a log file generated by a UNIX program such as `uucp`,
> and the report might summarize the data in a format useful to a system administrator. Another example is a *data processing* application consisting of separate data entry and data retrieval programs. Data entry is the process of recording data in a structured way. Data retrieval is the process of extracting data from a file and generating a report.

>The key to all of these operations is that the *data has some kind of structure*. ... `Awk` allows you to use the structure of a text file in writing the *procedures* for *putting things in* and *taking things out*.
>
>Thus, the benefits of `awk` are best realized when the data has some kind of structure.



>[!quote]
> Some of the things `awk` allows you to do are:
> - View a text file as a textual database made up of records and fields.
> - Use variables to manipulate the database.
> - Use arithmetic and string operators.
> - Use common programming constructs such as loops and conditionals.
> - *Generate formatted reports*.
> - Define functions.
> - *Execute UNIX commands from a script*.
> - Process the result of UNIX commands.
> - Process command-line arguments more gracefully.
> - Work more easily with multiple input streams.







-----------
##  Recommended Notes

- [AWK command in Unix/Linux with examples](https://www.geeksforgeeks.org/awk-command-unixlinux-examples/)





----------
##  Citations

- *Full Bibliography*: Robbins, A. (2002). Sed and Awk: Pocket Reference, 2nd Edition (2nd edition). O’Reilly Media.



