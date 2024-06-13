---
tags:
  - code
  - code_snippet
  - linux/grep
keywords: 
topics: 
language: linux
date of note: 2024-04-04
---

## Code Snippet Summary

>[!important]
>Match patterns in bash using `grep`

## Code

>[!info]
> - The `grep` command is one of the most useful commands in a Linux terminal environment. 
> - The name `grep` stands for **“global regular expression print”.** 
> - This means that you can use `grep` to check whether the input it receives matches a specified pattern. 
> - This seemingly trivial program is extremely powerful; its ability to *sort* input based on *complex rules* makes it a popular link in many command chains.

### Search Keyword via Literal Match

- you can use `grep` to match **literal patterns** within a text file.
- if you pass `grep` a word to search for, it will print out **every line** in the file containing that word.

```bash
grep "GNU" GPL-3
```

- *The first argument*, `"GNU"`, is the pattern you’re searching for, while the *second argument*, `GPL-3`, is the *input file* you wish to search.
- By default, `grep` will search for *the exact specified pattern* within the input file and return the lines it finds. 
	- You can make this behavior more useful though by adding some optional flags to `grep`.
- To interpret PATTERNS as **fixed strings**, not regular expressions (regex) when fgrep used.
```bash
grep -F "GNU" GPL-3
```

#### Additional Control Parameters

>[!example]
> If you want `grep` to **ignore the “case”** of your search parameter and search for both *upper-* and *lower-case* variations, you can specify the `-i` or `--ignore-case` option.
> 
> ```bash
> grep -i "license" GPL-3
> ```


>[!example]
>If you want to find all lines that **do not** contain a specified pattern, you can use the `-v` or `--invert-match` option.
> ```bash
> grep -v "the" BSD
> ```


>[!example]
>It is often useful to know the **line number** that the matches occur on. You can do this by using the `-n` or `--line-number` option. Re-run the previous example with this flag added:
> ```bash
> grep -vn "the" BSD
> ```


>[!example]
>Search **Recursively**, i.e. look for all files in the **current directory** and in **all of its subdirectories** in Linux for the word ‘httpd’:
> ```bash
> grep -R 'httpd' .
> grep -r 'httpd' .
> ```


>[!example]
>Search and display **the total number of times** that the string ‘nixcraft’ appears in a file named frontpage.md:
> ```bash
> grep -c 'nixcraft' frontpage.md
> ```


### Search Keyword with Regular Expression

#### Anchor Matches

- **Anchors** are *special characters* that specify *where* in the line a match must occur to be valid.

>[!example]
>Search for the lines that match `GNU` at the **very beginning** of the line.
> ```bash
> grep "^GNU" GPL-3
> ```

>[!example]
>Similarly, you use the `$` anchor **at the end of a pattern** to indicate that the match will only be valid if it occurs at **the very end of a line**.
> ```bash
> grep "and$" GPL-3
> ```

#### Matching Any Characters

- The period character **(.)** is used in regular expressions to mean that *any single character* can exist at the specified location.

>[!example]
>Match anything in the `GPL-3` file that has *two characters* and then the string `cept`
> ```bash
> grep "..cept" GPL-3
> ```

#### Bracket Expressions

- By placing a **group of characters** within *brackets* (`\[` and `\]`), you can specify that the character at that position can be **any one character** found *within the bracket group*.

>[!example]
find the lines that contain `too` or `two`
> ```bash
> grep "t[wo]o" GPL-3
> ```

- You can have the pattern match anything **except** the characters *within a bracket* by beginning the list of characters within the brackets with a `^` character.

>[!example]
This example is like the pattern `.ode`, but will not match the pattern `code`
> ```bash
> grep "[^c]ode" GPL-3
> ```

- Another helpful feature of brackets is that you can specify *a range of characters* instead of individually typing every available character.

>[!example]
find every line that begins with a capital letter, you can use the following pattern:
> ```bash
> grep "^[A-Z]" GPL-3
> ```

