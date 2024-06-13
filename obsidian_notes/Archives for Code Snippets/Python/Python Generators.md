---
tags:
  - code
  - code_snippet
  - python/generator
keywords: 
topics: 
language: python
date of note: 2024-04-12
---

## Code Snippet Summary

>[!important]
>A **generator** in python is a function that `yield` output instead of `return` them. This makes sure when we rerun the function it will keep the internal state and *yield* one result in a time.
>- Generator functions allow you to declare a function that behaves like an **iterator**, i.e. it can be used in a *`for` loop*.


## Code

```python
# a generator that yields items instead of returning a list
def firstn(n):
	num = 0
	while num < n:
		yield num
		num += 1
```

### Visit the next value

```python
x = next(firstn(10))
# x = 0

x = next(firstn(10))
# x = 1

...

x = next(firstn(10))
# x = 9

x = next(firstn(10))
# StopIteration
```

## Why use Generator ?

>[!quote]
>The performance improvement from the use of generators is the result of the *lazy (**on demand**) generation of values*, which translates to **lower memory usage**. Furthermore, we *do not need to wait* until all the elements have been generated before we start to use them. This is similar to the benefits provided by iterators, but the *generator makes building iterators easy*.
>-- *# Improved Performance* [reference](https://wiki.python.org/moin/Generators)


-----------
##  Recommended Notes

- Python wiki: Generators [reference](https://wiki.python.org/moin/Generators)
- [[Design Pattern Iterator Pattern]]

- Youtube video
	- [Python Tutorial: Generators - How to use them and the benefits you receive](https://www.youtube.com/watch?v=bD05uGo_sVI&ab_channel=CoreySchafer)