---
tags:
  - code
  - code_snippet
  - python/built-in
  - python/filter
keywords: 
topics: 
language: python
date of note: 2024-04-23
---

## Code Snippet Summary

>[!important]
>Be Familiar with *built-in function* `filter` and `map`  in python
>- `filter`: apply a *boolean function* on each item of iterable (list, set, dict) and return a **iterator** that only keep the element if the corresponding function return `True`, i.e. the iterator *filter out* `False` values
>- `map`: apply a function on each item of iterable, keep corresponding return value in the list


## Code

### Filter

```python 
# remove all negative numbers in the list a_list

non_negative = [x for x in filter(lambda s: s >= 0, a_list)]

# equivalent

non_negative = [x in a_list if x >= 0]

# general case
res = [x for x in filter(bool_fun, a_list)]
res = [x for x in a_list if bool_fun(x)]
```

- `filter(fun, iterable)`: [reference](https://docs.python.org/3/library/functions.html#filter)
	- Construct an **iterator** from those elements of _iterable_ for which _function_ is **true**. 
	- _iterable_ may be either a sequence, a container which supports iteration, or an iterator. 
	- If _function_ is `None`, the *identity function* is assumed, that is, all elements of _iterable_ that are *false* are **removed**.
	- See [`itertools.filterfalse()`](https://docs.python.org/3/library/itertools.html#itertools.filterfalse "itertools.filterfalse") for the complementary function that returns elements of _iterable_ for which _function_ is false.


### Map

```python 
# map all negative values to zero in the list a_list

non_negative_mapped = [x for x in map(lambda x: 0 if x < 0 else x, a_list)]

# equivalent

non_negative_mapped = [0 if x < 0 else x for x in a_list]

# general case
res = [x for x in map(fun, a_list)]
res = [fun(x) for x in a_list]

# two argument
def sum_two(x, y):
	return x + y

sum_two_res = [x for x in map(sum_two, a_list, b_list)]
```


- `map(fun, iterable, *iterables)`:  [reference](https://docs.python.org/3/library/functions.html#map)
	- Return an **iterator** that applies _function_ to every item of _iterable_, **yielding** the results. 
	- If **additional** _iterables_ **arguments** are passed, _function_ must take that many **arguments** and is applied to the items from all iterables **in parallel**. 
	- With **multiple iterables**, the iterator stops when the **shortest iterable is exhausted**. 
	- For cases where the function inputs are already arranged into argument tuples, see [`itertools.starmap()`](https://docs.python.org/3/library/itertools.html#itertools.starmap "itertools.starmap").


-----------
##  Recommended Notes

- `filter()`: [reference](https://docs.python.org/3/library/functions.html#filter)
- `map()`: [reference](https://docs.python.org/3/library/functions.html#map)

- [[List Comprehension]]

- Stack Overflow:
	- [List comprehension vs map](https://stackoverflow.com/questions/1247486/list-comprehension-vs-map)
	- [List comprehension vs. lambda + filter](https://stackoverflow.com/questions/3013449/list-comprehension-vs-lambda-filter)