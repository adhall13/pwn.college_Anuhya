# Redirecting Output 
The challenge is simple and specific: use shell output redirection to write the exact string `PWN` (uppercase) into a file named `COLLEGE` (uppercase). 

## The Solve
The straightforward solution is to run a shell command that emits `PWN` and redirect that output into the file `COLLEGE`
code:
```
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your 
flag:
pwn.college{MzoOJmTpFbk_DEUTGmqbR4uUwOJ.QX0YTN0wiMwEzNzEzW}
```

## What I learnt 
This exercise reinforces core shell concepts: how `>` redirects and truncates or creates files, the difference between `>` and `>>` (overwrite vs append), how commands like `echo` and `printf` produce stdout, and that filenames and payloads are case-sensitive on typical Unix-like systems (so `COLLEGE` ≠ `college`). It also highlights small practical details — `echo` may add a newline, shell expansions or quotes can change the output, and file permissions/environment affect whether redirection succeeds — all useful basics for safe, predictable shell scripting and operations. 

## References
None used for this challenge


# Redirecting More Output 
The challenge asks to redirect the output of the /challenge/run command to a file named `myflag`, capturing the flag, while ensuring that instructions and feedback (printed to stderr) still appear on the terminal.

## The Solve
 You can redirect just the `stdout` (where the flag is printed) to the file `myflag` using: `/challenge/run > myflag`. This keeps the `stderr` visible in the terminal while saving the flag in the file.

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

## What I learnt
This exercise drills the crucial distinction between `stdout` and `stderr` and when to capture one stream but not the other. It reinforces that `>` only affects `stdout`, that `2>` targets `stderr`, and that `2>&1` merges streams. Practically, it’s a useful pattern: capture machine-readable output to files while keeping human-readable errors and prompts visible — a technique common in scripting, logging, and debugging.

## References
None used for this challenge


# Appending Output
The challenge asks to run `/challenge/run` so that its output is appended to the file `/home/hacker/the-flag` (not overwritten). The program writes the first half of the flag into the file and the second half to `stdout`; if you use truncation (`>`), the second half will overwrite the first, and you’ll lose half the flag — so you must use append mode.

## The Solve
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

## What I learnt
This reinforces the difference between `>` (truncate/create) and `>>` (append) and why append is essential when aggregating outputs across multiple runs. It’s a practical reminder to choose redirection mode carefully to avoid unintentionally destroying previously collected data, and to check file permissions and confirm results after redirection.

## References
None used for this challenge


# Redirecting Errors
The level requires you to capture the flag into a file named `myflag` and capture everything it prints to standard error into a separate file named `instructions`. Because both streams must be redirected, nothing should be left printing to the terminal — the flag should end up in `myflag` and the instructions in `instructions`.

## The Solve
Run the program and explicitly redirect FD 1 (stdout) and FD 2 (stderr) to the two files. Verify with `cat myflag` to read the flag and `cat instructions` to read the program’s messages. Ensure you have write permission in the current directory so both files can be created/overwritten.

code:
```
hacker@piping~redirecting-errors:~$ /challenge/run > myflag 2>
 instructions
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{EmE9zG_Ji7L1D9l0E8Z93Alo_Ez.QX3YTN0wiMwEzNzEzW}
```

## What I learnt
This exercise reinforces how Linux uses file descriptors (0,1,2) for stdin/stdout/stderr, how `>` without a number implies `1>`, and how to redirect multiple FDs at once. It shows a practical pattern: separate machine-readable output (stdout) from human-readable errors/prompts (stderr) into different files, which is useful for logging, automated parsing, and debugging.

## References
None used for this challenge


# Redirecting Input
The level requires supplying the program’s standard input from a file named `PWN`, and that `PWN` file must contain the exact text `COLLEGE`. 

## The Solve
Create the file `PWN` and put the exact word `COLLEGE` into it (overwriting any previous contents). Then invoke the challenge so that its standard input comes from the `PWN` file. 
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

