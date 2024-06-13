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
>Create **Table view** to show 
>- year, 
>- name, 
>- author, 
>- publication property as well as 
>- incoming links to the notes 
>  
>for papers of a given topic


## Code

```plain
dataview 
TABLE year, name, authors, publication, file.inlinks AS "Related Notes" 
FROM #paper and #programmatic_weak_supervision 

```

- `TABLE` 

#### Build-In Meta fields

Dataview gives you a ton of control with a bunch of _built-in_ metadata for all of your notes.

| Field Name             | Description                                                                                                                                                                     |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `file.name`            | The file name as seen in Obsidians sidebar.                                                                                                                                     |
| `file.folder`          | The path of the folder this file belongs to.                                                                                                                                    |
| `file.path`            | The full file path, including the files name.                                                                                                                                   |
| `file.ext`             | The extension of the file type; generally `md`.                                                                                                                                 |
| `file.link`            | A link to the file.                                                                                                                                                             |
| `file.size`            | The size (in bytes) of the file.                                                                                                                                                |
| `file.ctime` with Time | The date that the file was created.                                                                                                                                             |
| `file.cday`            | The date that the file was created.                                                                                                                                             |
| `file.mtime` with Time | The date that the file was last modified.                                                                                                                                       |
| `file.mday`            | The date that the file was last modified.                                                                                                                                       |
| `file.tags`            | A list of all unique tags in the note. Subtags are broken down by each level, so `#Tag/1/A` will be stored in the list as `[#Tag, #Tag/1, #Tag/1/A]`.                           |
| `file.etags`           | A list of all explicit tags in the note; unlike `file.tags`, does not break subtags down, i.e. `[#Tag/1/A]`                                                                     |
| `file.inlinks`         | A list of all incoming links to this file, meaning all files that contain a link to this file.                                                                                  |
| `file.outlinks`        | A list of all outgoing links from this file, meaning all links the file contains.                                                                                               |
| `file.aliases`         | A list of all aliases for the note as defined via the [YAML frontmatter](https://help.obsidian.md/How+to/Add+aliases+to+note).                                                  |
| `file.tasks`           | A list of all tasks (I.e., `\|[ ] some task`) in this file.                                                                                                                     |
| `file.lists`           | A list of all list elements in the file (including tasks); these elements are effectively tasks and can be rendered in task views.                                              |
| `file.frontmatter`     | Contains the raw values of all frontmatter in form of `key \|value` text values; mainly useful for checking raw frontmatter values or for dynamically listing frontmatter keys. |
| `file.day`             | Only available if the file has a date inside its file name (of form `yyyy-mm-dd` or `yyyymmdd`), or has a `Date` field/inline field.                                            |
| `file.starred`         | if this file has been starred via the Obsidian Core Plugin “Starred Files”.                                                                                                     |



-----------
##  Recommended Notes

- Dataview official guide [reference](https://blacksmithgu.github.io/obsidian-dataview/)
- [Dataview in Obsidian: A Beginner’s Guide](https://obsidian.rocks/dataview-in-obsidian-a-beginners-guide/)