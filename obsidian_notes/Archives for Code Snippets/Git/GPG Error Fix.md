---
tags:
  - code
  - code_snippet
  - git/trouble_shooting
keywords: 
topics: 
language: git
date of note: 2024-11-29
---

## Code Snippet Summary

>[!important]
>Fix the error with message
>`W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: https://cli.github.com/packages stable InRelease: The following signatures were invalid: EXPKEYSIG 23F3D4EA75716059 GitHub CLI <opensource+cli@github.com>`
>`W: Failed to fetch https://cli.github.com/packages/dists/stable/InRelease  The following signatures were invalid: EXPKEYSIG 23F3D4EA75716059 GitHub CLI <opensource+cli@github.com>`
>`W: Some index files failed to download. They have been ignored, or old ones used instead.`


## Code

>[!quote]
>This error occurs because the GPG key used to verify the GitHub CLI repository has expired or is no longer valid. To resolve this issue, you need to update the GPG key. Here's how you can do it:
>
>-- ChatGPT

### 1. **Remove the expired key**

Run the following command to delete the expired GPG key from your system:

```bash
sudo apt-key del 23F3D4EA75716059
```

### 2. **Add the updated key**

Get the updated GPG key for the GitHub CLI repository and add it to your system:

```bash
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo gpg --dearmor -o /usr/share/keyrings/githubcli-archive-keyring.gpg
```

### 3. **Update the repository list**

If your `/etc/apt/sources.list.d/github-cli.list` file contains the GitHub CLI repository, ensure it references the correct keyring. Update the file if necessary:

```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null
```


### 4. **Update your package index**

Run the following commands to refresh your system's package list and resolve the issue:

```bash
sudo apt update
```

### 5. **Verify and upgrade**

After the `apt update`, you should no longer see the signature error. You can now install or upgrade GitHub CLI:

```bash
sudo apt install gh
```








-----------
##  Recommended Notes

- Stack Overflow
	- [gpg-error-https-cli-github-com-packages](https://stackoverflow.com/questions/73600286/gpg-error-https-cli-github-com-packages-stable-inrelease-expkeysig-c99b11deb)