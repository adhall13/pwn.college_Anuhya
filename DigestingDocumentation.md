# Learning From Documentation
code:
```
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{U0yhomrUaflY4TjCjxlJOeNtybd.QX0ITO0wiMwEzNzEzW}
```


# Learning Complex Usage
code:
```
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /challenge/DESCRIPTION.md
Correct argument! Here is the /challenge/DESCRIPTION.md file:
While using most commands is straightforward, the usage of some commands can get quite complex.
For example, the arguments to commands like `sed` and `awk`, which we're definitely not getting into right now, are entire programs in an esoteric programming language!
Somewhere on the spectrum between `cd` and `awk` are commands that take arguments to their arguments...

This sounds crazy, but you've already encountered this with the `find` level in [Basic Commands](/linux-luminarium/commands).
`find` has a `-name` argument, and the `-name` argument itself takes an argument specifying the name to search for.
Many other commands are analogous.

Here is this level's documentation for `/challenge/challenge`:

> Welcome to the documentation for `/challenge/challenge`! This program allows you to print arbitrary files to the terminal, when given the `--printfile` argument. The argument to the `--printfile` argument is the path of the flag to read. For example, `/challenge/challenge --printfile /challenge/DESCRIPTION.md` will print out the description of the level!

Given that documentation, go get the flag!
hacker@man~learning-complex-usage:~$ ls -la
total 20
drwxr-xr-x 1 hacker hacker   74 Sep 29 08:39 .
drwxr-xr-x 1 root   root   4096 Sep 26 17:24 ..
-rw------- 1 hacker hacker 5787 Sep 29 09:11 .bash_history
drwxr-xr-x 1 hacker hacker    0 Sep 22 18:21 .config
-rw-r--r-- 1 root   hacker   60 Sep 27 04:26 f
lrwxrwxrwx 1 hacker hacker    5 Sep 29 08:39 not-the-flag -> /flag
drwxr-xr-x 1 hacker hacker    0 Sep 24 21:11 test
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:
pwn.college{0Uwk_g32UCws9_ULpXBCqGAeh6B.QX1ITO0wiMwEzNzEzW}
```

note:
ls -al
=> ls: The base command, which lists the contents of a directory.
-l (long format): This option displays file and directory information in a table with seven columns of detailed attributes.
-a (all): This option includes hidden files in the output. Hidden files and directories have names that begin with a dot (.)


# Reading Manuals
code:
```
hacker@man~reading-manuals:~$ man challenge
hacker@man~reading-manuals:~$ /challenge/challenge --kkvbux 364
Correct usage! Your flag: pwn.college{kkvT3GUbux6GQ44fCJeUUPdrq3m.QX0EDO0wiMwEzNzEzW}
```


# Searching Manuals
code:
```
hacker@man~searching-manuals:~$ man challenge
hacker@man~searching-manuals:~$ /challenge/challenge --xi
Initializing...
Correct usage! Your flag: pwn.college{IBo6p-5IgB4xt-xjQp2EBH5ar3u.QX1EDO0wiMwEzNzEzW}
```


# Searching For Manuals
code:
```
hacker@man~searching-for-manuals:~$ man man
hacker@man~searching-for-manuals:~$ man -k challenge
camioqiuxe (1)       - print the flag!
hacker@man~searching-for-manuals:~$ man camioqiuxe
hacker@man~searching-for-manuals:~$ /challenge/challenge --camioq 263
Correct usage! Your flag: pwn.college{c2SBa63m-3iWoqi-BuxOe3w0d9o.QX2EDO0wiMwEzNzEzW}
```


# Helpful Programs
code:
```
hacker@man~helpful-programs:~$ /challenge/challenge --help
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give you the flag
hacker@man~helpful-programs:~$ /challenge/challenge --p
The secret value is: 117
hacker@man~helpful-programs:~$ /challenge/challenge --g 117
Correct usage! Your flag: pwn.college{kVIxlkIJ1KGS1dwHbhDq7tF0sls.QX3IDO0wiMwEzNzEzW}
```


# Help for Builtins
code:
```
hacker@man~help-for-builtins:~$ help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!
    
    Options:
      --fortune         display a fortune
      --version         display the version
      --secret VALUE    prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "gX3C4eeE".
hacker@man~help-for-builtins:~$ challenge --secret gX3C4eeE
Correct! Here is your flag!
pwn.college{gX3C4eeEwKBWKlc0jP-bbTPCpa1.QX0ETO0wiMwEzNzEzW}
```
