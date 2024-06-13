---
tags:
  - code
  - code_snippet
  - linux/truncate
keywords: 
topics: 
language: linux
date of note: 2024-04-04
---

## Code Snippet Summary

>[!important]
>- Truncate the system log file `/var/log/syslog.1` to avoid it taking too much spaces
>- Remove oldest archived journal fiels


## Code


```bash
sudo truncate -s 0 /var/log/syslog.1
```

- **`truncate`**:  [reference](https://man7.org/linux/man-pages/man1/truncate.1.html)
	- `truncate OPTION... FILE...` 
		- Shrink or extend the size of each FILE to the specified size
		- A FILE argument that does not exist is created.
		- If a FILE is larger than the specified size, the extra data is lost.  If a FILE is shorter, it is extended and the sparse extended part (hole) reads as zero bytes.
		- Mandatory arguments to long options are mandatory for short options too.
	- **`-s`**, `--size=_SIZE_`:  set or adjust the file size by *SIZE* bytes


>[!info]
>The following command `journalctl` remove the oldest archived journal files until the disk fall under 500M

```bash
sudo journalctl --vacuum-size=500M
```

- `journalctl` [manual reference](https://man.archlinux.org/man/journalctl.1.en)
	- **`--vacuum-size=`**, **`--vacuum-time=`**, **`--vacuum-files=`**: 
		- **`--vacuum-size=`**:  **removes** the *oldest archived journal files* until the disk space they use falls *below the specified size*. Accepts the usual "K", "M", "G" and "T" suffixes (to the base of 1024).


-----------
##  Recommended Notes

- `truncate`: [reference](https://man7.org/linux/man-pages/man1/truncate.1.html)
- `journalctl` [manual reference](https://man.archlinux.org/man/journalctl.1.en)
- Blog: [How To Use journalctl to View and Manipulate Systemd Logs](https://docs.rackspace.com/docs/how-to-use-journalctl-to-view-and-manipulate-systemd-logs)