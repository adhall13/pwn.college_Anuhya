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

## What I learnt
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
hacker@paths~position-thy-self:~$ cd /
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


# Position Elsewhere
For this challenge, you will be required to execute the `/challenge/run` program from a specific path (which will be told) and need to cd to that directory before rerunning the challenge program

## The Solve
To address this challenge, we need to use the `cd` (change directory) command to navigate our shell to the particular path needed by the challenge program. First, we determine the required directory from the provided instructions. Next, we run the `cd` command followed by that path as its argument (for instance, `cd /the/required/path`). After we have successfully altered our current working directory, we can then run the program, `/challenge/run`, to finish the task.

code:
```
hacker@paths~position-elsewhere:~$ cd /tmp
hacker@paths~position-elsewhere:/tmp$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{Iwf5g3KXOtFnnGx1USi909PiK6Z.QX3QTN0wiMwEzNzEzW}
```
flag: `pwn.college{Iwf5g3KXOtFnnGx1USi909PiK6Z.QX3QTN0wiMwEzNzEzW}`

## What I learnt
The main concepts I grasped from this challenge revolved around navigating the Linux filesystem. I learned how to alter my location within the system using the fundamental `cd` (change directory) command, which requires a path as its argument. This command adjusts the current working directory of my shell process. Additionally, I realised that the tilde (`~`) symbol in the shell prompt indicates the path of my current location in the shell. Ultimately, the challenge taught me that I must be in the right directory—using `cd`—before I can run a program like `/challenge/run`.

## References 
None used for this challenge


# Position Yet Elsewhere
For this challenge, you will be required to execute the `/challenge/run` program from a specific path (which will be told). You'll need to cd to that directory before rerunning the challenge program.

## The Solve
To solve it, we must first identify the specific path required by the instructions. We then use the `cd` command, like `cd /the/required/path`, to change our shell's current working directory to that location. Once successfully positioned, we execute the program `/challenge/run` to complete the task.

code:
```
hacker@paths~position-yet-elsewhere:~$ cd /proc/148/fd
hacker@paths~position-yet-elsewhere:/proc/148/fd$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{MS86CwnojvDdxy3tEKw1-Z6Shx2.QX4QTN0wiMwEzNzEzW}

```
flag: `pwn.college{MS86CwnojvDdxy3tEKw1-Z6Shx2.QX4QTN0wiMwEzNzEzW}`

## What I learnt
The essential ideas derived from this exercise include the crucial function of the `cd` command for navigating the filesystem, and the realisation that this command alters the current working directory of the shell process. Furthermore, I learnt that the tilde (`~`) character in the shell prompt serves as a shorthand indicator of the present position in the filesystem, offering instant feedback on the location of our process.

## References 
None used for this challenge


# Implicit Relative Paths, from /
For this challenge, you will need to run /challenge/run using a relative path while having a current working directory of /

## The Solve
To solve this specific challenge, we must first change our current working directory to the root directory, `/`, by using the command: `cd /`. Once our shell is located at the root, we can construct the correct relative path to the program `/challenge/run`. Since relative paths are interpreted starting from the current working directory and do not begin with a slash, the correct path to use in this context is `challenge/run`. Therefore, the solution involves executing `cd /` followed by running the program using that specific relative path.

code:
```
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{Qs_MZ-aQQM7oJMTzWt9JSmKauQ3.QX5QTN0wiMwEzNzEzW}
```
flag: `pwn.college{Qs_MZ-aQQM7oJMTzWt9JSmKauQ3.QX5QTN0wiMwEzNzEzW}`

## What I learnt
The key concept I learnt here is the critical difference between absolute paths and relative paths in the Linux filesystem. An absolute path always starts at the root (`/`) and works regardless of the current working directory. In contrast, a relative path does not start with `/` and is interpreted relative to the current working directory. The challenge demonstrates that the same target file requires different relative paths depending on where our shell is located. Furthermore, I learnt the special meaning of `..`, which allows us to reference the parent directory when building relative paths

## References 
None used for this challenge


# Explicit Relative Paths, from /
For this challenge, you will need to use `.` which refers to the current directory, to make your relative paths more explicit

