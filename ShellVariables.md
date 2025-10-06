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
This exercise teaches me about shell variables and parameter expansion: a `$` before a name tells the shell to replace that token with the variable’s value before running the command. It also highlights that the environment available to your interactive shell can hold secrets (like `FLAG`) separate from what a particular program returns, and that simple built-in commands can be used to inspect those variables.

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
This exercise taught me that the challenge reinforces shell variable assignment and expansion: `NAME=VALUE` creates or changes a shell variable, and `$NAME` expands to its value. Important gotchas are that there must be no spaces around the `=` and that both variable names and values are case-sensitive. Also note the distinction between assigning a shell variable and exporting it to the environment — a plain assignment lives in the current shell unless you explicitly export it. Also revised the concept of shell being case-sensitive. 

## References
None used for this challenge


# Multi-word Variables
The challenge asks you to set a variable in the shell, but with a value that contains spaces. Specifically, asked to assign the value "COLLEGE YEAH" to the variable PWN. 

## The Solve
To solve the challenge, you must ensure that the entire value, `COLLEGE YEAH`, is treated as a single entity. In the shell, this can be done by using a method to prevent the space from being interpreted as a separator. The solution would be to encapsulate the multi-word string in a way that treats it as a single token, avoiding the shell splitting it up.

code:
```
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{gvC-2y5JgwgVN2etELt_AEKsByw.QXwYTN0wiMwEzNzEzW}
```

## What I learnt 
The key concepts here I learnt are variable assignment and shell parsing. When assigning a value to a variable, there should be no spaces around the `=` sign. Additionally, spaces within a value are interpreted by the shell as argument separators, which can cause errors. 

## References
None used for this challenge


# Exporting Variables
The challenge asks to work with environment variables in the shell. Specifically, it requires setting the variable PWN to the value COLLEGE and exporting it, while setting another variable COLLEGE to the value PWN but not exporting it. After setting up the variables, you must run a command (/challenge/run) where the PWN variable is inherited because it was exported, but the COLLEGE variable is not inherited because it was not exported.

## The Solve
To solve the challenge, we first set the PWN variable to COLLEGE and export it using the export command. This will ensure that the PWN variable is passed into the environment of child processes. Next, you need to set the COLLEGE variable to PWN, but do not export it. Since it is not exported, it won't be inherited by any child processes, such as the /challenge/run command. After setting the variables, run `/challenge/run`, which will result in the `PWN` variable being inherited, but the COLLEGE variable will not be.

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

## What I learnt 
The key concepts in this challenge I learnt revolve around local shell variables versus environment variables. By default, when you set a variable in the shell, it is a local shell variable, meaning it is only accessible within the current shell process. Child processes (such as new shells or commands) will not inherit local variables. To make a variable available to child processes, you need to export it, turning it into an environment variable. Once exported, the variable can be inherited by any child process, allowing programs or scripts to access it. This is a crucial concept in managing data flow between processes, especially when dealing with sensitive information or configuring the environment for various commands.

In this challenge, we export the `PWN` variable, making it available to child processes like `/challenge/run`, while ensuring that the `COLLEGE` variable is not exported, meaning it won't be passed into the environment of child processes. 

## References
None used for this challenge


# Printing Exporting Variables
The challenge asks to locate the `FLAG` variable by using a method other than `echo`; specifically, it directs you to use the `env` command to print all exported environment variables and then inspect that output to find the `FLAG` entry.

## The Solve
To solve the challenge, run the `printenv FLAG` command

code:
```
hacker@variables~printing-exported-variables:~$ printenv FLAG
pwn.college{klfjOTv0X1_7q3yvFagwwdr45DI.QX4UTN0wiMwEzNzEzW}
```

## What I learnt
Key concepts in this challenge I learnt include understanding that there are multiple ways to read shell variables (for example `echo` and `env`), that `env` displays only exported environment variables.

## References
None used for this challenge


# Sorting Command Output
The challenge asks to capture the output of the `/challenge/run` command into a shell variable named `PWN` so that the variable holds the flag produced by that command rather than just displaying it directly on the terminal.

## The Solve
To solve the challenge we use command substitution to run `/challenge/run` and assign its stdout to the `PWN` variable, which causes the shell to execute the command, capture what it prints, and store that text into `PWN` so you can inspect or use the flag later from the variable.

code:
```
hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out 
and submit it!
hacker@variables~storing-command-output:~$ echo "$PWN"
pwn.college{8nbc38e93hhsqz02p07QgUm7w7a.QX1cDN1wiMwEzNzEzW}
```

## What I learnt 
The key concepts I learnt from the challenge include command substitution (which runs a command and stores its output in a variable), the difference between capturing output and just printing it, and the older backtick syntax. The preferred method today is using `$()` because it’s easier to read and allows for nesting commands more easily.

## References
None used for this challenge


# Reading Input
The challenge asks you to use the read command to set the `PWN` variable to the value `COLLEGE`. The read command allows you to capture user input from the standard input and store it in a variable. In this case, you’ll need to use it to capture the string `COLLEGE` and assign it to `PWN`.

## The Solve
To solve the challenge, use the read command to prompt the user for input, store that input in the `PWN` variable, and make sure the value of `COLLEGE` is captured correctly. Once the variable is set, you can verify it by referencing `PWN` to check that the value has been stored correctly.

code:
```
hacker@variables~reading-input:~$ read -p "INPUT :" PWN
INPUT :COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{A0ygtfH97tGvLtMKhgO6ltkfGVe.QX4cTN0wiMwEzNzEzW}
```

## What I learnt 
Key concepts in this challenge I learnt include understanding the `read` command, which takes input from the user and stores it in a variable, and the use of prompts to guide the user. Another important point is the distinction between input (what the user types) and output (what the program prints), as well as how to properly store user input in a variable and use it in subsequent commands.

## References
None used for this challenge


# Reading Files
Put the current contents of the file `/challenge/read_me` into a shell variable named `PWN` with a single command, without starting an extra program just to read the file.

## The Solve
Use the shell builtin `read` and redirect the file into its standard input so `read` assigns the file’s contents directly into `PWN` in one step.
code:
```
hacker@variables~reading-files:~$ read PWN < /challenge/read_me
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{kd_v4Ve8zoWvSm954wSlwsEJkSn.QXwIDO0wiMwEzNzEzW}
```

## What I learnt 
This exercise reinforces a few important shell fundamentals. First, shell builtins like `read` can operate on redirected standard input (stdin) and assign values directly to the shell environment, which is more efficient than invoking external utilities. Second, input redirection (`<`) lets you feed files into commands without using pipes or extra processes, eliminating the use of `cat`. Third, the distinction between shell builtins and external programs matters for performance and for whether a variable becomes available in the current shell. Finally, because the file changes over time, reading it directly at the moment you run the built-in guarantees you capture the file’s latest contents rather than an earlier snapshot.

## References
None used for this challenge
