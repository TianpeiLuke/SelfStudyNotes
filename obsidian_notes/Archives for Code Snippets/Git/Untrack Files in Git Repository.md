---
tags:
  - code
  - code_snippet
  - bash/git
  - git/ignore
keywords: 
topics: 
language: git
date of note: 2024-04-27
---

## Code Snippet Summary

>[!important]
>Untrack a set of files in git so that they would not be pushed to the remote repository


## Code

### Temporary Untrack Files

```bash
# start ignoring the changes to the file  
git update-index --assume-unchanged path/to/file

# start keeping track again  
git update-index --no-assume-unchanged path/to/file
```


### Delete Files in Remote and Add Files back

```bash
# this will remove the file in remote
git rm -r --cached <file>

# add your files back
git add -u
```

- This command remove `\<file\>` from remote version control, while keeping it in the working repository.


### Untrack Permanently 

- Add paths (with regular expression) or filenames to `.gitignore`



-----------
##  Recommended Notes

- `update-index` [Github Documentation](https://help.github.com/articles/ignoring-files)

- [[Remove sensitive files and commits in Git Repo]]

- Stack Overflow:
	- [Untrack files from git temporarily](https://stackoverflow.com/questions/6964297/untrack-files-from-git-temporarily)
	- [How to stop tracking and ignore changes to a file in Git?](https://stackoverflow.com/questions/936249/how-to-stop-tracking-and-ignore-changes-to-a-file-in-git)
	- [Git still showing deleted files after a commit](https://stackoverflow.com/questions/4307728/git-still-showing-deleted-files-after-a-commit)