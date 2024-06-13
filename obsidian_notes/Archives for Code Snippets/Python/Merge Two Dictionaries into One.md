---
tags:
  - code
  - code_snippet
  - python/dict
keywords: 
topics: 
language: python
date of note: 2024-04-27
---

## Code Snippet Summary

>[!important]
>Given two dictionaries `dict1` and `dict2`, merge the keys and values of both into one `dict_merge`


## Code

### Shallow Merge with `|`

- For dictionaries `dict1` and `dict2`, their shallowly-merged dictionary `dict_merge` takes values from `dict2`, replacing those from `dict1`.

```python
dict_merge = dict1 | dict2
```

### Use `**` to unpack key-value pairs of dictionaries

```python
dict_merge = {**dict1, **dict2}
```

- `**` unpack the dictionary into tuples of key value `(key, value)`
- use `{}` to construct the dictionary with tuple of (key, value)

### Use `update()`

```python
def merge_two_dicts(x, y):
    z = x.copy()   # start with keys and values of x
    z.update(y)    # modifies z with keys and values of y
    return z
```

- first copy one dictionary `dict1`
- then update the dictionary with key, values from `dict2`



-----------
##  Recommended Notes

- [[List Comprehension]]
- [[Asterisk and Double Asterisk in Python]]

- Stack Overflow:
	- [How do I merge two dictionaries in a single expression in Python?](https://stackoverflow.com/questions/38987/how-do-i-merge-two-dictionaries-in-a-single-expression-in-python)
