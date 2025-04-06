---
tags:
  - code
  - code_snippet
  - python/string
keywords: 
topics: 
language: python
date of note: 2025-04-06
---

## Code Snippet Summary

>[!important]
>Given a string `sentence`, remove heading and trailing whitespaces


## Code

- Use `strip()`

```python
sentence.strip()
```

- `str.strip([chars])`
	- [reference](https://docs.python.org/3.4/library/stdtypes.html#str.strip)
	- Return a copy of the string with the *leading and trailing characters* removed. 
	- The `chars` argument is a string specifying the set of characters to be removed. 
		- If omitted or None, the _chars_ argument defaults to removing whitespace. 
		- The _chars_ argument is not a prefix or suffix; rather, *all combinations* of its values are stripped:

- `str.lstrip([chars])`
	- [reference](https://docs.python.org/3.4/library/stdtypes.html#str.lstrip)
	- remove the *leading characters*
- `str.rstrip([chars])`
	- [reference](https://docs.python.org/3.4/library/stdtypes.html#str.rstrip)
	- remove the *trailing characters*




-----------
##  Recommended Notes

