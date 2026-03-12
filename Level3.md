## Level 2 -> 3

### :trophy: Level Goal

The password for the next level is stored in a file called --spaces in this filename-- located in the home directory

```
ssh bandit2@bandit.labs.overthewire.org -p 2220
password:The discovered in Level 2 

user@user: ls
user@user: cat ./"spaces in this filename"
```
### :mag: Explanation

First we need to clarify something regarding this type of exercises. 

Naming your directories or your files with "Reserved Characters" is not common. Furthermore, is considered bad praxis because it complicates the workflow.

That being said, the explanation is similar to the last exercise, here the bash interprets blanks spaces as delimiters so each word will be treated as a command, due to that we are going to aim the specific file name via " ".

_*Note: If you are more comfortable with backslashes here they can be use too. The command will look like this: cat ./--spaces\ in\ this\ filename-- . The \ is treated as a separator so the was will give you the same result.*_