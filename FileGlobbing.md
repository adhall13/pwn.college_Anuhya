# Matching with *
code:
```
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
hacker@globbing~matching-with-:~$ echo /c*
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
/challenge
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
hacker@globbing~matching-with-:~$ cd /c*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{IW-znbWF-HEBMo48h9FzdP3-09q.QXxIDO0wiMwEzNzEzW}
```
Explanation: /c* is 3 characters; the shell expands /c* to /challenge (assuming /challenge is the only root entry starting with c). echo /c* shows what will be used before you cd. If the echo prints /c* unchanged, your shell's globbing might be configured not to expand unmatched patterns — but on the challenge system /c* should expand to /challenge.


# Matching with ?
code:
```
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
hacker@globbing~matching-with-:~$ echo /?ha??enge
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
/challenge
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{YFpj4gfqxRl2BR8uPtWXiyLQ4vf.QXyIDO0wiMwEzNzEzW}
```


# Matching with []
code:
```
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ echo Look: file_[bash]
Look: file_a file_b file_h file_s
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[bash]
You got it! Here is your flag!
pwn.college{s0TCOgbLRGZn7Lwflxpz1c33DZr.QXzIDO0wiMwEzNzEzW}
```


# Matching Paths with []
code:
```
hacker@globbing~matching-paths-with-:~$ echo /challenge/files/file_[bash]
/challenge/files/file_a /challenge/files/file_b /challenge/files/file_h /challenge/files/file_s
hacker@globbing~matching-paths-with-:~$ /challenge/run /challe
nge/files/file_[bash]
You got it! Here is your flag!
pwn.college{ErSsiVsGhCbi3Q3jrc5wY4M2PaV.QX0IDO0wiMwEzNzEzW}
```


# Multiple Globs
code:
```
hacker@globbing~multiple-globs:~$ cd /challenge/files
hacker@globbing~multiple-globs:/challenge/files$ echo *p*
happy optimistic pwning splendid uplifting
hacker@globbing~multiple-globs:/challenge/files$ /challenge/run *p*
You got it! Here is your flag!
pwn.college{sVm5KUZzdDzyYaI2xjNk_P0xYwh.0lM3kjNxwiMwEzNzEzW}
```


# Mixing Globs
code:
```
hacker@globbing~mixing-globs:~$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]
Your expansion did not expand to the requested files (challenging, educational, 
pwning). Instead, it expanded to:
[cep]
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{EIqyHyjztCDLuYqzZqC1m0UvDC5.QX1IDO0wiMwEzNzEzW}
```


# Exclusionary Globbing
code:
```
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [^pwn]*
You got it! Here is your flag!
pwn.college{sGdct-pUkZ1tTz94FAR5KXETGgd.QX2IDO0wiMwEzNzEzW}
```


# Tab Completion
code:
```
hacker@globbing~tab-completion:~$ ls /challenge
DESCRIPTION.md  pwncollege​
hacker@globbing~tab-completion:~$ cat /challenge/pwncollege​ 
pwn.college{wTfbp6pxnMppN6NKLITDkpioxmW.0FN0EzNxwiMwEzNzEzW}
```


# Multiple Options for Tab Completion
code:
```
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwncollege-flag
pwn.college{oN_H_KC1kw_ji1IrYElsxakJ6Us.0lN0EzNxwiMwEzNzEzW}
```


# Multiple Options on Command
Type `pwncollege` and press tab to autofill the command, and press enter to get the flag
code:
```
hacker@globbing~tab-completion-on-commands:~$ pwncollege-8310 
Correct! Here is your flag:
pwn.college{omvdNFY-pb7ZUfrcRspEW-EvgQE.0VN0EzNxwiMwEzNzEzW}
```
