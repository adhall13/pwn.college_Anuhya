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

```


# Exclusionary Globbing
code:
```

```
