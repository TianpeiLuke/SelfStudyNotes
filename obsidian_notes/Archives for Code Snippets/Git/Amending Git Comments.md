---
tags:
  - code
  - code_snippet
  - git/commit
  - bash/git
keywords: 
topics: 
language: git
date of note: 2024-11-17
---

## Code Snippet Summary

>[!important]
>- Add additional comments to *already committed* git
>


## Code

```bash
git commit --amend
```

- will open your editor, allowing you to change the commit message of the most recent commit.


```bash
git commit --amend -m "New commit message"
```

- …however, this can make multi-line commit messages or small corrections more cumbersome to enter.
- Make sure you don't have any working copy changes _staged_ before doing this or they will get committed too. (_Unstaged_ changes will not get committed.)


### Changing the message of a commit that you've already pushed to your remote branch

```bash
git push <remote> <branch> --force
# Or
git push <remote> <branch> -f
```

- If you've already pushed your commit up to your remote branch, then - after amending your commit locally (as described above) - you'll also [need to force push the commit](https://stackoverflow.com/questions/41003071/why-must-i-force-push-after-changing-a-commit-message) with:

>[!warning]
>**force-pushing will overwrite the remote branch with the state of your local one**. If there are commits on the remote branch that you don't have in your local branch, you _will_ lose those commits.

>[!warning]
>**be cautious about amending commits that you have already shared with other people.** Amending commits essentially _rewrites_ them to have *different* [SHA](https://en.wikipedia.org/wiki/SHA-1) IDs, which poses a problem if *other people* have copies of the old commit that you've rewritten. 
>- Anyone who has a copy of the old commit will need to *synchronize their work* with your newly re-written commit, which can sometimes be difficult, so make sure you *coordinate with others* when attempting to rewrite shared commit history, or just avoid rewriting shared commits altogether.




### Perform an interactive rebase

Another option is to use interactive rebase. This allows you to edit any message you want to update even if it's not the latest message.

In order to do a Git squash, follow these steps:

```bash
// n is the number of commits up to the last commit you want to be able to edit
git rebase -i HEAD~n
```

Once you squash your commits - choose the `e/r` for editing the message:

>[!important]
>When you use `git rebase -i HEAD~n` there can be **more** than n commits. Git will "collect" all the commits in the last n commits, and if there was a merge somewhere in between that range you will see all the commits as well, so the outcome will be n + .



-----------
##  Recommended Notes


- [git-commit(1) Manual Page](https://www.kernel.org/pub/software/scm/git/docs/git-commit.html)
- [git-rebase(1) Manual Page](https://www.kernel.org/pub/software/scm/git/docs/git-rebase.html)
- [git-push(1) Manual Page](https://www.kernel.org/pub/software/scm/git/docs/git-push.html)

- Stack Overflow [Amending the most recent commit message](https://stackoverflow.com/questions/179123/how-to-modify-existing-unpushed-commit-messages)