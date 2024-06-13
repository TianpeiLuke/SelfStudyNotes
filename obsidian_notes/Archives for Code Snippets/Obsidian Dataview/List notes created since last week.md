---
tags:
  - code
  - code_snippet
  - obsidian/dataview
keywords: 
topics: 
language: obsidian/data_view
date of note: 2024-04-14
---

## Code Snippet Summary

>[!important]
>Create a dataview that list all notes created since last 7 days


## Code


```plain
dataview
TABLE file.ctime AS "Created"
WHERE file.ctime >= date(today) - dur(1 week)

```

- `file.ctime`: a built-in meta field for created time for the `.md` file


-----------
##  Recommended Notes

- Dataview official guide [reference](https://blacksmithgu.github.io/obsidian-dataview/)
- [Dataview in Obsidian: A Beginner’s Guide](https://obsidian.rocks/dataview-in-obsidian-a-beginners-guide/)

- [Basic Inline Queries](https://s-blu.github.io/obsidian_dataview_example_vault/20%20Dataview%20Queries/Basic%20Inline%20Queries/#basic-inline-queries "Permanent link"): Showcase basic syntax of DQL and JS Inline Queries
- [Dataview functions](https://blacksmithgu.github.io/obsidian-dataview/query/functions/) are available in inline queries.

- Obsidian forum 
	- [Specify the sort order in Dataview Query](https://forum.obsidian.md/t/specify-the-sort-order-in-dataview-query/37196)
