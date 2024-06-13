---
tags:
  - code
  - code_snippet
  - bash/git
  - git/config
keywords: 
topics: 
language: git
date of note: 2024-04-27
---

## Code Snippet Summary

>[!important]
>Configure the name and email address to a Git Repository


## Code

```bash
git config --global user.name "Your Name"
git config --global user.email you@example.com
```

- Git writes the Name and Email into the configuration file (`--global` means in the global config file).
- After this, you need to reset the commit information with the command:

```bash
git commit --amend --reset-author
```



>[!info]
> `Git`  detects if you have the following section in your config files:
> 
> ```
> [user]
>     name = \<your name\>
>     email = \<your mail\>
> ```
> 
> - `<project_path>/.git/config` for the project specific config file.
> - `~/.gitconfig` the global config file




-----------
##  Recommended Notes

- Stack Overflow
	- [Git: name and email address configuration](https://stackoverflow.com/questions/10946893/git-name-and-email-address-configuration)
	- [How do I avoid the specification of the username and password at every git push?](https://stackoverflow.com/questions/8588768/how-do-i-avoid-the-specification-of-the-username-and-password-at-every-git-push)
	- [How do I change the URI (URL) for a remote Git repository?](https://stackoverflow.com/questions/2432764/how-do-i-change-the-uri-url-for-a-remote-git-repository)