## The Solve
To solve the challenge, we should use the single dot `.` in the relative path when referencing the target file or directory. Since the single dot explicitly refers to the current directory, a typical solution involves starting your relative path with `./`. 

code:
```
hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{w8RDYFvu-nY8WahZIkH1xj9_vGx.QXwUTN0wiMwEzNzEzW}

```
flag: `pwn.college{w8RDYFvu-nY8WahZIkH1xj9_vGx.QXwUTN0wiMwEzNzEzW}`

## What I learnt
The key concept is understanding that the single dot (`.`) explicitly refers to the current working directory. This allows you to create explicit relative paths, such as `./filename`, which clarifies that the path starts from your current location. Importantly, the file system treats repeated use of `./` (e.g., `././challenge`) and trailing `/.` (e.g., `challenge/.`) as redundant but valid references, confirming that paths like `challenge` and `./challenge` are functionally equivalent.

## References 
None used for this challenge


# Implicit Relative Path
This challenge requires executing the program named `run` located in the current working directory, which is `/challenge`

## The Solve
The challenge is solved by explicitly telling the Linux shell to execute the program run located in the current directory (`/challenge`) by using the relative path indicator `./` before the program name. Since Linux does not automatically look in the current directory for security reasons, simply typing run results in a "command not found" error. By executing the command as `./run`, the dot (`.`) represents the current directory, the forward slash (`/`) acts as a path separator, and the shell is correctly instructed to look in the current location for the executable file, thus successfully launching the program

code:
```
hacker@paths~implicit-relative-path:/$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{c2PsSN2E8yNjv6cjXVRwqXt1lqG.QXxUTN0wiMwEzNzEzW}
```
flag: `pwn.college{c2PsSN2E8yNjv6cjXVRwqXt1lqG.QXxUTN0wiMwEzNzEzW} `

## What I learnt
The key concept learned from this challenge is the necessity of using the relative path prefix `./` when executing programs located in the current working directory on Linux. This practice explicitly tells the shell to look in the present location (represented by the dot, `.`) for the executable, as simply typing the program name will fail with a "command not found" error. This behaviour is a fundamental security measure in Linux, preventing accidental execution of programs in the current directory that might inadvertently share the names of core system utilities.

## References 
None used for this challenge


# Home Sweet Home
The challenge requires you to execute the program `/challenge/run` and provide it with a single absolute path as a command-line argument, where the program will write a copy of the flag. This argument must satisfy three strict constraints: the final, expanded path must be a valid absolute path; the path must reside inside your home directory (`/home/hacker`); and critically, the path argument must be three characters or less before the shell performs any expansion. The goal is to use a path shorthand to meet both the absolute path and the length constraints simultaneously.

## The Solve
The challenge requires us to execute the program `/challenge/run` and provide it with a single absolute path as a command-line argument, where the program will write a copy of the flag. This argument must satisfy three strict constraints: the final, expanded path must be a valid absolute path; the path must reside inside our home directory (`/home/hacker`); and critically, the path argument must be three characters or fewer before the shell performs any expansion. The goal is to use a path shorthand to meet both the absolute path and the length constraints simultaneously.

code:
```
hacker@paths~home-sweet-home:~$ /challenge/run ~/f
Writing the file to /home/hacker/f!
... and reading it back to you:
pwn.college{Y-joQ8ey8ROGU9LFxAfBuhSPYG7.QXzMDO0wiMwEzNzEzW}
```
flag: `pwn.college{Y-joQ8ey8ROGU9LFxAfBuhSPYG7.QXzMDO0wiMwEzNzEzW} `

## What I learnt
I learnt from this challenge the remarkable usefulness of tilde expansion (`~`) in the Bash shell. I learned that this single character `~` is a shortcut that the shell automatically converts to the absolute path of my home directory (`/home/hacker`) before executing a command. This feature proved essential for completing the challenge, as it enabled me to circumvent the strict three-character length limitation while also providing an absolute path located within my home directory, fulfilling all the program's criteria with the succinct command: `/challenge/run ~`.

## References 
None used for this challenge
