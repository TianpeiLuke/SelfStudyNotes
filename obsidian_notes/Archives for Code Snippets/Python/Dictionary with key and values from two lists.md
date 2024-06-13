---
tags:
  - code
  - code_snippet
  - python/list
  - python/dict
keywords: 
topics: 
language: python
date of note: 2024-04-25
---

## Code Snippet Summary

>[!important]
>Create a dictionary whose keys and values are from two lists `key_list` and `value_list`, respectively 


## Code

### Use list comprehension on dictionary and `zip`

```python
dictionary = {key: value for key, value in zip(key_list, value_list)}
```

- `zip(key_list, value_list)` return an *iterator* that yields tuple `(key_list[i], value_list[i])` for each call
- `for` loop will iterate through the iterator, each time providing a tuple pair `(key, value)`
- use *list comprehension* on dictionary will create key-value map iteratively. 



-----------
##  Recommended Notes

- [[Built-In Function Zip]]
- [[Dictionary with key and values to two lists]]
- [[List Comprehension]]

- Youtube
	- [Python Tutorial: Comprehensions - How they work and why you should be using them](https://www.youtube.com/watch?v=3dt4OGnU5sM)

- Stack Overflow:
	- [Make a dictionary (dict) from separate lists of keys and values](https://stackoverflow.com/questions/209840/make-a-dictionary-dict-from-separate-lists-of-keys-and-values)