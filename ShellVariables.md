# Printing Variables
The challenge hides the flag in a shell variable named FLAG instead of letting the provided program return it. We have to print the contents of that environment variable from the current shell to read the flag directly.

## The Solve
Use a command that prints text to standard output and reference the variable with a leading dollar sign; for example, run `echo $FLAG` in your shell. The shell will substitute the value stored in `FLAG` before `echo` runs, and the variable’s contents (the flag) will be printed to the terminal. If you prefer, other printing utilities like `printf` will work as well, but `echo $FLAG` is the simplest.

code:
```
hacker@variables~printing-variables:~$ echo "$FLAG"
pwn.college{88pvETaZUhs75lwPTchr7TFAxBs.QX3UTN0wiMwEzNzEzW}
```

## What I learnt
This exercise teaches about shell variables and parameter expansion: a `$` before a name tells the shell to replace that token with the variable’s value before running the command. It also highlights that the environment available to your interactive shell can hold secrets (like `FLAG`) separate from what a particular program returns, and that simple built-in commands can be used to inspect those variables.

## References
None used for this challenge


# Setting Variables
For this challenge, create a shell variable named `PWN` and assign it the exact value `COLLEGE`. 

## The Solve
Assign the value to the variable using the shell’s assignment syntax: the variable name, an equals sign with no surrounding spaces, and the value. After that, you can read the variable using the `$` prefix to confirm it holds the expected value. Remember that the `$` is only used when accessing a variable, not when creating it.

code:
```
hacker@variables~setting-variables:~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{w3i3kK9Oqc3OgEttaH_PZCECzUh.QX5UTN0wiMwEzNzEzW}
```

## What I learnt
This exercise reinforces shell variable assignment and expansion: `NAME=VALUE` creates or changes a shell variable, and `$NAME` expands to its value. Important gotchas are that there must be no spaces around the `=` and that both variable names and values are case-sensitive. Also note the distinction between assigning a shell variable and exporting it to the environment — a plain assignment lives in the current shell unless you explicitly export it. Also revised the concept of shell being case-sensitive. 

## References
None used for this challenge


# Multi-word Variables
The challenge asks you to set a variable in the shell, but with a value that contains spaces. Specifically, you are asked to assign the value "COLLEGE YEAH" to the variable PWN. 

## The Solve

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
