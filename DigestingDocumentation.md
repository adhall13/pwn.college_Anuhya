# Learning From Documentation
The challenge is asking us to solve the problem of properly invoking the `/challenge/challenge` program in order to receive the flag. To do this, we need to correctly identify and provide the required command-line argument, which, according to the documentation, is `--giveflag`. 

## The Solve
To solve the challenge, we must refer to the provided documentation, which clearly states that the program requires the argument `--giveflag` to function properly. To run the program and get the flag, we should enter the following command: `/challenge/challenge --giveflag`. By including this argument, the program will execute as expected and output the flag, solving the challenge.

code:
```
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{U0yhomrUaflY4TjCjxlJOeNtybd.QX0ITO0wiMwEzNzEzW}
```

## What I learnt
I learnt about command-line arguments and their role in controlling program behaviour. Similar to the `-a` option in the `ls` command for listing hidden files, arguments like `--giveflag` change the program’s operation. The challenge emphasises the importance of reading and interpreting documentation to determine which arguments are needed for a program to work correctly. This is an essential skill in navigating software and systems.

## References
None used for this challenge


# Learning Complex Usage
The challenge is asking us to solve the problem of properly using the `/challenge/challenge` program to print the flag by providing the correct arguments. The program requires two arguments: `--printfile`, which specifies that we want to print a file, and the path to the flag file itself, which is the second argument. 

## The Solve
To solve the challenge, we need to run the `/challenge/challenge` program with the `--printfile` argument followed by the correct path to the flag file. Based on the documentation, we can see that a valid command might look like `/challenge/challenge --printfile /challenge/flag.txt`, where `/challenge/flag.txt` is the file containing the flag. By running the program with the correct file path, the flag will be printed to the terminal.

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

## What I learnt
The key concepts I learnt from this challenge involve understanding how commands can take multiple arguments, including arguments to arguments, and how to use these in practice. In this case, the `--printfile` argument takes an additional argument specifying the file path to print. This challenge also reinforces the importance of reading documentation carefully to understand the expected structure of commands, as well as how arguments interact with each other to control the behaviour of a program.
short note:
ls -al
=> ls: The base command, which lists the contents of a directory.
-l (long format): This option displays file and directory information in a table with seven columns of detailed attributes.
-a (all): This option includes hidden files in the output. Hidden files and directories have names that begin with a dot (.)

## References
None used for this challenge


# Reading Manuals
The challenge asks us to discover and use a secret command-line option for the `/challenge/challenge` program that will cause it to print the flag. We are expected to find the necessary information ourselves using the program's manual; using the `man` command. 

## The Solve
To solve the challenge, we must run the command `man challenge` in the terminal. This will open the manual page for the `challenge` program, where we can read through the available options and usage information. By carefully reviewing the `SYNOPSIS` and `DESCRIPTION` sections, we should be able to identify the secret flag or option mentioned in the documentation. Once discovered, we can then run the program with that option to get the flag. 

code:
```
hacker@man~reading-manuals:~$ man challenge
hacker@man~reading-manuals:~$ /challenge/challenge --kkvbux 364
Correct usage! Your flag: pwn.college{kkvT3GUbux6GQ44fCJeUUPdrq3m.QX0EDO0wiMwEzNzEzW}
```

## What I learnt
The key concepts of this challenge revolve around using the `man` command to read manual pages, which is an essential skill for understanding how Unix-like commands work. This includes learning how to interpret the structure of a manpage, such as the `NAME`, `SYNOPSIS`, and `DESCRIPTION` sections, and recognising that command-line tools often include undocumented or less obvious options that can only be found by reading the official documentation. 

## References
None used for this challenge


# Searching Manuals
The challenge asks us to discover the specific option within the `/challenge/challenge` program's man (manual) page that will make the program output the flag. 

## The Solve
To solve the challenge, we must run the command `man challenge` to open the manual page for the program. Once inside the man page, we can search for the relevant option using `/` followed by keywords (such as "flag" or "option"). After finding the right entry, we can execute the program with that option to retrieve the flag. Additionally, we can use `n` to jump to the next search result or `N` to go to the previous one, which makes it easier to navigate through the results.

code:
```
hacker@man~searching-manuals:~$ man challenge
hacker@man~searching-manuals:~$ /challenge/challenge --xi
Initializing...
Correct usage! Your flag: pwn.college{IBo6p-5IgB4xt-xjQp2EBH5ar3u.QX1EDO0wiMwEzNzEzW}
```


## What I learnt
The key concepts I learnt from this challenge involve using the `man` command to read manual pages and effectively searching within them using `/` for forward searches and `?` for backward searches. 

## References
None used for this challenge


# Searching For Manuals
The challenge asks to find a hidden, randomly named manpage that contains documentation for a secret option of the `/challenge/challenge` program so you can make that program print the flag. 

## The Solve
To solve the challenge, you first read the manual using the `man` command (`man man`) to learn its advanced search capabilities. Use `man -k <keyword>` to search short manpage descriptions with keywords like “challenge” or “flag” to reveal the randomised manpage entry. Open the found manpage with `man <entry>` and search within it using `/` to locate the secret option; finally, invoke `/challenge/challenge --<keyword value>` which will upon execution generate the flag.

code:
```
hacker@man~searching-for-manuals:~$ man man
hacker@man~searching-for-manuals:~$ man -k challenge
camioqiuxe (1)       - print the flag!
hacker@man~searching-for-manuals:~$ man camioqiuxe
hacker@man~searching-for-manuals:~$ /challenge/challenge --camioq 263
Correct usage! Your flag: pwn.college{c2SBa63m-3iWoqi-BuxOe3w0d9o.QX2EDO0wiMwEzNzEzW}
```

## What I learnt
The key concepts are that manpages are stored in a centralized searchable database (MANPATH), and `man` provides tools for locating entries without knowing their filenames (`-k` is for short descriptions and `-K` is for full text). Navigating and searching inside a manpage (use `/` to search, `n` (is for next)/`N` (is for previous) to move between matches, arrow keys or PgUp/PgDn to scroll, and `q` to quit). 

## References
None used for this challenge


# Helpful Programs
The challenge asks to solve the problem of reading a program’s documentation when it doesn’t have a manpage, but instead provides help information through a  built-in help feature, `--help`. 

# The Solve
To solve the challenge, you need to invoke the program with the `--help` argument (or possibly `-h`, depending on the program) to display its documentation. Once the help information is displayed, carefully read through the options and usage instructions to understand how the program works. If the help output is long, you may need to scroll or search for specific keywords to find the relevant details. The goal is to learn how to correctly use the program based on the provided help documentation.

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

# What I learnt
The key concepts I learnt through this challenge involve recognising that many programs offer built-in documentation through arguments such as `--help`, `-h`, or `-?`. These options are crucial for using a program effectively when a manpage is not available.

## References
None used for this challenge


# Help for Builtins
The challenge asks to discover the secret argument for the `challenge` command when that command is a shell rather than an external program. 

# The Solve
To solve the challenge, we should run the shell’s `help` command for the builtin: `help challenge`. That will display the synopsis and description the shell provides for that builtin. Read the displayed to find the value of the builtin expects, then invoke the builtin with that value to make it print the flag.

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

# What I learnt
Key concepts I leanrt are the distinction between external programs and shell builtins, and how the shell handles builtins internally instead of launching separate processes. I also leanrnt that the shell exposes builtin documentation via the `help` command (and `help <name>` for specific entries) as you can’t inspect them the same way you would ordinary programs; instead must recognize that `challenge` is handled internally by the shell and that its usage information is exposed through the shell’s `help` builtin.

## References
None used for this challenge
