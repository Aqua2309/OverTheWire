## Level 10 -> 11

### :trophy: Level Goal
The password for the next level is stored in the file data.txt, which contains base64 encoded data

```
ssh bandit10@bandit.labs.overthewire.org -p 2220
password:The discovered in Level 10
```

### :mag: Explanation

To successfully complete this level, we can adopt several methodologies, each of which will be explored in detail. The most straightforward approach involves utilizing the base64 utility equipped with the -d (decode) flag. This effectively reverses the encoding process to reveal the cleartext password.
```
bandit10@bandit:~$ base64 -d data.txt
The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```

### :bulb: Alternative Methodologies

As I mention before we have two other possible solutions in order to clear this level:

### :muscle: Robust Approach
In professional environments, openssl is often used for anything involving encoding, certificates, or encryption. It is more robust than the standard base64 utility.
```
bandit10@bandit:~$ openssl enc -base64 -d -in data.txt
```
* enc: Stands for encoding.

* base64: Specifies the encoding type.

* d: The flag for decoding.

* in: Specifies the input file.


### :snake: Python Approach

Since Linux servers almost always have Python installed, you can use a "one-liner" to decode the file. This is useful if you are working on a system that (rarely) lacks the base64 binary.
```
bandit10@bandit:~$ python3 -m base64 -d data.txt
```