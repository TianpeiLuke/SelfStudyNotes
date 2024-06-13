---
tags:
  - code
  - code_snippet
  - python/dataframe
keywords: 
topics: 
language: python
date of note: 2024-04-09
---

## Code Snippet Summary

>[!important]
>Assume that `pandas.DataFrame` has field `id`, and field `input1`, `input2`, .... 
>- Define a function `input_transform` that takes field `input1`, `input2` as input and make transformation and output one value.
>- We want to
>	- **group by** `id`, and 
>	- for each group, **apply function** `input_transform` and output one value. 
>	- Save this value to a **new field** name `output`

## Code

```python
import pandas as pd

def input_transform(df, input1, input2, ...):
	"""
	input df: a dataframe for the group
	      input1, input2 ...: the input field name of df
	output:
		a single value 
	"""
	output = ...
	return output

df_by_id = df.groupby('id').apply(input_transform, input1, input2, ...).reset_index(name = "output")
```




>[!example]
>- `df` has field `MESSAGE_BODY_PROCESSED`, and `SENDER_ROLE`, `ARRIVAL_DATE`
>- Group by thread, and concatenate a thread of messages into one dialogue with the following templates for each message
> ```python
> "{time} [{role}]: {message}\n"
> ```

```python
fields = {
    'role': 'SENDER_ROLE',
    'time': 'ARRIVAL_DATE',
    'message':  'MESSAGE_BODY_PROCESSED'
}

def thread_dialogoue_concat(df, fields):
    out = ""
    roles = df[fields['role']].tolist()
    times = df[fields['time']].tolist()
    messages = df[fields['message']].tolist()
    temp = []
    for (role, time, message) in zip(roles, times, messages):
        temp.append(f'''{time} [{role}]: {message}''')
    
    out = '\n'.join(temp)
    return out

df_by_thread = df.groupby(['THREAD_ID']).apply(thread_dialogoue_concat, fields).reset_index(name="dialogoue")
```



-----------
##  Recommended Notes

- Stack Overflow:
	- [How to apply a function to two columns of Pandas dataframe](https://stackoverflow.com/questions/13331698/how-to-apply-a-function-to-two-columns-of-pandas-dataframe)