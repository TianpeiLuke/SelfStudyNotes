---
tags:
  - code
  - code_snippet
  - git/rebase
keywords: 
topics: 
language: git
date of note: 2025-04-30
---

## Code Snippet Summary

>[!important]


## Code

```bash
# interactively edit the last N commits
git rebase -i HEAD~N
# mark commits with "edit", then:
git commit --amend --author="yourname <you@email.com>"
git rebase --continue

git push --force-with-lease origin master
```


### Quick checklist

|Step|Command / Location|
|---|---|
|See current author on last commit|`git log -1 --format='%an <%ae>'`|
|Change identity for this repo|`git config user.name …` / `git config user.email …`|
|Verify e-mail on GitHub|Web UI → **Settings › Emails**|
|Rewrite past commits (optional)|`git rebase -i` + `git commit --amend --author=…`|





-----------
##  Recommended Notes

- [[Configure Email and Name for Git Repository]]
- [[Revert Previous Commit in Git Repo]]
