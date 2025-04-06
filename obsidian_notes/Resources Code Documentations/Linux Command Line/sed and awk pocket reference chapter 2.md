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

# 2: Understanding Basic Operations

## Awk, by Sed and Grep, out of Ed

>[!quote]
>You can trace the lineage of `awk` to `sed` and `grep`, and through those two programs to `ed`, the original UNIX line editor.

>[!quote]
>Entering “`1`” makes the first line the current line, displaying it on the screen. The delete command in `ed` is `d` and here it deletes the current line. Rather than moving to a line and then editing it, you can *prefix an editing command with an **address*** that indicates *which line or range of lines* is the object of the command. If you enter “`1d`”, the first line would be deleted.

>[!quote]
> You can also specify a **regular expression as an address**. To *delete a line containing the word “regular,”* you could issue this command:
> ```bash
> /regular/d
> ```
>where slashes *delimit the regular expression* and “regular” is the string you want to match

>[!quote]
> To delete *all the lines* that contain the regular expression, you’d prefix the command with the letter g for global.
> ```bash
> g/regular/d
> ```
> The **global command** makes all lines that match the regular expression the object
> of the specified command.

>[!quote]
> **Substituting text** (replacing one bit of text with another) is much more interesting. The substitution command, `s`, in `ed` is:
> ```bash
> [address]s/pattern/replacement/flag
> ```
> `pattern` is a **regular expression** that *matches a string* in the *current line* to be
> replaced by *replacement*. For example, the following command replaces the first
> occurr ence of “regular” with “complex” on the current line.
> ```bash
> s/regular/complex/
> ```

- [[Find a word and replace with another one]]

>[!quote]
> To look for *multiple occurrences* on the *same line*, you must specify `g` as a **flag**:
> ```bash
> s/regular/complex/g
> ```
> This command changes *all occurrences* on **the current line**. An *address* must be specified to direct this command to act upon *more than the current line*. The following substitution command specifies an address:
> ```bash
> /regular/s/regular/complex/g
> ```
> 


>[!quote]
> The familiar UNIX utility `grep` is derived from the following **global command** in `ed`:
> ```bash
> g/re/p
> ```
> which stands for **“global regular expression print.”** `Grep` is a *line-editing* command
> that has been extracted from `ed` and made available as an external program. It is
> hard-wired to perform *one editing command*. It takes *the regular expression* as *an
> argument* on the command line and uses it as *the address of lines* to print

>[!example]
> ```bash
> grep ’box’ test
> ```
> It prints all lines matching the regular expression.


>[!quote]
> `Sed` was created as a *special-purpose editor* that was meant to execute scripts exclusively; unlike `ed`, it cannot be used interactively. `Sed` differs from `ed` primarily in that **it is stream-oriented.** By default, *all of the input to `sed` passes through and goes to standard output*. The **input file itself is not changed**. If you actually do want to alter the input file, you typically use the shell mechanism for output redirection, and when you are satisfied with the edits you’ve made, *replace the original file with the modified version.*

>[!info]
>The stream orientation of `sed` has a major impact on how addressing is applied. ... **`Sed` goes through the file**, *a line at a time*, such that *each line becomes the current line*, and the commands are applied to it. The result is that `sed` applies *a command without an address* to **every line in the file**.

>[!quote]
> That is, `sed` commands are **implicitly global**. In `sed`, the previous example has the same result as the following global command in `ed`:
> ```bash
> g/regular/s//complex/
> ```


>[!quote]
>`Awk` was developed as a programmable editor that, like `sed`, is **stream-oriented** and **interprets a script of editing commands.** Where `awk` departs from `sed` is in **discarding the line-editor command set.** It offers in its place a programming language modeled on the **C language**. The `print` statement replaces the `p` command, for example. The concept of **addressing** is carried over, such that:
> ```bash
> /regular/ { print }
> ```
> prints those lines matching “regular”. The braces (`{}`) surround a series of one or more statements that are applied to the same address.

>[!info]
>The advantage of using a programming language **in scripts** is that *it offers many more ways to control* what the programmable editor can do. `Awk` offers **expressions**, **conditional statements**, **loops**, and other *programming constructs*.

>[!quote]
>One of the **most distinctive features** of `awk` is that it **parses**, or **breaks up**, *each input line* and makes *individual words available* for processing with a script. (An editor such as `vi` also recognizes words, allowing you to move word by word, or make a word the object of an action, but these features can only be used interactively.)





-----------
##  Recommended Notes

- [AWK command in Unix/Linux with examples](https://www.geeksforgeeks.org/awk-command-unixlinux-examples/)
- Blog: 
	- [Using AWK to Filter Rows](https://www.tim-dennis.com/data/tech/2016/08/09/using-awk-filter-rows.html)
	- [8 Powerful Awk Built-in Variables – FS, OFS, RS, ORS, NR, NF, FILENAME, FNR](https://www.thegeekstuff.com/2010/01/8-powerful-awk-built-in-variables-fs-ofs-rs-ors-nr-nf-filename-fnr/?ref=vidupdatez.com/image)
	- [AWK command in Unix/Linux with examples](https://www.geeksforgeeks.org/awk-command-unixlinux-examples/)


- [[Use grep to show matched lines with keyword]]
- [[Use awk to Filter Rows]]
- [[Use awk to Parse CSV]]





----------
##  Citations

- *Full Bibliography*: Robbins, A. (2002). Sed and Awk: Pocket Reference, 2nd Edition (2nd edition). O’Reilly Media.



