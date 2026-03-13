## Level 9 -> Level 10

### :trophy: Level Goal
The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

```
ssh bandit9@bandit.labs.overthewire.org -p 2220
password:The discovered in Level 9
```

### :mag: Explanation

To fulfill this level we have to different approaches. The easy and clean one (with the usage of "strings") and a less aesthetic one ("with "grep" and the flag -a). This being said let's go over them.
On one hand, the CLI counts with "strings" the strings command finds human-readable strings in files. Specifically, it prints sequences of printable characters. Its main use is for non-printable files like hex dumps or executables.
```
bandit9@bandit:~$ ls
data.txt
bandit9@bandit:~$ strings data.txt
Dm|H
d:Bj
pgM,
g%q&N
}}Jae
:AJsC
E!ML
~>#~
+PIqZ
Zf{,
========== the
tWIN
W9`5
UnTZ
[O9xK
6dG"I>
WJC<
UW'$
6cb6:
@;IT
(p.[1
Om5O
	72eW
Y8)s
Y2V:
YF_|
&g2*7
bandit9@bandit:~$ strings data.txt | grep "===" 
========== the
========== password
f\Z'========== is
========== FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
```
As we can see if we only use "string" we surely get the password but we get noise too (all the human-readable text) so we need a filter (grep works fine).

On the other hand, we can use "grep" follow up by the flag -a. This combination is asking the CLI to go over the file and bypass all the noise only printing the human-readable characters.
```
grep -a "===" data.txt
_�Z�
    С���H��v��ޝn<�kX����Bt�y�/
                              X��?�m�x�,����=��E���nq��e
                                                        &�/g>�========== the
���q	�r���3>!�A]����;�L��u<Q� /oa��.�*��O��Y��	ﾂ!�Z��W�y�4$� ��========== password
#��#�AM�M/D���q]L":J������wy����St+�7Ea����|RE�>w�n�;�
                                                      �泬?�@��F,�f\Z'========== is
�ǭ�?�*�9���f3�ߚ�q�w}ɺ��Tc�#y-ey =1�а{��}#A�x}��K
                                                o�8Q��Gap��AD����0��l�Lx2�2;lö���( D!��� O?e�츺R��=���[G�6�D��Vw �����========== FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
```

Is less fancy but the password is outputted too