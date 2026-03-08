## Level 5

### :trophy: Level Goal

The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.
```
ssh bandit4@bandit.labs.overthewire.org -p 2220
password:The discovered in Level 4

user@user: ls
user@user: cd inhere
user@user:~/inhere$ ls 
user@user:~/inhere$ file ./*
user@user:~/inhere$ cat ./-file07
```
### :mag: Explanation

As we progress, the challenges require more than simple directory navigation. This level necessitates distinguishing a single human-readable file from a collection of binary or data files stored within the inhere subdirectory.

To achieve this, we utilize the file command combined with a wildcard (file ./*). The file utility is essential because it examines the file's header to determine its actual content type, regardless of the filename. We are specifically looking for a file identified as ASCII text, which is a standard character encoding for representing text in computers. Once the ASCII file is isolated among the binary noise, we can simply cat its contents to retrieve the password.