---
tags:
  - code
  - code_snippet
  - git/remove
  - bash/git
keywords: 
topics: 
language: git
date of note: 2024-04-26
---

## Code Snippet Summary

>[!important]
>Remove deleted some sensitive files in Git Repository



## Code

 - [GitHub answered exactly that question as an FAQ](https://help.github.com/articles/remove-sensitive-data "Remove sensitive data - GitHub Help"):

```bash
  git filter-branch --force --index-filter \
  "git rm --cached --ignore-unmatch PATH-TO-YOUR-FILE-WITH-SENSITIVE-DATA" \
  --prune-empty --tag-name-filter cat -- --all
  git push --force --verbose --dry-run
  git push --force
```

>[!quote]
>Keep in mind that once you've pushed this code to a remote repository like GitHub and others have cloned that remote repository, you're now in a situation where you're **rewriting history**. When others try pull down your latest changes after this, they'll get a message indicating that **the changes can't be applied** because it's not a fast-forward.
>
>To fix this, they'll have to either delete their existing repository and re-clone it, or follow the instructions under "RECOVERING FROM UPSTREAM REBASE" in the [git-rebase manpage](http://git-scm.com/docs/git-rebase).
>
>-- Stack Overflow [Remove sensitive files and their commits from Git history](https://stackoverflow.com/questions/872565/remove-sensitive-files-and-their-commits-from-git-history)

- **Tip**: Execute `git rebase --interactive`

### Change before Pushed to Remote Repo

- In the future, if you accidentally commit some changes with sensitive information but you notice **before** pushing to a remote repository, there are some easier fixes. 
- If you *last commit* is the one to *add the sensitive information*, you can simply remove the sensitive information, then run:
  
```bash
git commit -a --amend
```

- That will **amend the previous commit** with *any new changes* you've made, including entire file removals done with a `git rm`. 
- If the changes are further back in history but still **not pushed** to a remote repository, you can do an **interactive rebase**:
  
```bash
git rebase -i origin/master
```

- That *opens an editor* with the commits you've made since your last common ancestor with the remote repository. 
- **Change "pick" to "edit"** on any lines representing a commit with sensitive information, and **save and quit**. Git will walk through the changes, and leave you at a spot where you can:
  
```bash
$EDITOR file-to-fix
git commit -a --amend
git rebase --continue
```

- For each change with sensitive information. Eventually, you'll end up *back on your branch*, and you can safely push the new changes.



-----------
##  Recommended Notes

- [[Revert Previous Commit in Git Repo]]
- [[Untrack Files in Git Repository]]

- Stack Overflow:
	- [Remove sensitive files and their commits from Git history](https://stackoverflow.com/questions/872565/remove-sensitive-files-and-their-commits-from-git-history)
	- [Delete all previous versions of file in git repo [duplicate]](https://stackoverflow.com/questions/26831494/delete-all-previous-versions-of-file-in-git-repo)
	- [Git still showing deleted files after a commit](https://stackoverflow.com/questions/4307728/git-still-showing-deleted-files-after-a-commit)
	- [Remove commit from history](https://stackoverflow.com/questions/30893040/remove-commit-from-history)