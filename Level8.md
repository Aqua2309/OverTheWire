## Level 8

### :trophy: Level Goal

The password for the next level is stored in the file data.txt next to the word millionth

```
ssh bandit7@bandit.labs.overthewire.org -p 2220
password:The discovered in Level 7
```

### :mag: Explanation

If we compare this level with the previous one we will see that this one is really a walk in the park. First things first a brief explanation of the simplicity of the level. They are telling us that the password is next to "millionth" and stored inside a .txt. Furthermore they suggest the usage of "grep" so we only follow the lead.
```
user@usert:~$ grep "millionth" data.txt
millionth	dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```

*_Note: If yoy try to use "cat" directly in data.txt you'll be force to kill the command because the file is huge (the displayed number means roughly 4MG) and you could compromise the integrity of your computer_*
```
bandit7@bandit:~$ du -b data.txt 
4184396 data.txt
```
