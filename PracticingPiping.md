# Redirecting Output 
code:
```
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your 
flag:
pwn.college{MzoOJmTpFbk_DEUTGmqbR4uUwOJ.QX0YTN0wiMwEzNzEzW}
```


# Redirecting More Output 
code:
```
hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{oyFrN7X8C5GTnBdLLwGLZvTrRkr.QX1YTN0wiMwEzNzEzW}

```


# Appending Output
code:
```
hacker@piping~appending-output:~$ /challenge/run >> /home/hacker/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do 
the first write directly to the file, and the second write, I'll do to stdout 
(if it's pointing at the file). If you redirect the output in append mode, the 
second write will append to (rather than overwrite) the first write, and you'll 
get the whole flag!
hacker@piping~appending-output:~$ cat /home/hacker/the-flag
 | 
\|/ This is the first half:
 v 
pwn.college{cDwoQ1glwWKoYG_CnBi9mP2S3TR.QX3ATO0wiMwEzNzEzW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>) 
rather than *append* mode (>>), and so the write of the second half to stdout 
overwrote the initial write of the first half directly to the file. Try append 
mode!
hacker@piping~appending-output:~$ 
```


# Redirecting Errors
code:
```
hacker@piping~redirecting-errors:~$ /challenge/run > myflag 2>
 instructions
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{EmE9zG_Ji7L1D9l0E8Z93Alo_Ez.QX3YTN0wiMwEzNzEzW}
```


# Redirecting Input
code:
```
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read 
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{IHINM8VBJE_Ih8xYoGU7bzD_FD8.QXwcTN0wiMwEzNzEzW}
```


# Grepping Stored Results
code:
```
hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
hacker@piping~grepping-stored-results:~$ grep -ni 'flag' /tmp/data.txt
hacker@piping~grepping-stored-results:~$ grep -nE '\{.*\}' /tmp/data.txt
28951:pwn.college{U5svksqVrXngdkTCA6bl6HD-YyI.QX4EDO0wiMwEzNzEzW}
```

# Grepping Live Output
code:
```
hacker@piping~grepping-live-output:~$ /challenge/run | grep -n
i 'flag'
hacker@piping~grepping-live-output:~$ /challenge/run | grep -Eo '\{[^}]+\}'
[PASS] Success! You have satisfied all execution requirements.
{0sIIvIV7S9yz45qwi81q6IVGrjs.QX5EDO0wiMwEzNzEzW}
```


# Grepping Errors
code:
```
hacker@piping~grepping-errors:~$ /challenge/run 2>&1 | grep -ni 'flag'
hacker@piping~grepping-errors:~$ /challenge/run 2>&1 | grep -Eo '\{[^}]+\}'
[PASS] Success! You have satisfied all execution requirements.
{IKYXFphvtiwmoTAmTfvMKMSula2.QX1ATO0wiMwEzNzEzW}
```


# Filtering with Grep -v
code:
```
hacker@piping~filtering-with-grep-v:~$ /challenge/run | grep -v 'DECOY'
pwn.college{os6mawOpkz-61Ckib1-FTbLopr5.0FOxEzNxwiMwEzNzEzW}
```


# Duplicating Piped Data with Tee
code:
```
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee /tmp/pwn_output.txt | /challenge/college
Processing...
The input to 'college' does not contain the correct secret code! This code 
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the 
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:~$ cat /tmp/pwn_output.txt
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "kGTwN1KI"
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret kGTwN1KI | /challenge/college
Processing...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{kGTwN1KIRQ1A8KF8i_Vw5oPgvDG.QXxITO0wiMwEzNzEzW}
hacker@piping~duplicating-piped-data-with-tee:~$
```


# Process Substitution for Output
code:
```
hacker@piping~process-substitution-for-input:~$ diff <( /challenge/print_decoys ) <( /challenge/print_decoys_and_flag )
43a44
> pwn.college{06n1VhzR_Pdil2DJ2yVe9T3gUYH.0lNwMDOxwiMwEzNzEzW}
```


# Writing to Multiple Programs
code:
```
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >( /challenge/the ) >( /challenge/planet )
This secret data must directly and simultaneously make it to /challenge/the and 
/challenge/planet. Don't try to copy-paste it; it changes too fast.
11967155301869310305
Congratulations, you have duplicated data into the input of two programs! Here 
is your flag:
pwn.college{QA9VbphefINLlDjYBMk5Utwj7mQ.QXwgDN1wiMwEzNzEzW}
```
process:
- /challenge/hack outputs data.
- tee reads that output and duplicates it.
- One copy goes to /challenge/the via the first >(...).
- The other copy goes to /challenge/planet via the second >(...).
- tee also sends a copy to its standard output, but since you didn't redirect that, it just prints to your terminal (you can ignore or redirect it if needed).


# Split-piping stderr and stdout
code:
```
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack > >( /challenge/planet ) 2> >( /challenge/the )
Congratulations, you have learned a redirection technique that even experts 
struggle with! Here is your flag:
pwn.college{E91OaHum_jIXt6njBk8prtmzO3K.QXxQDM2wiMwEzNzEzW}
```


# Named Pipes
code:
```
