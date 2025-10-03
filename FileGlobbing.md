# Matching with *
The challenge requires you to change directory from your home into the absolute path `/challenge` while making sure the single argument you pass to `cd` is no more than four characters long, and then run `/challenge/run` to get the flag.

## How to solve the challenge
Type a compact glob that the shell will expand to `/challenge` — for example, `/ch*`. When the shell performs pathname expansion, it will match entries in the root directory whose names start with `ch`, and `/ch*` will expand to `/challenge`, so `cd /ch*` changes you into `/challenge`. Once there, run the provided program `/challenge/run` to obtain the flag.

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

## What I learnt
I learnt that the exercise depends on filename globbing: `*`. It is a wildcard that matches any sequence of characters except `/` and a leading `.`. The shell expands globs before invoking a command, and a short glob can expand to a longer path — letting you meet the “four-character argument” constraint even though the real pathname is longer. Also note that globs can match zero, one, or many files; here, you rely on a pattern that uniquely matches the desired directory in the filesystem.

## References
None used for this challenge


# Matching with ?
The task is to change directory from your home into the absolute path `/challenge` while using the single-character glob `?` in place of the letters `c` and `l` in the argument you pass to `cd`, then run `/challenge/run` to get the flag.

## The Solve
Type a `cd` command that uses `?` for each of the specified characters so the shell’s pathname expansion produces `/challenge`. For example: `cd /?ha??enge` — here the first `?` stands for `c` and the two `?`s stand in for the two `l` characters; the shell expands `/​?ha??enge` to `/challenge` and `cd` moves you there. After changing the directory, run `/challenge/run` to retrieve the flag.

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

## What I learnt
This exercise taught me single-character globbing: `?` matches exactly one character (not `/` and not a leading `.`). Multiple `?`s can be used to match multiple single characters in specific positions, letting a short pattern expand into a longer filename or path. The shell performs glob expansion before running the command, so you can type a pattern that looks different from the final pathname but still resolves to the target directory.

## References
None used for this challenge


# Matching with []
In this challenge, you are asked to change your working directory to `/challenge/files` and then run `/challenge/run`. However, you need to use a glob pattern with square brackets `[]` to match a specific set of files — specifically, `file_b`, `file_a`, `file_s`, and `file_h` — all with a single argument. This requires you to craft a pattern using square brackets that includes the characters needed to match the filenames you're interested in.

## The Solve
To solve this, you'll need to identify the common pattern in the filenames and use square bracket globbing to match them. The pattern you need is `file_[bahs]`, where the square brackets allow you to match any one of the characters `b`, `a`, `h`, or `s` in place of the last character of the filename. This will match the filenames `file_b`, `file_a`, `file_s`, and `file_h`. Once you're in the right directory, running the command `/challenge/run` will give you the flag.

code:
```
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ echo Look: file_[bash]
Look: file_a file_b file_h file_s
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[bash]
You got it! Here is your flag!
pwn.college{s0TCOgbLRGZn7Lwflxpz1c33DZr.QXzIDO0wiMwEzNzEzW}
```

## What I learnt
The challenge revolves around using the square brackets `[]` for pattern matching in filenames. Unlike `?`, which matches exactly one character, `[]` allows you to specify a range or set of characters that can match any one of them. For example, `[pwn]` will match any of the characters `p`, `w`, or `n`. This makes `[]` a more flexible tool compared to `?`, as you can precisely control which characters can appear in a given position of the filename. Understanding how to apply this concept in the context of globbing is key to solving the challenge efficiently.

## References
None used for this challenge


# Matching Paths with []
For this challenge, run `/challenge/run` from your home directory with a single argument that, after shell globbing, becomes the absolute paths to `file_b`, `file_a`, `file_s`, and `file_h` in `/challenge/files`. Thus, you must provide one bracket-globbed argument that the shell expands into the four full paths under `/challenge/files`.

## The Solve
To solve this, we use a glob pattern that matches the four specific files. You will use square brackets `[]` to specify a set of characters that can match the final character in the filenames. The pattern you choose should be able to match all the necessary files in `/challenge/files` by expanding to their absolute paths when used as an argument in the run command.

