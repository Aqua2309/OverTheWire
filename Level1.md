## Level 1

### :trophy: Level Goal

The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

```
ssh bandit0@bandit.labs.overthewire.org -p 2220
password:bandit0

user@user: ls
user@user: cat readme
```
### :mag: Explanation

The first level is the easiest one, we only have to list the content of the personal directory (with ls). This will lead us to the readme file needed to pass to level 2. Once located we simple use cat to reed the file and find the password.

_*Note: Due to the fact that we are dealing with files we can use nano instead of cat to read the file (with this command we can overwrite the file so be careful)*_

_*Note 2: This command is quite handy. We are going to use * (also known as a wildcard) to see the files (ths command is going to be used in future level too because it tells the type of date the files are based on). The command is find (or file if you wanna know the data type) ./* *_