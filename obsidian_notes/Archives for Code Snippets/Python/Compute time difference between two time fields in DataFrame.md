---
tags:
  - code
  - code_snippet
  - python/dataframe
  - python/time
keywords: 
topics: 
language: 
date of note: 2024-04-04
---

## Code Snippet Summary

>[!important]
>Suppose a dataframe has two time fields `event1_timestamp` and `event2_timestamp`. 
>- Both `event1_timestamp` and `event2_timestamp` are "string" type
>- The date and timestamp is recorded in format `YYYY-MM-DD HH:mm:SS` such as "2021-06-24 08:51:03"
>- The task is to create a new field `timediff_event1_event2` to **compute the time difference** between `event1_timestamp` and `event2_timestamp`


## Code

```python
import pandas as pd

# Convert the timestamp columns to datetime objects
df['event1_timestamp'] = pd.to_datetime(df['event1_timestamp'])
df['event2_timestamp'] = pd.to_datetime(df['event2_timestamp'])

# Calculate the time difference and create a new column
df['time_gap_event1_event2'] = df['event2_timestamp'] - df['event1_timestamp']
```

- `pandas.DataFrame.to_datetime()`: Convert argument to datetime. [reference](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.to_datetime.html#pandas.to_datetime)
	- This function converts a scalar, array-like, [`Series`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Series.html#pandas.Series "pandas.Series") or [`DataFrame`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html#pandas.DataFrame "pandas.DataFrame")/dict-like to a **pandas datetime object**.
	- **`arg`**: The object to convert to a datetime. If a [`DataFrame`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html#pandas.DataFrame "pandas.DataFrame") is provided, the method expects minimally the following columns: `"year"`, `"month"`, `"day"`. The column “year” must be specified in 4-digit format.
	- `dayfirst` : Specify a date parse order if arg is str or is list-like.
	- `yearfirst`
	- `utc`: Control timezone-related parsing, localization and conversion.
	- **`format`**: The `datetime.strftime()` to **parse time**. 
		- See [strftime documentation](https://docs.python.org/3/library/datetime.html#strftime-and-strptime-behavior) for more information on choices, though note that `"%f"` will parse all the way up to nanoseconds.
	- `unit`: default 'ns'. 
	- Returns `datetime.datatime` if scalar. For arrays, *Series*, *DataFrame* return the corresponding type with `datetime64` type object.

### Extension

>[!important]
>We want to specify that the time gap is in seconds

```python
import pandas as pd

# Assuming you have a DataFrame named 'df' with 'event1_timestamp' and 'event2_timestamp' columns

# Convert timestamp strings to datetime objects
df['event1_timestamp'] = pd.to_datetime(df['event1_timestamp'])
df['event2_timestamp'] = pd.to_datetime(df['event2_timestamp'])

# Calculate the time difference in seconds
df['time_gap_event1_event2'] = (df['event2_timestamp'] - df['event1_timestamp']).dt.total_seconds()

# time differece in days
df['time_gap_event1_event2'] = (df['event2_timestamp'] - df['event1_timestamp']).dt.days
```

- We use the `pd.Series.dt.total_seconds()` method on the resulting timedelta object to **convert the time difference into seconds**. This gives us the desired time gap between the two events.
- `Series.dt.total_seconds()`: Return total duration of each element expressed in seconds.  [reference](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Series.dt.total_seconds.html#pandas.Series.dt.total_seconds)
	- This method is available directly on TimedeltaArray, TimedeltaIndex and on Series containing timedelta values **under the `.dt` namespace**.
- `Series.dt.days`: Number of days for each element. [reference](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Series.dt.days.html#pandas-series-dt-days)

>[!important]
>Plot a histogram of the time gap and save it locally
>- Use `bins = [-10, 0, 3, 7, 14, 30, 60, 180, 365, 720]`

```python
import pandas as pd
import matplotlib.pyplot as plt

# Assuming you have a DataFrame named 'df' with the 'time_gap_event1_event2' field

# Create the histogram plot
plt.figure(figsize=(10, 6))
bins = [-10, 0, 3, 7, 14, 30, 60, 180, 365, 720]
plt.hist(df['time_gap_event1_event2'], bins=, edgecolor='black')
plt.xlabel('Time Gap (days)')
plt.ylabel('Frequency')
plt.title('Histogram of Time Gap between order and message arrival date (days)')
plt.xticks(bins, rotation=90, fontsize=10)
plt.grid(True)

# Save the plot to a .png file
plt.savefig('time_gap_histogram.png')

# Display the plot
plt.show()
```

- 



-----------
##  Recommended Notes

- `datetime` package: [reference](https://docs.python.org/3/library/datetime.html)
	- `datetime.strftime()`: Return a string representing the date, controlled by an explicit format string. [reference](https://docs.python.org/3/library/datetime.html#datetime.date.strftime)
	- `strftime()` and `strptime()`: [reference](https://docs.python.org/3/library/datetime.html#strftime-and-strptime-behavior)
		- Format Codes: [reference](https://docs.python.org/3/library/datetime.html#strftime-and-strptime-format-codes) 
- Pandas **DataFrame**: [User Guide](https://pandas.pydata.org/docs/user_guide/dsintro.html#basics-dataframe)
	- `to_datetime`: [reference](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.to_datetime.html#pandas.to_datetime)
	- `to_timedelta`: [reference](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.to_timedelta.html#pandas.to_timedelta)
- Pandas **Series**: [User Guide](https://pandas.pydata.org/pandas-docs/stable/reference/series.html)
	- `to_timestamp`: [reference](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Series.to_timestamp.html#pandas.Series.to_timestamp)
	- `.dt.total_seconds()`: [reference](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Series.dt.total_seconds.html#pandas.Series.dt.total_seconds)
- **Matplotlib**: [reference](https://matplotlib.org/stable/api/index)
	- Stack Overflow: 
		- [X-axis tick labels are too dense when drawing plots](https://stackoverflow.com/questions/54783160/x-axis-tick-labels-are-too-dense-when-drawing-plots)
		- [Rotate axis tick labels](https://stackoverflow.com/questions/10998621/rotate-axis-tick-labels)

- [[Convert and Sort by Year and Week Number in Dataframe]]