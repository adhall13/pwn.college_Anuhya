# The Root
For this challenge, launch a terminal, invoke the pwn program using its absolute path to capture the flag

## The Solve
I will launch a program by specifying its path in the command line. In this instance, I will provide the complete path, beginning from /, so the path will be /pwn. This type of path, which starts from the root directory, is known as an "absolute path."

code:
```
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{sChKj3fPT6HG2ZzbNXQ2yHGDh3R.QX4cTO0wiMwEzNzEzW}
```
flag: `pwn.college{sChKj3fPT6HG2ZzbNXQ2yHGDh3R.QX4cTO0wiMwEzNzEzW}`

## What I learned
Through this challenge, I understood the core of the filesystem begins at the root directory (/), where all other directories and files branch out. An absolute path is a full address that starts from this root, and providing this path on the command line allows you to execute or "invoke" a specific program. For example, running the program at /pwn requires specifying that exact absolute path

## References 
None used for this challenge


# PROGRAMS AND ABSOLUTE PATHS
For this challenge, we must execute it by invoking its absolute path

## The Solve
In this task, the location of the challenge directory is /challenge. The challenge program for this level is called run and is located in the /challenge directory. Therefore, the full path to the run challenge program is /challenge/run. We can execute it by using its absolute path, after which I will obtain the flag.

code:
```
hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{4ehI2Lik4C_YFqovRQU1y6WMT5i.QX1QTN0wiMwEzNzEzW}
```
flag: `pwn.college{4ehI2Lik4C_YFqovRQU1y6WMT5i.QX1QTN0wiMwEzNzEzW} `

## What I learnt
This challenge taught me how to execute a program using its absolute path, which is a file's complete address from the root directory, denoted by /. Specifically, the challenge program is located at /challenge/run, and you must invoke it with its full, absolute path to receive the flag, not a relative path or just the filename. 

## References 
None used for this challenge


# POSITION THY SELF
This challenge will require you to execute the /challenge/run program from a specific path (which it will tell you) and need to cd to that directory before rerunning the challenge program. 

## The Solve
To solve this challenge, we must first run the /challenge/run program. This program will output a specific directory path. The task is to then change their current working directory to the path provided by the program. This is achieved using the cd command, followed by the specific path as an argument. For instance, if the program outputs /path/to/target/directory, then we would execute cd /path/to/target/directory. After successfully changing the directory, we must then re-execute the /challenge/run program, which will now be executed from the required current working directory, thus fulfilling the challenge's requirements.

code:
```
hacker@paths~position-thy-self:/$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{gKP3l6bw3MmpI056iWkOJsGXhU5.QX2QTN0wiMwEzNzEzW}
```
flag: `pwn.college{gKP3l6bw3MmpI056iWkOJsGXhU5.QX2QTN0wiMwEzNzEzW}`

## What I learnt
This challenge taught me how to execute a program using its absolute path, which is a file's complete address from the root directory, denoted by /. Specifically, the challenge program is located at /challenge/run, and you must invoke it with its full, absolute path to receive the flag, not a relative path or just the filename. 

## References 
None used for this challenge


