## Level 2

### :trophy: Level Goal

The password for the next level is stored in a file called - located in the home directory.

```
ssh bandit1@bandit.labs.overthewire.org -p 2220
password:The discovered in Level 1 

user@user: ls
user@user: cat ./-
```
### :mag: Explanation

This is the first tricky level. At first you would try to cat - on the file or even nano to get access to edit it. Unfortunately, this won't work because "-" is part of a group of "Special Characters", this will result in a bash failure. 

To circumvent this we are going to aim for the relative path to avoid the bash failure (./-). By doing so, we are telling the bash that "-" is not a reserved character and what we want is to gain access to the file.