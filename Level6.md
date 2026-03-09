## Level 6

### :trophy: Level Goal

The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

* human-readable
* 1033 bytes in size
* not executable

```
ssh bandit5@bandit.labs.overthewire.org -p 2220
password:The discovered in Level 5
```

### :mag: Explanation

As we progress, the challenges require more than simple directory navigation. This time around we have multiple sub-directories and multiple files too.

The approach this time will be different as we are going to try it step by step and then by a single command line. 

First, we are going to assume that the password is behind a non-executable file. This will be easy and the fastest way to get to it in case we are correct.
```
user@user: ls
user@user: cd inhere
user@user:~/inhere$ ls 
user@user~/inhere$ ls -la
total 88
drwxr-x--- 22 root bandit5 4096 Oct 14 09:26 .
drwxr-xr-x  3 root root    4096 Oct 14 09:26 ..
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere00
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere01
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere02
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere03
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere04
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere05
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere06
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere07
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere08
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere09
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere10
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere11
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere12
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere13
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere14
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere15
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere16
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere17
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere18
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere19
```
As we can see there are multiple sub-directories and going one by one will be a tedious and pointless work so the approach will be a little different now.

If the exercise is similar to the last one we can try to filter only the human readable files, with this the amount of information we are going to receive is going to be less.
```
user@user~/inhere$  file */{.,}* | grep "ASCII text" | grep -v ', with very long lines'
maybehere10/.file2:       ASCII text
maybehere15/.file2:       ASCII text
maybehere01/-file2:       ASCII text
maybehere08/spaces file1: ASCII text
maybehere12/-file2:       ASCII text
maybehere15/spaces file2: ASCII text
maybehere18/-file2:       ASCII text
```
we are using "file * / * to print all the files in all the directories and we are adding {.,} to include hidden files too (to be precise, we are including every file except for the ones that start with 1).

Then grep is use to filter the files by the condition that the have to be ASCII text only (human readable).

Lastly, we are assuming that the password can be long but no very long so we are doing another grep (grep -v this time) to exclude that type of files.

We receive less outputs this time around but still we are not sure if the password is behind any of these files so we are going to compliment the last given property: 1033 bytes files.

We are aiming for disk usage so "du" will be our best choice. By typing  "du -b -a | grep 1033" we are going to receive any output that was filtered by disk usage first (du), displayed in bytes (-b) and not only directories will show, files will be outputted too (-a). Furthermore, using "|" and grep 1033 the files will need to fulfill the first requisites explained above an they will need to be exactly 1033 byte max.
```
user@user:~/inhere$  du -b -a | grep 1033
1033	./maybehere07/.file2
user@user:~/inhere$ cat ./maybehere07/.file2
```

In conclusion, our previous assumption was wrong, the password wasn't contain in any of the outputted files as we saw by filtering by byte.


_*Note: For obvious reasons there is a faster way to do this. I only did this step by step because that how I though this problem could be solve. To solve the problem in one command line use: find . -type f -size 1033c ! -executable -exec file '{}' \; | grep ASCII. By doing so we are: finding in the actual directory only files that have a size of 1033 exactly and aren't executable, then we are executing those files and then we are filtering them by ASCII *_