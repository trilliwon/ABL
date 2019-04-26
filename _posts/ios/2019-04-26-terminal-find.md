---
layout: post
title: "How to find"
date: 2019-04-26 17:00:00 +0900
tag: [Shell]
---

# find

> find -- walk a file hierarchy
> The *find* utility recursively descends the directory tree each path listed, evaluating an expression in terms of each file in the treee.


## Examples

- Print out a list of all the files whose names do not end in .c.
    - `find / \! -name "*.c" -print`

- Print out a list of all the files owned by user ``wnj'' that are newer than the file ttt.
    - `find . -newer ttt -user won -print`

- Print out a list of all the files that are either owned by ``wnj'' or that are newer than ttt. 
    - `find / \( -newer ttt -or -user wnj \) -print`

- Print out a list of all the files whose inode change time is more recent than the current time minus one minute.
    - `find / -newerct '1 minute ago' -print`

- Use the echo(1) command to print out a list of all the files.
    - `find / -type f -exec echo {} \;`

- Find files and directories that are at least seven levels deep in the working directory /usr/src.
    - `find /usr/src -name CVS -prune -o -depth +6 -print`

```
find / -name filename
```

The most useful parameter is `-name`

### Find mp3 files

- `find ~ -name *.mp3`

### Find png files

- `find ~ -name *.png`

### Find empty files and folders

`find / -empty`


---

# grep

> References

- [How to Find a File in Linux Using the Command Line](https://www.lifewire.com/uses-of-linux-command-find-2201100)