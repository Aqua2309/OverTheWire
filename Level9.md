## Level 8 -> 9

### :trophy: Level Goal

The password for the next level is stored in the file data.txt and is the only line of text that occurs only once.The password for the next level is stored in the file data.txt and is the only line of text that occurs only once.

```
ssh bandit8@bandit.labs.overthewire.org -p 2220
password:The discovered in Level 8
```

### :mag: Explanation

uniq is a command that filters input and writes to the output. Specifically, it filters based on identical lines. It has a flag -u, which filters for unique lines (lines that appear only ones). Another interesting functionality is, for example, that it can also count (-c) or only return duplicate lines (-d).

The command is often used with sort. For uniq to filter for unique lines, the lines need to be sorted. sort sorts the lines of a text file. Furthermore, it has flags for sorting in reverse (-r) and sorting numerically (-n).

This being said, to find the line that occurs only once in the file, we first sort the lines and then filter for the unique one.

```
bandit8@bandit:~$ sort data.txt | uniq -u
UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
```
