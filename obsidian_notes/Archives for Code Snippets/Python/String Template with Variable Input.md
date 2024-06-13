---
tags:
  - code
  - code_snippet
  - python/string
keywords: 
topics: 
language: python
date of note: 2024-04-12
---

## Code Snippet Summary

>[!important]
>Construct a **string template** with a variable input

## Code

- **F-string**: using the prefix `f` before string as `f'xxxx {var}'` where `var` is the variable declared above. 

```python
var1 = ... # string
var2 = ... # floating point value

template = f'this is a template for var1 = {var1}, var2 = {var2}'
```


- equivalent forms of template
	- using `'..{}..'.format()`
	- using `%`

```python
...

template = 'this is a template for var1 = {var1}, var2 = {var2}'.format(var1 = var1, var2 = var2)

template = 'this is a template for var1 = {}, var2 = {}'.format(var1, var2)

template = 'this is a template for var1 = %s, var2 = %f' % (var1, var2)
```

- We can create the string template first and add values later

```python
template = 'this is a template for var1 = {var1}, var2 = {var2}'

string_output = template.format(var1 = var1, var2 = var2)
```

## Additional Controls

- `{var:k}`: for numeric `var` only show the first `k` digits
- `{var:0k}`: for numeric `var` only show the first `k` digits with *zero padding*

```python
...

# print numeric with two digits
template = f'this is a template for var2 = {var2:02}'
template = 'this is a template for var2 = {:02}'.format(var2)
template = 'this is a template for var2 = %02f' % (var2)
```

- `{var:.k}`: for numeric `var` *rounds* the precision up to `k` decimal points
- `{var:.kf}`: for numeric `var` rounds the precision up to `k` decimal points for *floating point type* `f`.

```python
...

# print floating numeric rounds up to 2 decimal points 
template = f'this is a template for var2 = {var2:.2f}'
template = 'this is a template for var2 = {:.2f}'.format(var2)
template = 'this is a template for var2 = %.2f' % (var2)
```

- For time and date, there are different formatting. Add formatting separating from input with `:`

```python
from datetime import datetime

someday = datetime(2020, 1, 1)

sentence = f'this is {someday}'
# print 'this is 2020-01-01 00:00:00'

sentence = f'this is {someday:%B %d, %Y}'
# print 'this is January 01, 2020'
```

- Separate by thousand for large numbers
	- `{:_}`: separate by `_`
	- `{:,}`: separate by `,`

```python
var2 = 10_000_000_000
print(var2)
# 10000000000

var3 = 10000000000

large_number_string = f'{var3:_}'
# '10_000_000_000'

large_number_string = f'{var3:,}'
# '10,000,000,000'
```

- Align position of inputs to form tabular structure by padding with empty spaces
	- `{:>m}`: `m` width of total space including the input, *pad before*
	- `{:<m}`: `m` width of total space including the input, *pad after*
	- `{:m}`: `m` width of total space including the input, *pad after*
	- `{:_>m}`: `m` width of total space including the input, *pad before using `_`*
	- `{:#<m}`: `m` width of total space including the input, *pad after using `#`*

```python
var1 = 'one'

var2 = 'thousand'

aligned_string = f'|{var1:>10}|{var2:>10}|'
# '|       one|  thousand|'

aligned_string = f'|{var1:<10}|{var2:<10}|'
# '|one       |thousand  |'

aligned_string = f'|{var1:10}|{var2:10}|'
# '|one       |thousand  |'

aligned_string = f'|{var1:#>10}|{var2:>10}|'
# '|#######one|##thousand|'
```

- Show an equation
	- using `{ = }` to show both variable/operation description and the calculation result. 

```python
var1 = 10
var2 = 5

equation = f'{var1 + var2 = }'
# 'var1 + var2 = 15'

def f(x):
	return x ** 2

equation = f'{f(var1) = }'
# 'f(var1) = 100'
```



-----------
##  Recommended Notes

- Tutorial
	- [python-tutorial: formatted-output](https://python-course.eu/python-tutorial/formatted-output.php)

- Youtube video
	- [Useful F-String Tricks In Python](https://www.youtube.com/watch?v=EoNOWVYKyo0&t=38s)
	- [Python Quick Tip: F-Strings - How to Use Them and Advanced String Formatting](https://www.youtube.com/watch?v=nghuHvKLhJA&t=9s&ab_channel=CoreySchafer)
	- [F-strings In Python: Everything You Need To Know](https://www.youtube.com/watch?v=Mfmr_Puhtew&ab_channel=ArjanCodes)