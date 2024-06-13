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
>Show all items inside **section** "Research"


## Code

```plain
dataview

TABLE L.text AS "My lists"
FROM "Folder Name"
FLATTEN file.lists AS L
WHERE meta(L.section).subpath = "Research"
```

### Group By

```plain
dataview

TABLE rows.L.text AS "My lists"
FROM "Folder Name"
FLATTEN file.lists AS L
WHERE meta(L.section).subpath = "Research"
GROUP BY file.link
```

### Flatten or Filter

```plain
dataview

TABLE WITHOUT ID "<nobr>" + file.link + "</nobr>" AS Page, Research
FROM "Folder Name"
FLATTEN list(filter(file.lists, (x) => meta(x.section).subpath = "Research").text) as Research
WHERE Research
```

### Using flatten to make multiple columns based on different headings

```plain
dataview

TABLE WITHOUT ID "<nobr>" + file.link + "</nobr>" AS Page, Research, Topics
FROM "Folder Name"
FLATTEN list(filter(file.lists, (x) => meta(x.section).subpath = "Research").text) as Research
FLATTEN list(filter(file.lists, (x) => meta(x.section).subpath = "Topics").text) as Topics
WHERE Research OR Topics
```


-----------
##  Recommended Notes

- [Obsidian Example Vault for Dataview Queries](https://s-blu.github.io/obsidian_dataview_example_vault/)
- [Show all list items under a specific heading](https://s-blu.github.io/obsidian_dataview_example_vault/20%20Dataview%20Queries/Show%20all%20list%20items%20under%20a%20specific%20heading/#show-all-list-items-under-a-specific-heading "Permanent link")
- Obsidian Forum
	- [Collecting text from multiple notes under the same heading](https://forum.obsidian.md/t/collecting-text-from-multiple-notes-under-the-same-heading/46915)