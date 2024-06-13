---
tags:
  - code
  - code_snippet
  - bash/git
  - git/push
keywords: 
topics: 
language: git
date of note: 2024-04-27
---

## Code Snippet Summary

>[!important]
>- Add files to remote repository
>- Push committed changes to repository


## Code

### Git Remote Add

```bash
git remote add origin <url_of_remote repository>
```

 - Git is a distributed version control system. Most operations are done locally. 
 - To communicate with the outside world, Git uses what are called **"remotes"**. 
 - These are **repositories** other than the one on your local disk which you can **push** your changes into (so that other people can see them) or **pull** from (so that you can get others changes). 
 - The command `git remote add origin git@github.com:home_folder/XXX.git` creates **a new remote called `origin`** located at `git@github.com:home_folder/XXX.git`. 
 - Once you do this, in your push commands, you can push to **origin** instead of typing out *the whole URL*.

### Git Push

```bash
 git push origin master
```

- This is a command that says "push the commits in the *local branch* named **master** to the *remote* named **origin**". 
- Once this is executed, all the stuff that you last synchronised with _origin_ will be sent to the remote repository and other people will be able to see them there.`

>[!info]
>- Now about transports (i.e., what `git://`) means. 
>- **Remote repository URLs** can be of many types (`file://`, `https://`, etc.). Git simply relies on the authentication mechanism provided by the transport to take care of permissions and stuff. 
>- This means that for `file://` URLs, it will be *Unix file permissions*, etc. 
>- The `git://` scheme is *asking Git to use* **its own internal transport protocol**, which is optimised for sending Git change-sets around. 
>- As for the exact URL, it's the way it is because of *the way GitHub has set up its Git server*.

```bash
git remote add origin git@github.com:home_folder/XXX.git
git push origin master
```

-  The command above is the general one. 
- It's possible to tell Git something like "the branch called **master** over here is *local mirror* of the branch called _foo_ on the remote called _bar_". 
- In Git speak, this means that _master_ _**tracks**_ _bar/foo_. 
- When you clone for *the first time*, you will get a branch called _master_ and a remote called _origin_ (where you cloned from) with *the local master set to track the master on origin*.
- Once this is set up, you can simply say `git push` and it'll do it. 
- The longer command is available in case you need it (e.g., `git push` might push to the official public repository and `git push review master` can be used to push to a separate remote which your team uses to review code). 
- You can set your branch to be a tracking branch using the `--set-upstream` option of the `git branch` command.



-----------
##  Recommended Notes

- Stack Overflow:
	- [What is "git remote add ..." and "git push origin master"?](https://stackoverflow.com/questions/5617211/what-is-git-remote-add-and-git-push-origin-master)