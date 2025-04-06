---
tags:
  - code
  - code_snippet
  - SQL/redshift
keywords: 
topics: 
language: SQL
date of note: 2024-08-29
---

## Code Snippet Summary

>[!important] 
>Filter table with date and time format

## Code

### Use `to_date` clause

```sql
select
    field
from tab a
where a.cond1 = 'xxx'
and a.date >= to_date('20240101','YYYYMMDD')
```

- `to_date` function [reference](https://docs.aws.amazon.com/redshift/latest/dg/r_TO_DATE_function.html) [to_date](https://spark.apache.org/docs/latest/api/sql/index.html#to_date)
	- TO_DATE **converts a date** represented by a character string to a **DATE data type**.
	- `string` to be converted
	- `format` A string literal that defines the format of the input _string_, in terms of its date parts. For a list of valid day, month, and year formats, see [Datetime format strings](https://docs.aws.amazon.com/redshift/latest/dg/r_FORMAT_strings.html).
		- `YYYY` - year in 4-digit format
		- `MM` - Month number
		- `DD` - Day of month as a number (01–31)

#### Datetime Format

see [Datetime format strings](https://docs.aws.amazon.com/redshift/latest/dg/r_FORMAT_strings.html).

| Datepart or timepart                           | Meaning                                                                                                                                                                                                                                                                                                                                                                                   |     |
| ---------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --- |
| BC or B.C., AD or A.D., b.c. or bc, ad or a.d. | Upper and lowercase era indicators                                                                                                                                                                                                                                                                                                                                                        |     |
| CC                                             | Two-digit century number                                                                                                                                                                                                                                                                                                                                                                  |     |
| YYYY, YYY, YY, Y                               | 4-digit, 3-digit, 2-digit, 1-digit year number                                                                                                                                                                                                                                                                                                                                            |     |
| Y,YYY                                          | 4-digit year number with comma                                                                                                                                                                                                                                                                                                                                                            |     |
| IYYY, IYY, IY, I                               | 4-digit, 3-digit, 2-digit, 1-digit International Organization for Standardization (ISO) year number                                                                                                                                                                                                                                                                                       |     |
| Q                                              | Quarter number (1 to 4)                                                                                                                                                                                                                                                                                                                                                                   |     |
| MONTH, Month, month                            | Month name (uppercase, mixed-case, lowercase, blank-padded to 9 characters)                                                                                                                                                                                                                                                                                                               |     |
| MON, Mon, mon                                  | Abbreviated month name (uppercase, mixed-case, lowercase, blank-padded to 3 characters)                                                                                                                                                                                                                                                                                                   |     |
| MM                                             | Month number (01-12)                                                                                                                                                                                                                                                                                                                                                                      |     |
| RM, rm                                         | Month number in Roman numerals (I–XII, with I being January, uppercase or lowercase)                                                                                                                                                                                                                                                                                                      |     |
| W                                              | Week of month (1–5; the first week starts on the first day of the month.)                                                                                                                                                                                                                                                                                                                 |     |
| WW                                             | Week number of year (1–53; the first week starts on the first day of the year.)                                                                                                                                                                                                                                                                                                           |     |
| IW                                             | ISO week number of year (the first Thursday of the new year is in week 1.)                                                                                                                                                                                                                                                                                                                |     |
| DAY, Day, day                                  | Day name (uppercase, mixed-case, lowercase, blank-padded to 9 characters)                                                                                                                                                                                                                                                                                                                 |     |
| DY, Dy, dy                                     | Abbreviated day name (uppercase, mixed-case, lowercase, blank-padded to 3 characters)                                                                                                                                                                                                                                                                                                     |     |
| DDD                                            | Day of year (001–366)                                                                                                                                                                                                                                                                                                                                                                     |     |
| IDDD                                           | Day of ISO 8601 week-numbering year (001-371; day 1 of the year is Monday of the first ISO week)                                                                                                                                                                                                                                                                                          |     |
| DD                                             | Day of month as a number (01–31)                                                                                                                                                                                                                                                                                                                                                          |     |
| D                                              | Day of week (1–7; Sunday is 1) Note<br><br>The D datepart behaves differently from the day of week (DOW) datepart used for the datetime functions DATE_PART and EXTRACT. DOW is based on integers 0–6, where Sunday is 0. For more information, see [Date parts for date or timestamp functions](https://docs.aws.amazon.com/redshift/latest/dg/r_Dateparts_for_datetime_functions.html). |     |
| ID                                             | ISO 8601 day of the week, Monday (1) to Sunday (7)                                                                                                                                                                                                                                                                                                                                        |     |
| J                                              | Julian day (days since January 1, 4712 BC)                                                                                                                                                                                                                                                                                                                                                |     |
| HH24                                           | Hour (24-hour clock, 00–23)                                                                                                                                                                                                                                                                                                                                                               |     |
| HH or HH12                                     | Hour (12-hour clock, 01–12)                                                                                                                                                                                                                                                                                                                                                               |     |
| MI                                             | Minutes (00–59)                                                                                                                                                                                                                                                                                                                                                                           |     |
| SS                                             | Seconds (00–59)                                                                                                                                                                                                                                                                                                                                                                           |     |
| MS                                             | Milliseconds (.000)                                                                                                                                                                                                                                                                                                                                                                       |     |
| US                                             | Microseconds (.000000)                                                                                                                                                                                                                                                                                                                                                                    |     |
| AM or PM, A.M. or P.M., a.m. or p.m., am or pm | Upper and lowercase meridian indicators (for 12-hour clock)                                                                                                                                                                                                                                                                                                                               |     |
| TZ, tz                                         | Upper and lowercase time zone abbreviation; valid for TIMESTAMPTZ only                                                                                                                                                                                                                                                                                                                    |     |
| OF                                             | Offset from UTC; valid for TIMESTAMPTZ only                                                                                                                                                                                                                                                                                                                                               |     |





-----------
##  Recommended Notes

- Amazon Redshift
	- `to_date` function [TO_DATE function](https://docs.aws.amazon.com/redshift/latest/dg/r_TO_DATE_function.html)

- [[Amazon Cradle Date Format]]