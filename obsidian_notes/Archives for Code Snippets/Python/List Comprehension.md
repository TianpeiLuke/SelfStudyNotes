---
tags:
  - code
  - code_snippet
  - python/list
keywords: 
topics: 
language: python
date of note: 2024-04-23
---

## Code Snippet Summary

>[!important]
>Be Familiar with *List Comprehension* in place of for-loops


## Code

### List Comprehension

```python 
# a_list is a list
# 
# res = []
# for x in a_list:
#    res.append(x+1)   

res = [x + 1 for x in a_list]
```

### List Comprehension with One Condition

```python 

# even = []
# for x in range(10):
#    if x % 2 == 0:
#        even.append(x)   

even = [x for x in range(10) if x % 2 == 0]
```

### List Comprehension with Multiple Conditions

```python 
# a_list is a list
# 
# res = []
# for x in range(10):
#    if x % 2 == 0:
#        continue
#    if x % 3 == 0:
#        continue
#    res.append(x)

res = [x for x in range(10) 
	   if x % 2 != 0 
	   if x % 3 != 0
	   ]
```

### Multiple Lists (Flatten Matrix to List)

```python 
# a_mat is a list of lists
# 
# res = []
# for row in a_mat:
#    for elem in row:
#        res.append(elem)

res = [elem for row in a_mat for elem in row]
```

### If-Else

```python 

# res = []
# for x in range(10):
#    if x % 2 == 0:
#        res.append('even')
#    else:
#        res.append('old')


res = ['even' if x % 2 ==0 else 'old' for x in range(10)]
```

### Nested List (Reshape List to Matrix)

```python 
# a_list is a list of 25 elements
# 
# res = []
# for row_id in range(5):
#    row = []
#    for col_id in range(5):
#        row.append(a_list[row_id*5 + col_id])
#    res.append(row)

res = [
	   [a_list[row_id*5 + col_id] for col_id in range(5)] 
	   for row_id in range(5)
	   ]
```




-----------
##  Recommended Notes

- [[Asterisk and Double Asterisk in Python]]
- [[Dictionary with key and values from two lists]]
- [[Dictionary with key and values to two lists]]
- [[Merge Two Dictionaries into One]]

- Stack Overflow:
	- [Python3: Conditional extraction of keys from a dictionary with comprehension](https://stackoverflow.com/questions/17583225/python3-conditional-extraction-of-keys-from-a-dictionary-with-comprehension)
	- [Extract first item of each sublist in Python](https://stackoverflow.com/questions/25050311/extract-first-item-of-each-sublist-in-python)
	- [How do I merge two dictionaries in a single expression in Python?](https://stackoverflow.com/questions/38987/how-do-i-merge-two-dictionaries-in-a-single-expression-in-python)

- Youtube
	- [10 Python Comprehensions You SHOULD Be Using](https://www.youtube.com/watch?v=twxE0dEp3qQ)
	- [Python Tutorial: Comprehensions - How they work and why you should be using them](https://www.youtube.com/watch?v=3dt4OGnU5sM)