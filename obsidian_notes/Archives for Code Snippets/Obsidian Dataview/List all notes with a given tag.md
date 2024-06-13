---
tags:
  - code
  - code_snippet
  - obsidian/dataview
keywords: 
topics: 
language: obsidian/data_view
date of note: 2024-04-12
---

## Code Snippet Summary

>[!important]
>Create a dataview that list all notes with a given tag


## Code

### Use `query` 

```plain
query
tag:#tag
```

### Use `dataview`

- Use from `#` tag name

```plain
dataview

list
from #tag
```

####  List notes with *two tags* simultaneously 

```plain
dataview

list
from #tag1 and #tag2
```

#### List note that *do not* have a specific tag

- Use `-` in front of tag for negation.

```plain
dataview

list
from -#tag1
```

#### List notes that *without any tags*I 

```plain
dataview

list
where !file.tags
```

or 

```plain
dataview

list 
from ""
where length(tags) = 0
```

### Use Flatten and Contains

- From a folder name 'My Folder'
- `FLATTEN`
- `contains`

```plain
dataview

LIST WITHOUT ID L.text
FROM "My Folder"
FLATTEN file.lists AS L
WHERE contains(L.tags, "#tag1")
```



-----------
##  Recommended Notes

- Dataview official guide [reference](https://blacksmithgu.github.io/obsidian-dataview/)
- [Dataview in Obsidian: A Beginner’s Guide](https://obsidian.rocks/dataview-in-obsidian-a-beginners-guide/)

- Reddit 
	- [Is there a native way to display a list of all notes tagged with a certain tag, or do I need to download DataView for it?](https://www.reddit.com/r/ObsidianMD/comments/ylglqd/is_there_a_native_way_to_display_a_list_of_all/)
	- [Is there a way to find all the notes without tags?](https://www.reddit.com/r/ObsidianMD/comments/1153gyl/is_there_a_way_to_find_all_the_notes_without_tags/)