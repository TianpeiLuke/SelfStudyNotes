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
> - Initially, a dataview results yields the pages you receive from your `FROM` and `WHERE` arguments as results - *one "row", one result item, per note*. When a `GROUP BY` is applied to a Query, you **bundle up** all pages after the **field you're grouping by**. This has two implications:  
> 	- First, after a `GROUP BY`, you have as many results as the field you grouped by has values.  
> 	- Secondly, the result pages are not your "first level" anymore, but the group is. When listing out a grouped query, you will not receive the files anymore, but the groups.


## Code


```plain
LIST
FROM "10 Example Data/books"
GROUP BY author
```

>[!info]
>A grouped result list is made up of result items that look like this:  
>- `Key`: Value of the field you used in GROUP BY  
>- `rows`: All pages that match `Key`  
>


>[!example]
>Before grouping, every note was a result item and *file.link* was the `Key`. After grouping, your file informations are *bundled up* under the group value as key under the field `rows`. That means you need to use `rows` as a prefix when listing informations.
> 
> ```plain
> TABLE rows.file.link
> FROM "10 Example Data/books"
> GROUP BY author
> 
> ```


### Deduplicate multiple matched groups

- If a page matches multiple groups, dataview will *duplicate the page* for you to put it in every matching group. Therefor, pages can show up multiple times in a grouped result list.

```plain
TABLE rows.file.link
FROM "10 Example Data/books"
FLATTEN genres
GROUP BY genres
```

- Note: In order to get decent groups, we need to `FLATTEN` the multi value field `genres` first. Read more about that in [Example FLATTEN Queries#Group by a flattened field](https://s-blu.github.io/obsidian_dataview_example_vault/20%20Dataview%20Queries/Example%20FLATTEN%20Queries/#group-by-a-flattened-field)

### Use a Calculation as a group

```plain
LIST rows.file.link
FROM "10 Example Data/assignments"
GROUP BY choice(due < date(today), "Overdue", "Still has time")
```

- In addition, you can name this calculation to reference it further in your query.

```plain
TABLE WITHOUT ID progress + "%" AS "% read", rows.file.link
FROM "10 Example Data/books"
GROUP BY round((pagesRead/totalPages) * 100) as progress
WHERE progress > 50 AND progress < 100

```

### Group by literals to trim down your result to exactly one result

> [!info]
> - Beside calculations and fields, you can use a [literal](https://blacksmithgu.github.io/obsidian-dataview/query/literals/) - a fixed value - as a group. This will always result into **one group** and can be useful in certain scenarios, i.e. if you want to calculate a sum or average of your data.
> - The literal itself is used as the group name, but doesn't matter otherwise. You can use it to declare a senseful prefix or omit it completely by using `WITHOUT ID`.

```plain
LIST length(rows) 
FROM "10 Example Data/books"
GROUP BY "Total Books in Obsidian"
```


-----------
##  Recommended Notes

- `GROUP BY` [Documentation](https://blacksmithgu.github.io/obsidian-dataview/query/literals/)
- Example GROUP BY Queries [link](https://s-blu.github.io/obsidian_dataview_example_vault/20%20Dataview%20Queries/Example%20GROUP%20BY%20Queries/)