## What I learnt 
This challenge highlighted the power of input redirection, showing how programs can read from files instead of waiting for manual input. It also reinforced the importance of precision when specifying filenames and content, particularly with case sensitivity and avoiding extra characters. Additionally, I learned how input and output redirection can be combined effectively to automate tasks and streamline processes in the command line.

## References
None used for this challenge


# Grepping Stored Results
The challenge asks you to capture the output of a program (`/challenge/run`) into a file and then locate the single line among ~100,000 lines that contains the flag.

## The Solve
code:
```
hacker@piping~grepping-stored-results:~$  /challenge/run > /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$  grep pwn /tmp/data.txt
pwned
pwning
pwn
pwn.college{U5svksqVrXngdkTCA6bl6HD-YyI.QX4EDO0wiMwEzNzEzW}
pwns
```

## What I learnt
This exercise reinforces basic but essential shell skills: redirection (`>`), understanding stdout vs stderr (stdout is the normal output of a program, while stderr is used for error messages), and powerful text processing with `grep` and regular expressions. 

## References
None used for this challenge


# Grepping Live Output
The challenge asks to capture the output of `/challenge/run` and find the single line that contains the flag, but instead of saving to a file first, you must use a pipeline so the program’s stdout flows directly into a searching tool.

## The Solve

code:
```
hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{0sIIvIV7S9yz45qwi81q6IVGrjs.QX5EDO0wiMwEzNzEzW}
```

## What I learnt 
Pipes let you process large outputs in‑memory without creating temporary files, making workflows simpler and faster. `grep` with a regex extracts the flag pattern directly.

## References
None used for this challenge


# Grepping Errors
The challenge asks to extract specific information from standard error (stderr) output by redirecting it to standard output (stdout) and then piping the combined output to a program like `grep` for further searching. 

## The Solve
code:
```
hacker@piping~grepping-errors:~$ /challenge/run 2>& 1 | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{IKYXFphvtiwmoTAmTfvMKMSula2.QX1ATO0wiMwEzNzEzW}
```

## What I learnt
This challenge taught me how to combine redirecting output and error streams using the `2>&1` operator.  
`2>&1`: redirects standard error to standard output; 

## References
None used for this challenge


# Filtering with Grep -v
The challenge gives a command `/challenge/run` that prints the real flag mixed together with over a thousand decoy flags — every decoy contains the literal string `DECOY` somewhere in the line; for this challenge, extract the single real flag from all the decoy lines. 

## The Solve
code:
```
hacker@piping~filtering-with-grep-v:~$ /challenge/run | grep -v 'DECOY'
pwn.college{os6mawOpkz-61Ckib1-FTbLopr5.0FOxEzNxwiMwEzNzEzW}
```

## What I learnt
This exercise reinforces how powerful simple Unix text tools are when combined with pipes: `grep -v` is an easy way to invert selections and remove unwanted decoys (noise) from data (stream) instead of trying to pick the one correct line out of thousands. Beware that an inverted filter will drop any line containing the pattern (so if the real flag ever contained the same token, we need a different approach).

## References
None used for this challenge


# Duplicating Piped Data with Tee
The challenge requires running the two-process pipeline while also inspecting the data that flows from `pwn` so you can discover what `pwn` is asking for and then provide the correct input to make the overall pipeline succeed. 

## The Solve
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

## What I learnt
The task taught me that `tee` is a straightforward tool to make a pipeline observable without interrupting data flow. Moreover, `tee` only mirrors stdout unless you redirect stderr, `-a` appends instead of overwriting, and captures intermediate output.

## References
None used for this challenge


# Process Substitution for Input
The challenge asks us to identify the real flag hidden among several decoy flags by comparing the outputs of two programs: `/challenge/print_decoys`, which prints a list of decoy flags, and `/challenge/print_decoys_and_flag`, which prints the same decoys along with the real flag. 

## The Solve

