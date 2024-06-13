---
tags:
  - code
  - code_snippet
  - python/list
  - python/dict
keywords: 
topics: 
language: python
date of note: 2024-04-26
---

## Code Snippet Summary

>[!important]
>Given a dictionary, extract its keys and values into two lists `key_list` and `value_list`, respectively 


## Code

### Direct call on `.key()` and `.value()` methods

```python
keys = list(dictionary.keys())
values = list(dictionary.values())
```


### Use  `zip` on `.iteritems()`

```python
(key_list, value_list) = zip(*dictionary.iteritems())
```

- `dictionary.iteritems()` return a *iterator* that yields the tuple `(key, value)` at each call
- `*dictionary.iteritems()` unpack the result yield from iterator into two positional arguments
- `zip(*dictionary.iteritems())` return an *iterator* that yields tuple `(dictionary.key()[i], dictionary.value()[i])` for each call




-----------
##  Recommended Notes

- [[Dictionary with key and values from two lists]]
- [[Built-In Function Zip]]
- [[Asterisk and Double Asterisk in Python]]


- Stack Overflow:
	- [Turn a dictionary into two lists, one for keys and the other for values?](https://stackoverflow.com/questions/21869973/turn-a-dictionary-into-two-lists-one-for-keys-and-the-other-for-values)