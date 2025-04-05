---
tags:
  - code
  - code_snippet
  - bash/csv
  - bash/wc
keywords: 
topics: 
language: bash
date of note: 2025-01-27
---

## Code Snippet Summary

>[!important]
>Given a csv file, count number of columns


## Code

```bash
awk -F, 'NR==1 {print NF; exit}' file.csv
```

^48d329

- **`-F,`** sets the field separator to a comma.
- **`NR==1`** ensures that only the first line (usually the header) is processed.
- **`print NF`** prints the number of fields (columns).
- **`exit`** stops processing after the first line, which is efficient for large files.





-----------
##  Recommended Notes

- [[Count Number of Lines in a File]]
- [[Use awk to Filter Rows]]
- [[Use awk to Parse CSV]]