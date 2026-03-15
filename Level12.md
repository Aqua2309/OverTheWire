### Level 11 -> 12 

### :trophy: Level Goal
The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

```
ssh bandit11@bandit.labs.overthewire.org -p 2220
password:The discovered in Level 11
```

### :mag: Explanation

The complexity of this level is based on encryption, to be more precise the ROT13 encryption, where the letters change 13 positions in the alphabet
```
bandit11@bandit:~$ cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
The password is 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
```
Lets go over the command and explain each part:

* cat data.txt: We are asking the CLI to open the data.txt file 
* | : A fundamental operator used to chain commands, passing the output of the preceding process as the direct input to the next. 
* tr 'A-Za-z': Invokes the translate utility. The first argument specifies the source range—in this case, the entire uppercase and lowercase Latin alphabet.
* 'N-ZA-Mn-za-m': This is the target mapping set. By starting the range at 'N', we instruct the utility to map 'A' to 'N', 'B' to 'O', and so forth. Once the sequence reaches 'Z', it wraps around to 'A' and continues through 'M'. This ensures a precise 13-character shift across the entire set while maintaining case sensitivity. 