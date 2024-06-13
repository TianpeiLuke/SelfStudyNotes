---
tags:
  - code
  - code_snippet
  - python/zip
keywords: 
topics: 
language: python
date of note: 2024-04-24
---

## Code Snippet Summary

>[!important]
>Given a list `s`, divide the list into a list of chunks, each chunk of length `n`


## Code


```python
zip(*[iter(s)]*n, strict=True)
```


- `iter(s)` returns a iterator with input list `s` 
- `[iter(s)]` is a list who element is returned by `iter(s)` i.e. **a list of one iterators**
- `[iter(s)]*n` is a *list of* **n iterators**, i.e. the length of this list is `n` and each element is a iterator, which is returned by `iter(s)`
	- Note that since the element of list is an *iterator*, its value is only retrieved when such element is referred by `__getitem__()` call of the list.
	- the order of calling the iterator would be from left to right
	- since `iter(s)` is called for each element of list, we call the list `s` **n**-times in a row from left to right
- `*[iter(s)]*n` extract all elements in the list, and place them in original order as the list
- `zip(*[iter(s)]*n)` would *collect the value* returned by each call of `iter(s)` in a row of *n*, and `zip` them into a tuple of size *n*. 


>[!example]
> ```python
> [x for x in zip(*[iter(range(8))]*2, strict=True)]
> ```
> - `iter(range(8))` return an iterator and each call returns one number from 0-7, in order
> - `[iter(range(8))]` return a list of one iterator
> - `[iter(range(8))]*2` return a list of two iterator; calling this function would return `[0,1]`, then `[2,3]`, then `[4,5]` etc.
> - `*[iter(range(8))]*2` would unpack the two iterators as *variadic positional arguments* of `zip()`. 
> - `zip(*[iter(range(8))]*2)` would merge tuples into one. returns `(0,1)` then `(2,3)`, then `(4,5)` etc.
> - Returns `[(0,1), (2,3), (4,5), (6,7)]`





-----------
##  Recommended Notes

- [[Built-In Function Zip]]
- [[Built-In Function Iter and Next]]
- [[Asterisk and Double Asterisk in Python]]

- `zip` [reference](https://docs.python.org/3/library/functions.html#zip)
- `iter()`: [reference](https://docs.python.org/3/library/functions.html#iter)