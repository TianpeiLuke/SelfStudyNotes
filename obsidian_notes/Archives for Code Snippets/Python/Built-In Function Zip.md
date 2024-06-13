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
>Be Familiar with Python Built-In function `zip()` that *merge* two list of the same size into *a list of tuples*


## Code

### Join two lists

```python

a = [1, 2, 3, 4]
b = ['a', 'b', 'c', 'd']

joint = zip(a, b)
# joint = [(1, 'a'), (2, 'b'), (3, 'c'), (4, 'd')]

```

### Join multiple lists

```python

a = [1, 2, 3, 4]
b = ['a', 'b', 'c', 'd']
c = [0.1, 0.2, 0.3, 0.4]

joint = zip(a, b, c)
# joint = [(1, 'a', 0.1), (2, 'b', 0.2), (3, 'c', 0.3), (4, 'd', 0.4)]

```

### Transpose List of Lists (Matrix Transpose)

```python

matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]


matrix_transposed = zip(*matrix)

# matrix_transposed = [[1, 4, 7], [2, 5, 8], [3, 6, 9]]

```


- `zip(*iterables, strict=False)`: [reference](https://docs.python.org/3/library/functions.html#zip)
	- Iterate over **several** *iterables* **in parallel**, producing **tuples** with an item from each one.
	- [`zip()`](https://docs.python.org/3/library/functions.html#zip "zip") returns an **iterator** of *tuples*, where the _i_-th tuple contains the _i_-th element from each of the argument iterables.
	- Another way to think of [`zip()`](https://docs.python.org/3/library/functions.html#zip "zip") is that it **turns rows into columns**, and **columns into rows**. This is similar to [transposing a matrix](https://en.wikipedia.org/wiki/Transpose).
	


>[!important]
>- [`zip()`](https://docs.python.org/3/library/functions.html#zip "zip") is lazy: The elements *won’t be processed until* the iterable is iterated on, e.g. by a `for` loop or by wrapping in a [`list`](https://docs.python.org/3/library/stdtypes.html#list "list").

### Dividing Inputs into a set of Chunks with size n

>[!important]
>The left-to-right evaluation order of the iterables is guaranteed.

```python
zip(*[iter(s)]*n, strict=True)
```

- Here `[iter(s)]*n` repeats the _same_ iterator `n` times
- each output tuple has the result of `n` calls to the iterator.
- This has the effect of dividing the input into n-length chunks.

### Unzip a list of tuples

```python

x_tuples = [(1, 'a'), (2, 'b'), (3, 'c')]

index, value = zip(*x_tuples)

# index = (1, 2, 3)
# value = ('a', 'b', 'c')


x_tuples = zip(index, value)
index2, value2 = zip(*zip(index, value))

list(index2) == index
list(value2) == value
```

- Use `zip(*List_of_Tuples)` to decompose the list of tuples into separate tuples, *i*-th element in the *j*-th tuple corresponding to *j*-th item in the tuple *i* in the original list.

### Deal with Different Length

>[!info]
>One thing to consider is that the iterables passed to [`zip()`](https://docs.python.org/3/library/functions.html#zip "zip") could have *different lengths*; sometimes by design, and sometimes because of a bug in the code that prepared these iterables. Python offers **three different approaches** to dealing with this issue:

#### Shortest Iterable

- By default, [`zip()`](https://docs.python.org/3/library/functions.html#zip "zip") stops when **the shortest iterable is exhausted**. It will ignore the remaining items in the longer iterables, *cutting off* the result to the length of the shortest iterable:

```python
list(zip(range(3), ['fee', 'fi', 'fo', 'fum']))
# [(0, 'fee'), (1, 'fi'), (2, 'fo')]
```

#### `ValueError` Exception

- [`zip()`](https://docs.python.org/3/library/functions.html#zip "zip") is often used in cases where the iterables are assumed to be of equal length. In such cases, it’s recommended to use the `strict=True` option. Its output is the same as regular [`zip()`](https://docs.python.org/3/library/functions.html#zip "zip"):

```python
list(zip(range(3), ['fee', 'fi', 'fo', 'fum'], strict=True))
# [(0, 'fee'), (1, 'fi'), (2, 'fo')]
```

Unlike the default behavior, it raises a [`ValueError`](https://docs.python.org/3/library/exceptions.html#ValueError "ValueError") if one iterable is *exhausted before the others*

#### Pad the Shorter Iterables

- Shorter iterables can be **padded with a constant value** to make all the iterables have the same length. This is done by [`itertools.zip_longest()`](https://docs.python.org/3/library/itertools.html#itertools.zip_longest "itertools.zip_longest").


-----------
##  Recommended Notes

- `zip` [reference](https://docs.python.org/3/library/functions.html#zip)