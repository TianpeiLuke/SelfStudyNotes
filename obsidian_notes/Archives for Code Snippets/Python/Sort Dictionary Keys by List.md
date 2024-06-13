---
tags:
  - code
  - code_snippet
  - python/dict
keywords: 
topics: 
language: python
date of note: 2024-04-25
---

## Code Snippet Summary

>[!important]
>Given a dictionary `dictionary` and a list of keys `a_list`, *sort* the dictionary keys according to the list


## Code

### Use `sorted` function

- Use a *custom* **sort key** (called for each `(key, value)` pair produced by `dict.items())

```python
sorted(dictionary.items(), key=lambda pair: a_list.index(pair[0]))
```

#### Use Index Map

```python
index_map = {v: i for i, v in enumerate(a_list)}
sorted(dictionary.items(), key=lambda pair: index_map[pair[0]])
```

- This is faster because the *dictionary lookup* in `index_map` takes $O(1)$ constant time, while the `a_list.index()` call has to *scan through the list each time*, so taking $O(N)$ linear time. 
- Since that scan is called for *each key-value pair* in the dictionary, the *naive sorting option* takes $O(N^2)$ quadratic time, 
- while using a map keeps *the sort efficient* ($O(N \log N$), linearithmic time).

### Scan Through List and Retrieve Value from Dictionary

- If all keys in `a_list` are keys of `dictionary`, then we can simply scan through the list
- This takes $O(N)$ linear time, and allows for extra keys in `a_list` that don't exist in `a`.

```python
[(key, dictionary[key]) for key in a_list if key in dictionary]
```




-----------
##  Recommended Notes

- [[Built-In Function Reversed and Sorted]]

- Stack Overflow:
	- [How to sort a dictionary based on a list in python](https://stackoverflow.com/questions/21773866/how-to-sort-a-dictionary-based-on-a-list-in-python)