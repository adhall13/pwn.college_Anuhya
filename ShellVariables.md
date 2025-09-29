# Printing Variables
code:
```
hacker@variables~printing-variables:~$ echo "$FLAG"
pwn.college{88pvETaZUhs75lwPTchr7TFAxBs.QX3UTN0wiMwEzNzEzW}
```


# Setting Variables
code:
```
hacker@variables~setting-variables:~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{w3i3kK9Oqc3OgEttaH_PZCECzUh.QX5UTN0wiMwEzNzEzW}
```


# Multi-word Variables
code:
```
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{gvC-2y5JgwgVN2etELt_AEKsByw.QXwYTN0wiMwEzNzEzW}
```


# Exporting Variables
code:
```
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ export PWN=COLLEGE
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ /challenge/run
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great 
job! Here is your flag:
pwn.college{8J7XZJtjwS7RPV7YpTmLyjXgYZh.QXyYTN0wiMwEzNzEzW}
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
```


# Printing Exporting Variables
code:
```
hacker@variables~printing-exported-variables:~$ printenv FLAG
pwn.college{klfjOTv0X1_7q3yvFagwwdr45DI.QX4UTN0wiMwEzNzEzW}
```


# Sorting Command Output
code:
```
hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out 
and submit it!
hacker@variables~storing-command-output:~$ echo "$PWN"
pwn.college{8nbc38e93hhsqz02p07QgUm7w7a.QX1cDN1wiMwEzNzEzW}
```


# Reading Input
code:
```
hacker@variables~reading-input:~$ read -p "INPUT :" PWN
INPUT :COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{A0ygtfH97tGvLtMKhgO6ltkfGVe.QX4cTN0wiMwEzNzEzW}
```


# Reading Files
code:
```
hacker@variables~reading-files:~$ read PWN < /challenge/read_me
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{kd_v4Ve8zoWvSm954wSlwsEJkSn.QXwIDO0wiMwEzNzEzW}
```
