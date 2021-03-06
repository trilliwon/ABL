---
layout: post
title: "How to find"
date: 2019-04-26 17:00:00 +0900
tag: [Shell]
---

# find

> find -- walk a file hierarchy
> The *find* utility recursively descends the directory tree each path listed, evaluating an expression in terms of each file in the treee.

- `find /Users -name "test.txt"`
- `locate NAME`
- `sudo launchctl load -w /System/Library/LaunchDaemons/com.apple.locate.plist`
- `mdfind NAME`

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

# grep - file pattern seacher

> The grep utility searches any given input files, selecting lines that match one or more patterns.  By default, a pattern matches an input line if the regular expression (RE) in the pattern matches the input line without its trailing newline. An empty expression matches every line. Each input line that matches at least one of the patterns is written to the standard output.

## Examples

```shell
grep 'word' filename
grep 'word' file1 file2 file3
grep 'string1 string2'  filename
cat otherfile | grep 'something'
command | grep 'something'
command option1 | grep 'data'
grep --color 'data' fileName
```

- To search case-insensertive way
    - `grep -i 'word' hello.md
- To search all files in the directory recursively
    - `grep -R "word" .`
- To find all occurrences of the word `patricia' in a file:
    - `grep 'patricia' myfile`
- To find all occurrences of the pattern `.Pp' at the beginning of a line:
    - `grep '^\.Pp' myfile`
- To find all lines in a file which do not contain the words `foo` or `bar`:
    - `grep -v -e 'foo' -e 'bar' myfile`
    - `-v` = `--invert-match`
- To count of word:
    - `grep -c 'word' /path/to/file`
- To search 2 different words
    - `egrep -w 'word1|word2' /path/to/file`
- To search line of the word

```shell
$ grep -n "left" index.html 
28:    <a href="{{ paginator.previous_page_path | prepend: site.baseurl }}" class="left arrow">&#8592;</a>
```
- To list files that contains the word:

```shell
$ grep -l "filter" _posts/computer-vision/*.md
_posts/computer-vision/2017-12-06-computer-vision.md
```

- `egrep '19|20|25' calendar`



> References

- [How to Find a File in Linux Using the Command Line](https://www.lifewire.com/uses-of-linux-command-find-2201100)