- We can use **POSIX character classes** instead of character ranges like you just used.

```bash
grep "^[[:upper:]]" GPL-3
```

#### Repeat Pattern Zero or More Times

- one of the most commonly used meta-characters is the **asterisk**, or `*`, which means **“repeat the previous character or expression zero or more times”**.

- To find each line in the `GPL-3` file that contains an opening and closing parenthesis,
```bash
grep "([A-Za-z ]*)" GPL-3
```

#### Escaping Meta-Characters

- There are times where you’ll need to search for **a literal period** or **a literal opening bracket**.
- Because these characters have special meaning in regular expressions, you need to **“escape”** these characters to tell `grep` that you do not wish to use their special meaning in this case.

```bash
grep "^[A-Z].*\.$" GPL-3
```

#### Extended Regular Expressions

- The `grep` command supports a more **extensive regular expression language** by using the `-E` flag or by calling the **`egrep` command** instead of `grep`.


>[!example] **Grouping**
>One of the most useful abilities that extended regular expressions open up is the ability to **group expressions together** to manipulate or reference as one unit.
>- To group expressions together, *wrap them in parentheses*.
>- If you would like to use parentheses without using extended regular expressions, you can **escape** them with the backslash to enable this functionality. 
>- This means that the following three expressions are functionally equivalent:
> ```bash
> grep "\(grouping\)" file.txt
> grep -E "(grouping)" file.txt
> egrep "(grouping)" file.txt
> ```


>[!example] **Alternation**
>Similar to how bracket expressions can specify different possible choices for single character matches, *alternation* allows you to **specify alternative matches** for strings or expression sets.
> - To indicate alternation, use the **pipe character** `|`. 
> - These are often used **within parenthetical grouping** to specify that one of two or more possibilities should be considered a match.
> - Alternation can select between *more than two choices* by adding additional choices within the selection group separated by additional pipe (`|`) characters.
> ```bash
> grep -E "(GPL|General Public License)" GPL-3
> ```


>[!example] **Quantifiers**
>Like the `*` meta-character that matched the previous character or character set **zero or more times**, there are other meta-characters available in extended regular expressions that **specify the number of occurrences**.
>- To match a character **zero or one times**, you can use the `?` character. 
>	- This makes character or character sets that came before optional, in essence.
> ```bash
> grep -E "(copy)?right" GPL-3
> ```
> - The `+` character matches an expression **one or more times**.
> ```bash
> grep -E "free[^[:space:]]+" GPL-3
> ```


>[!example] **Specifying Match Repetition**
>To specify **the number of times** that a match is **repeated**, use the brace characters (`{` and `}`). 
>- These characters let you specify an exact number, a range, or an upper or lower bounds to the amount of times an expression can match.
>
> ```bash
> grep -E "[AEIOUaeiou]{3}" GPL-3
> ```
> - To match any words that have between 16 and 20 characters, use the following expression:
> ```bash
> grep -E "[[:alpha:]]{16,20}" GPL-3
> ```





-----------
##  Recommended Notes

- `grep` command: *prints* lines that contain a **match** for one or more patterns. [manual reference](https://www.gnu.org/software/grep/manual/grep.html)

- Tutorial 
	- [Using Grep & Regular Expressions to Search for Text Patterns in Linux](https://www.digitalocean.com/community/tutorials/using-grep-regular-expressions-to-search-for-text-patterns-in-linux)
	- [How to use grep command In Linux / UNIX with examples](https://www.cyberciti.biz/faq/howto-use-grep-command-in-linux-unix/)


- Stack Overflow:
	- [How to get the part of a file after the first line that matches a regular expression](https://stackoverflow.com/questions/7103531/how-to-get-the-part-of-a-file-after-the-first-line-that-matches-a-regular-expres)

- Unix Stack Exchange
	- [How do you extract a whole word containing substring?](https://unix.stackexchange.com/questions/260457/how-do-you-extract-a-whole-word-containing-substring)

- [[Find a word and replace with another one]]
