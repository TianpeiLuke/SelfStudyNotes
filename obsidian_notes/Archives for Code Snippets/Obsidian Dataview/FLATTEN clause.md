---
tags:
  - code
  - code_snippet
  - obsidian/dataview
keywords: 
topics: 
language: obsidian/data_view
date of note: 2024-04-15
---

## Code Snippet Summary

>[!important]
> - `FLATTEN` is the opposite of `GROUP BY`. Instead of putting multiple notes into one row, it (potentionally) **splits up** one note into **multiple rows**. If your result contains seven notes and you use `FLATTEN` on a **multi value field**, you'll get `7 * sum of values in flattened field` results.
> - `FLATTEN` is a data command
> - `FLATTEN` needs to be used in combination with a [Query Type](https://s-blu.github.io/obsidian_dataview_example_vault/30%20Dataview%20Resources/33%20Use%20Cases/Learn%20the%20Basics/#understanding-query-types). You can use `FLATTEN` multiple times.


## Code

- **Query without FLATTEN**

```plain
TABLE genres
FROM "10 Example Data/books"
```

- **Query with FLATTEN**

```plain
TABLE genres
FROM "10 Example Data/books"
FLATTEN genres

```


### FLATTEN multiple fields

```plain
TABLE genres, booktopics
FROM "10 Example Data/books"
FLATTEN genres
FLATTEN booktopics
```

### Group by a flattened field

>[!important]
>A popular use case for `FLATTEN` is to use a **multi value field for grouping**. Without flattening the multi value field first, the result is somewhat unexpected.

- Without FLATTEN

```plain
TABLE rows.file.link
FROM "10 Example Data/books"
GROUP BY genres
```

- Grouping AFTER FLATTEN

```plain
TABLE rows.file.link
FROM "10 Example Data/books"
FLATTEN genres
GROUP BY genres
```

>[!important]
>- Please mind that the **order is important** - a flattened field is only available _after_ you wrote the `FLATTEN` command. 
>- **One big exception**: The Query Type command is always **the last** command to be executed - despite standing at the very top! That means **all flattened fields are available as fields for your Query Type**.

>[!example]
>If you **first group, then FLATTEN, you won't get the desired result!**
> ```plain
> TABLE rows.file.link
> FROM "10 Example Data/books"
> GROUP BY genres
> FLATTEN genres
> ```






-----------
##  Recommended Notes

- `FLATTEN` [Documentation](https://blacksmithgu.github.io/obsidian-dataview/query/queries/#flatten)
- Example FLATTEN Queries [link](https://s-blu.github.io/obsidian_dataview_example_vault/20%20Dataview%20Queries/Example%20FLATTEN%20Queries/#example-flatten-queries "Permanent link")