code:
```
hacker@globbing~matching-paths-with-:~$ echo /challenge/files/file_[bash]
/challenge/files/file_a /challenge/files/file_b /challenge/files/file_h /challenge/files/file_s
hacker@globbing~matching-paths-with-:~$ /challenge/run /challe
nge/files/file_[bash]
You got it! Here is your flag!
pwn.college{ErSsiVsGhCbi3Q3jrc5wY4M2PaV.QX0IDO0wiMwEzNzEzW}
```

## What I learnt 
Globbing operates per pathname component and is performed by the shell before a program is executed. Using `[]` lets you specify a range of characters that match exactly one character in that position, so a single bracket pattern can generate multiple filenames. Because you provided an absolute path with the bracket expression in the final component, the shell expands it into absolute filenames under `/challenge/files`, satisfying the requirement to pass the expanded absolute paths to `/challenge/run`.

## References
None used for this challenge


# Multiple Globs
The challenge requires you to navigate to `/challenge/files` and run `/challenge/run`, but you will need to provide a single, short glob pattern that includes two `*` wildcards. This pattern must expand to match all filenames in the directory that contain the letter `p`. Essentially, the shell will expand your small pattern into every file with `p` in its name, and those expanded file paths will be passed as arguments to `/challenge/run`.

## The Solve
Pick a compact pattern with two asterisks and the letter `p` between them so the shell will match any filename containing `p` anywhere in its name. The natural three-character choice is `*p*`; when the shell performs pathname expansion, it will replace that single argument with every filename in the current directory that includes `p`, and then `/challenge/run` will be invoked with those matched filenames.

code:
```
hacker@globbing~multiple-globs:~$ cd /challenge/files
hacker@globbing~multiple-globs:/challenge/files$ echo *p*
happy optimistic pwning splendid uplifting
hacker@globbing~multiple-globs:/challenge/files$ /challenge/run *p*
You got it! Here is your flag!
pwn.college{sVm5KUZzdDzyYaI2xjNk_P0xYwh.0lM3kjNxwiMwEzNzEzW}
```

## What I learnt
I learnt that it relies on multiple glob expansion inside a single word: a single argument may contain more than one `*` and the shell expands it before executing the command. The `*` wildcard matches any sequence of characters (except `/`), so `*p*` finds names with `p` anywhere. Globbing is performed by the shell on path components, and the result — zero, one, or many filenames — is what the receiving program actually gets.

## References
None used for this challenge


# Mixing Globs
In this challenge, we are to change into `/challenge/files` and run `/challenge/run` with a single, short glob pattern. This glob must match the filenames `challenging`, `educational`, and `pwning` when expanded by the shell. Essentially, you need to craft a glob that, when expanded, will target these specific files.

## The Solve
To solve this, you'll need to use globbing to match all three filenames within the 6-character limit. A possible solution would be using the pattern `*ing`. This works because the suffix `ing` is common to all three filenames, and the leading `*` matches any characters before it. The shell will expand `*ing` to match `challenging`, `educational`, and `pwning` when you run the `/challenge/run` command with that argument.

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

## What I learnt
I learnt that this challenge brings together multiple globbing concepts: using `*` to match any sequence of characters and narrowing the match with a specific suffix. The pattern `*ing` leverages the power of `*` to match any prefix before the `ing` suffix, which is common to all three target filenames. The shell expands this glob pattern before executing the command, and the result is passed as an argument to `/challenge/run`. Understanding how to craft short, efficient glob patterns that match specific files is crucial here.

## References
None used for this challenge


# Exclusionary Globbing
In this challenge, you're tasked with running `/challenge/run` from `/challenge/files`, but you must provide a glob pattern that matches all files in the directory except those that start with the letters `p`, `w`, or `n`. The glob should be able to exclude files starting with these letters, effectively filtering them out.

## The Solve
To solve this, you'll use the `[]` globbing feature to exclude files that start with `p`, `w`, or `n`. By using the `!` or `^` character inside the brackets, you can invert the match. For example, the pattern `file_[!pwn]*` or `file_[^pwn]*` will match all files that do not begin with `p`, `w`, or `n`. This way, when the shell expands the glob, it will pass only the filenames that don't start with those letters as arguments to `/challenge/run`.
code:
```
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [^pwn]*
You got it! Here is your flag!
pwn.college{sGdct-pUkZ1tTz94FAR5KXETGgd.QX2IDO0wiMwEzNzEzW}
```

