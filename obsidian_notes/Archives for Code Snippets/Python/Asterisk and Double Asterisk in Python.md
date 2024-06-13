---
tags:
  - code
  - code_snippet
  - python/variadic_arguments
keywords: 
topics: 
language: python
date of note: 2024-04-24
---

## Code Snippet Summary

>[!important]
>Understand the role of `*` and  `**` in Python



## Code

### Exponential Arithmetic

the expression of $2^3$
```python
2 ** 3 
```

### For repeatedly extending the list-type containers

- Python also supports that multiply the _list-type container (includes tuple)_ and _int_ for extending container data by given number times.

```python
[1] * n 
# [1, 1, ..., 1]
```

### For Variadic Positional Arguments


>[!quote]
>If the form “`*identifier`” is present, it is initialized to a tuple receiving any excess positional parameters, defaulting to the empty tuple. If the form “`**identifier`” is present, it is initialized to a new ordered mapping receiving any excess keyword arguments, defaulting to a new empty mapping of the same type. Parameters after “`*`” or “`*identifier`” are keyword-only parameters and may only be passed by keyword arguments.
>-- [Function Definitions: Reference](https://docs.python.org/3.12/reference/compound_stmts.html#function-definitions)

>[!quote]
>If the syntax `*expression` appears in the function call, `expression` must evaluate to an [iterable](https://docs.python.org/3.12/glossary.html#term-iterable). Elements from these iterables are treated as if they were additional positional arguments. For the call `f(x1, x2, *y, x3, x4)`, if _y_ evaluates to a sequence _y1_, …, _yM_, this is equivalent to a call with M+4 positional arguments _x1_, _x2_, _y1_, …, _yM_, _x3_, _x4_.
>
>-- [Function Calls](https://docs.python.org/3.12/reference/expressions.html#calls)


```python
def fun(*args, **kwargs)
```

- `*args` means accepting the arbitrary numbers of **positional arguments** 
- `**kwargs` means accepting the arbitrary numbers of **keyword arguments**. 
- In here, `*args`, `**kwargs` are called **packing**.
- using `*input_list` as input, Python would pack all positional arguments into a list `input_list`
- similarly, using `**dictionary` as input, Python would pack all keyword arguments into a dictionary `dictionary`

- we are passing the arguments which can hold **arbitrary numbers of positional or keyword values**. 
- The arguments passed as positional are stored in a _tuple_ called `args`, and the arguments passed as keyword are stored in a _dict_ called `kwargs`.

>[!important]
>As refered before, the _keyword arguments_ can not be declared before _positional arguments_, so following code should raises exceptions:
> ```python
> def fun(**kwargs, *args) # Execption
> ```

>[!example]
> ```python
> def f(x1, x2, x3):
> 	return x1 + x2 + x3
> 
> x_list = [1, 2, 3]
> 
> res = f(*x_list) 
> 
> # equivalent
> 
> res = f(1, 2, 3)
> ```


- Multiple positional arguments

```python
def f(x1, x2, x3, x4):
	return x1 + x2 + x3 + x4

x_23 = [2, 3]

res = f(1, *x_23, 4)
# = f(1, 2, 3, 4)
```


>[!quote]
>A consequence of this is that although the `*expression` syntax may appear **after** *explicit keyword* arguments, it is processed **before** the keyword arguments (and any `**expression` arguments – see below).
>
>It is unusual for both keyword arguments and the `*expression` syntax to be used in the same call, so in practice this confusion does not often arise.
>
>-- [Function Calls](https://docs.python.org/3.12/reference/expressions.html#calls)

```python
def f(a, b):
	print(a, b)

f(b=1, *(2,))
# = f(2,1) = f(a=2, b=1)
# print(2,1)

f(a=1, *(2,))
# TypeError since it is equivalent to f(a=1, a=2)

f(1, *(2,))
# = f(a=2, b=1)
# print(2,1)

```

### For Variadic Keyword Arguments

>[!quote]
>If the syntax `**expression` appears in the function call, `expression` must evaluate to a [mapping](https://docs.python.org/3.12/glossary.html#term-mapping), the contents of which are treated as additional keyword arguments. If a parameter matching a *key* has already been given a *value* (by an *explicit keyword argument*, or from another unpacking), a [`TypeError`](https://docs.python.org/3.12/library/exceptions.html#TypeError "TypeError") exception is raised.
>
>-- [Function Calls](https://docs.python.org/3.12/reference/expressions.html#calls)

```python
def f(x1, x2, x3):
	return x1 + x2 + x3
	
input_dict = {x1:1, x2: 2, x3: 3}

res = f(**input_dict)
# = f(x1=1, x2=2, x3=3)
```

>[!quote]
>When `**expression` is used, each *key* in this mapping must be a *string*. Each value from the mapping is assigned to the *first formal parameter eligible* for keyword assignment whose **name is equal to the key**. A key need not be a Python identifier (e.g. `"max-temp °F"` is acceptable, although it will not match any formal parameter that could be declared). If there is *no match* to a formal parameter the *key-value pair* is collected by the `**` parameter, if there is one, or if there is not, a [`TypeError`](https://docs.python.org/3.12/library/exceptions.html#TypeError "TypeError") exception is raised.
>
>-- [Function Calls](https://docs.python.org/3.12/reference/expressions.html#calls)

### Unpacking the Containers

- The \* can also be used for **unpacking the containers**. Its principles is similar to above. 
	- `*[1, 2, 3]` will show `1` and `2` and `3` individually instead of as a list
- The easiest example is that we have data in the form of a _list_, _tuple_ or _dict_, and a function take variable arguments:
```python
def f(*x):
	return [2*s for s in x]

x_list = [1, 2, 3]
res = f(*x_list)
# res = [2, 4, 6]

res = f(x_list)
# res = [[1, 2, 3, 1, 2, 3]]
```

- Because the `f()` take the *variable arguments*, we need to **unpack** the our **list data** and *pass* it to that function. 
	- In this case, if we pass the `x_list` as `*x_list`, *every elements* of the `x_list` list will be *unpacked*, then *stored* in list called `x`. 
	- If pass that list `x_list` to the function *without unpacking*, the `x` will has only *one* `x_list` list **not** *all elements* of `x_list`.
	- `f(*x_list)` the internal list `x` contain all element of `x_list`, i.e. `x = x_list`
	- `f(x_list)`, the internal list `x` contain one element `x_list`, i.e. `x = [x_list]`
- For *tuple*, it could be done exactly same to list, and 
- for *dict*, just use `**` instead of `*`.


- And there is also one more type of **unpacking**, it is *not for function* but just **unpack the list or tuple data** *to other variables* **dynamically**.

```python
numbers = [1, 2, 3, 4, 5, 6]

# The left side of unpacking should be list or tuple.
*a, = numbers
# a = [1, 2, 3, 4, 5, 6]

*a, b = numbers
# a = [1, 2, 3, 4, 5]
# b = 6

# a, b = numbers
# ValueError: too many values to unpack (expected 2)

a, *b, = numbers
# a = 1
# b = [2, 3, 4, 5, 6]

a, *b, c = numbers

# a = 1
# b = [2, 3, 4, 5]
# c = 6
```

- Here, the `*a` and `*b` will do *packing* the remaining values again except the single unpacked values which are assigned other normal variables after unpacking the list or tuple. 
- It is same concepts to **packing for variadic arguments**.

-----------
##  Recommended Notes

- Function Definition [reference](https://docs.python.org/3.12/reference/compound_stmts.html#function-definitions)
- Function Calls [reference](https://docs.python.org/3.12/reference/expressions.html#calls)
- [More on Defining Functions](https://docs.python.org/3/tutorial/controlflow.html#more-on-defining-functions)

- Stack Overflow:
	- [What does ** (double star/asterisk) and * (star/asterisk) do for parameters?](https://stackoverflow.com/questions/36901/what-does-double-star-asterisk-and-star-asterisk-do-for-parameters)
	- [What does asterisk * mean in Python? [duplicate]](https://stackoverflow.com/questions/400739/what-does-asterisk-mean-in-python)


- Medium
	- [Understanding the asterisk(\*) of Python](https://medium.com/understand-the-python/understanding-the-asterisk-of-python-8b9daaa4a558)

- Youtube:
	- [`*Args` and `**Kwargs` in Python](https://www.youtube.com/watch?v=4jBJhCaNrWU)