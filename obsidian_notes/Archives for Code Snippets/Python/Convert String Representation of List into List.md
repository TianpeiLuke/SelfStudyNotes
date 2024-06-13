---
tags:
  - code
  - code_snippet
  - python/string
keywords: 
topics: 
language: python
date of note: 2024-04-27
---

## Code Snippet Summary

>[!important]
>Given a string representation of list `"[1, 2, 3]"`, convert it into the list `[1, 2, 3]`


## Code

```python
import ast

# x_str = '[ "A","B","C" ," D"]'

x = ast.literal_eval(x_str)
# x = ["A", "B", "C", "D"]
```

- [`ast.literal_eval`](https://docs.python.org/library/ast.html#ast.literal_eval):
	- *Evaluate an expression node* or *a string* containing only a **Python literal or container display**. 
	- The string or node provided may only consist of the following Python literal structures: 
		- strings, 
		- bytes, 
		- numbers, 
		- tuples, 
		- lists, 
		- dicts, 
		- sets, 
		- booleans, 
		- `None` and 
		- `Ellipsis`.
	- This can be used for evaluating strings containing Python values *without the need to parse the values oneself.* It is not capable of evaluating arbitrarily complex expressions, for example involving operators or indexing.


-----------
##  Recommended Notes

- [`ast.literal_eval`](https://docs.python.org/library/ast.html#ast.literal_eval):

- Stack Overflow:
	- [How to convert string representation of list to a list](https://stackoverflow.com/questions/1894269/how-to-convert-string-representation-of-list-to-a-list)
	- [Converting a string representation of a list into an actual list object [duplicate]](https://stackoverflow.com/questions/10775894/converting-a-string-representation-of-a-list-into-an-actual-list-object)