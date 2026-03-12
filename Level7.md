## Level 6 -> 7

### :trophy: Level Goal

The password for the next level is stored somewhere on the server and has all of the following properties:

* owned by user bandit7
* owned by group bandit6
* 33 bytes in size


```
ssh bandit6@bandit.labs.overthewire.org -p 2220
password:The discovered in Level 6
```

### :mag: Explanation

This level is quite straightforward once you really know how dive into the information.

The level starts as usual, we log into the server we try ls to see subdirectories and... everything looks like a normal directory. We are facing an everyday problem so our approach must be different.
```
user@user:/$ ls
behemoth           formulaone         libx32      opt                 srv
bin                home               lost+found  proc                sys
bin.usr-is-merged  krypton            manpage     root                tmp
boot               lib                maze        run                 usr
dev                lib32              media       sbin                utumno
drifter            lib64              mnt         sbin.usr-is-merged  var
etc                lib.usr-is-merged  narnia      snap                vortex
user@user:/$
```
We definitely are not going to go over all the sub-directories because lets be real, that is not practical at all. A normal approach could be using the "find" command followed by the requested labels these are -user, -group and -size (this one must end in "c" to specify the data type).
```
user@user:/$ find . / -type f -user bandit7 -group bandit6 -size 33c 
find: ‘./proc/tty/driver’: Permission denied
find: ‘./proc/1/task/1/fd’: Permission denied
find: ‘./proc/1/task/1/fdinfo’: Permission denied
find: ‘./proc/1/task/1/ns’: Permission denied
find: ‘./proc/1/fd’: Permission denied
find: ‘./proc/1/map_files’: Permission denied
find: ‘./proc/1/fdinfo’: Permission denied
find: ‘./proc/1/ns’: Permission denied
find: ‘./proc/2/task/2/fd’: Permission denied
find: ‘./proc/2/task/2/fdinfo’: Permission denied
find: ‘./proc/2/task/2/ns’: Permission denied
find: ‘./proc/2/fd’: Permission denied
find: ‘./proc/2/map_files’: Permission denied
find: ‘./proc/2/fdinfo’: Permission denied
find: ‘./proc/2/ns’: Permission denied
find: ‘./proc/31/task/31/fdinfo/6’: No such file or directory
find: ‘./proc/31/fdinfo/5’: No such file or directory
```
We are getting close. Our file must be here but we are getting too much noise so we need to filter that. I'm going to proceed by dumping it to a bin and leaving only the outputs that really matches what I want.
```
user@user:/$ find . / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
./var/lib/dpkg/info/bandit7.password
/var/lib/dpkg/info/bandit7.password
user@user:/$ cat /var/lib/dpkg/info/bandit7.password
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
``` 
To mitigate this "noise" and clarify the output, I utilized I/O redirection (2>/dev/null). This effectively redirects the Standard Error (stderr) stream to the "null device," a special file that discards all data written to it. By suppressing these irrelevant error messages, the actual location of the password was revealed, allowing for a direct retrieval via cat.