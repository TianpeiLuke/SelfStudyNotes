---
tags:
  - code
  - code_snippet
  - python/dataframe
  - json
keywords: 
topics: 
language: python
date of note: 2024-04-01
---

## Code Snippet Summary

>[!important]
>The tasks for this code snippet:
>- Given a numpy array, such as `[0.1, 0.5, 0.3]`, transform it into a **JSON string** like 
>  ```json
>  {
> 	 "predictions": [
> 		 {"legacy-score": 0.1}, 
> 		 {"legacy-score": 0.5}, 
> 		 {"legacy-score": 0.3}
> 		 ]
>  }
>  ```
>- Serialize the JSON string into a stream
>- Generalize the above to multiple output fields such as 
> ```json
> {  
>       "predictions": [{  
>             "custom-score": 131,  
>             "legacy-score": 131,  
>             "calibrated-score": 0.9012,  
>             "score-percentile": 0.9901,  
>             "custom-output-label": "my-label"  
>       }]  
> }
> ```


## Code

```python
import numpy as np
import pandas as pd
import json
from io import StringIO

custom_score = np.array([...])
legacy_score = np.array([...])
calibrated_score = np.array([...])
score_percentile = np.array([...])
custom_output_label = [...]

# convert it into Panda DataFrame so that it is easier to convert a table of multiple columns into a records

df = pd.DataFrame({"custom-score": custom_score,
				   "legacy-score": legacy_score,
				   "calibrated-score": calibrated_score,
				   "score-percentile": score_percentile,
				   "custom-output-label": custom_output_label
				  })

# output DataFrame to json format; the orient = ‘records’ output list like [{column -> value}, … , {column -> value}]
records_json = df.to_json(orient='records')

# load the JSON string back into dict format 
records_dict = json.loads(records_json)

# inject dict into predefined output dict format
prediction_output = {"predictions": records_dict}

# output dict into JSON string
prediction_output_json = json.dumps(prediction_output)

# write the string into stream
out = StringIO()
out.write(prediction_output_json)
```

- `pandas.DataFrame`: 
	- **`to_json()`**: Convert the object to a JSON string. [reference](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.to_json.html#pandas-dataframe-to-json)
		- **`path_or_buf`**: 
			- *String*, 
			- *path object* (implementing os.PathLike[str]), or 
			- *file-like object* implementing a write() function.
			- If None, the result is **returned as a string**.
		- **`orient`**: Indication of expected JSON string format.
			- default is `‘columns’`
			- allowed values are: {`‘split’,` `‘records’`, `‘index’`, `‘columns’`, `‘values’`, `‘table’`}.
			- The format of the **JSON string**:
				- `‘split’` : *dict* like `{‘index’ -> [index], ‘columns’ -> [columns], ‘data’ -> [values]}`
				- **`‘records’`** : *list* like `[{column -> value}, … , {column -> value}]`
				- `‘index’` : *dict* like `{index -> {column -> value}}`
				- **`‘columns’`** : *dict* like `{column -> {index -> value}}`
				- **`‘values’`** : just the *values array*
				- `‘table’` : *dict* like `{‘schema’: {schema}, ‘data’: {data}}`
- `io.StringIO` [reference](https://docs.python.org/3/library/io.html#io.StringIO)
	- A text stream using an **in-memory text buffer**. It inherits from [`TextIOBase`](https://docs.python.org/3/library/io.html#io.TextIOBase "io.TextIOBase").
	- If newline translation is enabled, newlines will be encoded as if by [`write()`](https://docs.python.org/3/library/io.html#io.TextIOBase.write "io.TextIOBase.write"). The stream is positioned at the start of the buffer which emulates opening an existing file in a `w+` mode, making it ready for an immediate write from the beginning or for a write that would overwrite the initial value.
	- `getvalue()`: Return a [`str`](https://docs.python.org/3/library/stdtypes.html#str "str") containing the entire contents of the buffer. Newlines are decoded as if by [`read()`](https://docs.python.org/3/library/io.html#io.TextIOBase.read "io.TextIOBase.read"), although the stream position is not changed.
- `json`: [reference](https://docs.python.org/3/library/json.html)
	- `json.dump()`: [reference](https://docs.python.org/3/library/json.html#json.dump)
	- `json.dumps()`: **Serialize** _obj_ to a JSON formatted [`str`](https://docs.python.org/3/library/stdtypes.html#str "str") using this [conversion table](https://docs.python.org/3/library/json.html#py-to-json-table). The arguments have the same meaning as in [`dump()`](https://docs.python.org/3/library/json.html#json.dump "json.dump"). [reference](https://docs.python.org/3/library/json.html#json.dumps)
	- `json.load()`: [reference](https://docs.python.org/3/library/json.html#json.load)
	- `json.loads()`: **Deserialize** _s_ (a [`str`](https://docs.python.org/3/library/stdtypes.html#str "str"), [`bytes`](https://docs.python.org/3/library/stdtypes.html#bytes "bytes") or [`bytearray`](https://docs.python.org/3/library/stdtypes.html#bytearray "bytearray") instance containing a JSON document) to a Python object using this [conversion table](https://docs.python.org/3/library/json.html#json-to-py-table). [reference](https://docs.python.org/3/library/json.html#json.loads)
-----------
##  Recommended Notes

- `io` package [reference](https://docs.python.org/3/library/io.html)
	- `io.StringIO` [reference](https://docs.python.org/3/library/io.html#io.StringIO)
- `pandas` package [reference](https://pandas.pydata.org/pandas-docs/stable/reference/index.html)
	- `pandas.Series`: [reference](https://pandas.pydata.org/pandas-docs/stable/reference/series.html)
	- `pandas.DataFrame`: [reference](https://pandas.pydata.org/pandas-docs/stable/reference/frame.html)
- `json` package [reference](https://docs.python.org/3/library/json.html)
	- `json.dump()`: [reference](https://docs.python.org/3/library/json.html#json.dump)
	- `json.load()`: [reference](https://docs.python.org/3/library/json.html#json.load)
	- `json.loads()`: [reference](https://docs.python.org/3/library/json.html#json.loads)
	- `json.dumps()`: [reference](https://docs.python.org/3/library/json.html#json.dumps)