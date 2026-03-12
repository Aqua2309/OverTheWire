## Level 3 -> 4

### :trophy: Level Goal

The password for the next level is stored in a hidden file in the inhere directory.

```
ssh bandit3@bandit.labs.overthewire.org -p 2220
password:The discovered in Level 3 

user@user: ls
user@user: cd inhere
user@user:~/inhere$ ls -la
user@user:~/inhere$ cat "...Hiding-From-You"
```
### :mag: Explanation

While this challenge may initially appear more complex than previous levels, it is actually quite straightforward once you understand directory traversal and hidden file attributes.

First of all, we will need to list (ls) the current directory to find the path to the subdirectory "inhere". Once there we will list again the directory to see the files, this time we are using ls -la because I like to see what permissions each file have (-l) and if there are some hidden files (-a).
Furthermore, we see that there is a hidden file that can be read (our goal in this level) so we cat the file and we will get the password.