## What I learnt
The key concept here is the use of negation in globbing with the `!` or `^` character inside square brackets `[]`. When placed as the first character in the brackets, these symbols reverse the match, meaning the glob will match any character except those listed. This allows you to filter out specific files based on their starting letters. Additionally, it's important to remember that `!` has different meanings in bash depending on context, so using `^` is a more universally compatible approach for newer versions of bash. The ability to filter out files using globbing is a powerful tool for refining file matching.

## References
None used for this challenge


# Tab Completion
You must read a flag that was placed under `/challenge` but you are prevented from typing the real filename directly because it contains trickery (hidden or unusual characters). The directory listing shows a name that looks like `pwncollege`, and `cat` of that literal name fails; instead you are required to use your shell’s tab-completion to expand an abbreviated prefix into the actual filename so you can `cat` it and see the flag.

## The Solve
Change nothing about the file system — instead type a short unambiguous prefix of the name (for example `pwn`) and press the Tab key. The shell’s completion mechanism will query the filesystem and insert the exact filename, including any characters you cannot easily type or see. Once the name has been expanded by Tab you can run `cat` (or otherwise read the file) and the command will succeed because it now references the real filename the kernel knows about.

code:
```
hacker@globbing~tab-completion:~$ ls /challenge
DESCRIPTION.md  pwncollege​
hacker@globbing~tab-completion:~$ cat /challenge/pwncollege​ 
pwn.college{wTfbp6pxnMppN6NKLITDkpioxmW.0FN0EzNxwiMwEzNzEzW}
```

## What I learnt
This exercise demonstrates shell tab-completion (readline/programmable completion) as a safer and more reliable way to specify filenames than guessing or using wildcards. Completion uses the filesystem’s actual names, so it will reveal and insert characters that may be invisible or awkward to type (control characters, punctuation, unusual Unicode, etc.), avoiding mistakes caused by glob expansion or manual typing. It also highlights the difference between what a directory listing visually suggests and the exact string the shell must send to the kernel to open a file.

## References
None used for this challenge


# Multiple Options for Tab Completion
You need to find and read the flag that lives under `/challenge/files`, but the directory contains many filenames that share the same initial letters. The challenge requires you to use your shell’s tab-completion starting from a prefix like `/challenge/files/p` to navigate the many similarly-named entries and ultimately complete the correct filename so you can read the flag.

## The Solve
Type the path up to a reasonable prefix (for example `/challenge/files/p`) and hit Tab. Because multiple filenames match that prefix, your shell will either expand up to the common characters among all matches and then stop (bash’s default) or begin cycling through choices depending on configuration. If the first Tab stops at the longest unambiguous prefix, hit Tab again to list the options; inspect the list and continue typing more characters of the desired name or use additional Tab presses to complete the exact filename. Once the filename is fully expanded by completion, run the command to read the file and retrieve the flag.

code:
```
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwncollege-flag
pwn.college{oN_H_KC1kw_ji1IrYElsxakJ6Us.0lN0EzNxwiMwEzNzEzW}
```

## What I learnt
This exercise highlights how programmable completion behaves when multiple candidates exist: some shells (or bash defaults) expand only up to the shared prefix and require a second Tab to show choices, while others cycle through alternatives. Tab-completion reveals the true exact filename from the filesystem (including characters you might not want to type manually), helps avoid mistakes from wildcards, and is an interactive tool for disambiguating many similarly-named files. Understanding how your shell responds to single vs. repeated Tab presses is essential for efficiently locating and completing the correct target.

## References
None used for this challenge


# Multiple Options on Command
The task is to invoke a hidden program whose name begins with `pwncollege` by using your shell’s command-name tab-completion. The program will print the flag when executed, but you’re not expected to type the whole command name by hand — you should rely on the shell to auto-complete the command for you.

## The Solve
Start typing the beginning of the program name (`pwncollege`) at the shell prompt and press the Tab key. The shell’s completion system will fill in the rest of the command name; once the name is completed, hit Enter to run it and read the flag. 

Type `pwncollege` and press tab to autofill the command, and press enter to get the flag
code:
```
hacker@globbing~tab-completion-on-commands:~$ pwncollege-8310 
Correct! Here is your flag:
pwn.college{omvdNFY-pb7ZUfrcRspEW-EvgQE.0VN0EzNxwiMwEzNzEzW}
```

## What I learnt
Tab completion works for more than filenames: the shell also completes command names using entries found in the PATH. Completion reduces typing and prevents errors by inserting the exact executable name the system will call. 

## References
None used for this challenge