code:
```
hacker@piping~process-substitution-for-input:~$ diff <( /challenge/print_decoys ) <( /challenge/print_decoys_and_flag )
43a44
> pwn.college{06n1VhzR_Pdil2DJ2yVe9T3gUYH.0lNwMDOxwiMwEzNzEzW}
```

## What I learnt 
Through this challenge, I learnt the shell adheres to this by allowing us to treat not only traditional files but also the input and output of programs as file-like objects. This concept becomes especially powerful with Process Substitution, which enables us to hook the output of a command directly to the input of another, bypassing the need for temporary files. By using `<(command)`, we can treat the output of a command like a file, and with `(command)`, we can feed input to a command as if it were coming from a file. This capability makes it possible to seamlessly connect commands and utilities, allowing for more efficient and elegant workflows in the shell.


## References
None used for this challenge


# Writing to Multiple Programs
This challenge asks us to duplicate the output of the `/challenge/hack` command and pipe it as input to two other commands, `/challenge/the` and `/challenge/planet` without needing temporary files. 

## The Solve

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

## What I learnt 
Through this challenge, I gained a deeper understanding of how process substitution can be used not just for reading data, but also for writing data to commands. I learned how to combine `tee` with output process substitution to duplicate data to multiple commands at once. 

## References
None used for this challenge


# Split-piping stderr and stdout
In this challenge, need to redirect the output from the `/challenge/hack` command to two separate programs, `/challenge/the` and `/challenge/planet`. Specifically, the challenge asks you to send `stderr` (standard error) to `/challenge/the` and `stdout` (standard output) to `/challenge/planet`. The key difficulty here is keeping these two streams separate while still using shell piping.

## The Solve
code:
```
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack > >( /challenge/planet ) 2> >( /challenge/the )
Congratulations, you have learned a redirection technique that even experts 
struggle with! Here is your flag:
pwn.college{E91OaHum_jIXt6njBk8prtmzO3K.QXxQDM2wiMwEzNzEzW}
```

## What I learnt 
This challenge deepened my understanding of how to manipulate file descriptors in Unix-like systems. I learned how to use `2>`, `>(...)`, and `|` together to separate `stderr` and `stdout` and send them to different destinations. The power of process substitution became clear, as it allowed me to route `stderr` to a command without mixing it with `stdout`. I also reinforced the importance of understanding how file descriptors work in shell scripting, which is crucial for advanced tasks like managing multiple output streams.

## References
None used for this challenge


# Named Pipes
The challenge asks to create a persistent named pipe (FIFO) at `/tmp/flag_fifo` and then redirect the stdout of `/challenge/run` into that FIFO so that `/challenge/run` will write the flag into it. 

## The Solve
code:
```
hacker@piping~named-pipes:~$ mkfifo /tmp/flag_fifo
hacker@piping~named-pipes:~$ /challenge/run > /tmp/flag_fifo
You're successfully redirecting /challenge/run to a FIFO at /tmp/flag_fifo! 
Bash will now try to open the FIFO for writing, to pass it as the stdout of 
/challenge/run. Recall that operations on FIFOs will *block* until both the 
read side and the write side is open, so /challenge/run will not actually be 
launched until you start reading from the FIFO!
----------------------------------------------------------------------------
hacker@piping~named-pipes:~$  cat /tmp/flag_fifo
You've correctly redirected /challenge/run's stdout to a FIFO at
/tmp/flag_fifo! Here is your flag:
pwn.college{MbHdj-mVp10Kc1SiOyAui11b-A_.01MzMDOxwiMwEzNzEzW}
```

## What I learnt 
This exercise reinforced how FIFOs (mkfifo) let processes communicate through a filesystem-visible pipe: they don’t store data on disk, data is ephemeral (consumed once), and reads/writes automatically synchronize because operations block until the other side is ready. FIFOs are handy for orchestrating complex workflows or connecting multiple readers/writers without temporary files, but you must manage blocking behavior (use separate terminals or background processes) and clean up the FIFO when finished.

## References
None used for this challenge

