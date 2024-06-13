---
tags:
  - code
  - code_snippet
  - regular_expression
keywords: 
topics: 
language: regular expression
date of note: 2024-04-09
---

## Code Snippet Summary

>[!important]
>- Identify the text patterns *on the left before* the target
>- Identify the text patterns *on the right after* the target
>- *Do not include* the patterns before and after the target


## Code


```
(?<=pattern_before).*(?=pattern_after)
```

- `(?<=pattern)matched` **Positive Lookbehind assertion**. matches a `matched` that **follows** a `pattern`, **without** making the `pattern` *part of the match*.
	- It tells the regex engine to *temporarily step **backwards (to left)*** in the string, to check if the text inside the lookbehind can be matched there.
	- identify `matched` by looking for the *existence* of a *prefix* `pattern` on the left but not including it.
	
- `matched(?=pattern)` **Positive Lookahead assertion**. matches a `matched` that **is followed by** a `pattern`, **without** making the `pattern` *part of the match*.
	- identify `matched` by looking for the *existence* of a *suffix* `pattern` on the right but not including it.
	- You can use *any regular expression inside the lookahead* (but **not lookbehind**, as explained below). *Any valid regular expression* can be used inside the lookahead.
	- The *lookahead itself is not a capturing group*. It is not included in the count towards numbering the backreferences.

>[!important]
>Let’s apply `q(?=u)i` to `'quit'`. The *lookahead* is now *positive* and is *followed by another token*. Again, `q` matches `q` and `u` matches `u`. Again, **the match from the lookahead must be discarded**, so the engine **steps back** from `i` in the string to `u`. The lookahead was successful, so the engine continues with `i`. But i cannot match `u`. So this match attempt fails. All remaining attempts fail as well, because there are no more `q`’s in the string.
>
>The regex `q(?=u)i` can *never match anything*. It tries to **match `u` and `i` at the same position**. If there is a `u` immediately after the `q` then the *lookahead succeeds* but then `i` fails to match `u`. If there is anything other than a `u` immediately after the `q` then the lookahead fails.

- here `q(?=u)i` is to match `qi` but `q` need to on the left of `u` so it is not going to match anything


- `(?<!pattern)matched` **Negative Lookbehind assertion**. matches a `matched` that **does not** *follow* a `pattern`, *without* making the `pattern` *part of the match*.
	- compared to *Positive* Lookbehind, we change `'=' `to `'!'` 

- `matched(?!pattern)` **Negative Lookahead assertion**. matches a `matched` that *is* **not** *followed by* a `pattern`, *without* making the `pattern` *part of the match*.
	- compared to *Positive* Lookahead, we change `'=' `to `'!'` 

>[!example]
> ```
> Order\s*(#|Number|number):.*(?=Details:)
> ```



>[!important]
>- The good news is that you can use **lookbehind anywhere** in the regex, not only at the start.
>- The bad news is that **most regex** flavors **do not allow** you to use just *any regex* **inside a lookbehind**, because they cannot apply a regular expression backwards. 
>	- The regular expression engine needs to be able to figure out how many characters to step back before checking the lookbehind. 
>	- When evaluating the lookbehind, the regex engine *determines the length* of the regex *inside the lookbehind*, steps back that many characters in the subject string, and then applies the regex inside the lookbehind from left to right just as it would with a normal regex.



-----------
##  Recommended Notes

- Regular expression [wikipedia](https://en.wikipedia.org/wiki/Regular_expression)
- Regular Expressions Tutorial [https://www.regular-expressions.info](https://www.regular-expressions.info/tutorial.html)
- Lookahead and Lookbehind Zero-Length Assertions [link](https://www.regular-expressions.info/lookaround.html)

>[!quote]
>**Lookahead** and **lookbehind**, collectively called “**lookaround**”, are **zero-length assertions** just like the [start and end of line](https://www.regular-expressions.info/anchors.html), and [start and end of word](https://www.regular-expressions.info/wordboundaries.html) anchors explained earlier in this tutorial. The difference is that lookaround *actually matches characters*, but then *gives up the match*, **returning only the result: match or no match**. That is why they are called “*assertions*”. They do not consume characters in the string, but only assert whether a match is possible or not. Lookaround allows you to create regular expressions that are impossible to create without them, or that would get very longwinded without them.

- Test Regular expression [regex101.com](https://regex101.com/)

- Stack Overflow:
	- [How can I match "anything up until this sequence of characters" in a regular expression?](https://stackoverflow.com/questions/7124778/how-can-i-match-anything-up-until-this-sequence-of-characters-in-a-regular-exp)