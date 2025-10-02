# Cat: not the pet, but the command! 
For this challenge, a flag file is located in the home directory and read that file using the `cat` command.

## The Solve
Run cat on the flag file in your home directory, simply `cat flag`. The command will print the file’s contents (the flag) to your terminal, provided you have read permission.

code:
```
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{kM4GGFNbFPR32lS05QbwEvwffO_.QXxcTN0wiMwEzNzEzW}
```

## What I learnt
I learnt that `cat` reads and outputs file contents and can concatenate multiple files when given multiple arguments. If no arguments are supplied, `cat` reads from standard input. The shell’s home directory can be referenced by `~` or `$HOME`, and file permissions determine whether `cat` can read the file.

## References
None used for this challenge


# Catting Absolute Paths
The challenge is asking you to read the hidden flag file that lives at an absolute path (`/flag`) 

## The Solve
To solve the challenge, we run a command that reads the absolute path `/flag` —for example, `cat /flag` —instead of relying on a file named flag in the current directory. The DESCRIPTION already tells us `/flag` is readable, so supplying the absolute path as an argument to a file-reading utility like `cat`

code:
```
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{I4kRY-pqIOMFBUDfUjjj2Z6BD45.QX5ETO0wiMwEzNzEzW}
```

## What I learnt
In this challenge, I learned the difference between absolute and relative paths. I realized that a file called `flag` in my home directory is completely different from `/flag`, which is located at the root of the system. I also learned how file permissions work—if a file is marked as readable, I can access it as long as I know the correct path. More importantly, I saw how CTF challenges often restrict access to files, so I have to think carefully about where things are located. This challenge also reminded me to always read the description closely, because it can contain important hints to solve the task.

## References
None used for this challenge


# More Catting Practice
This challenge asks to read a `flag` that’s hidden somewhere in the filesystem by using its absolute path without using `cd` 

## The Solve
Solve it by trying commands that accept absolute paths using cat until I reference the correct location the challenge creator placed the flag; since cd is disabled, I must supply the full path to a reading tool like cat to display the file.

code:
```
hacker@commands~more-catting-practice:~$ cat /usr/share/fish/flag
pwn.college{YPhsT8k1JdxxetS51Y5eph4ULVW.QXwITO0wiMwEzNzEzW}
```

## The Solve
I learned the practical difference between absolute and relative paths. 
An absolute path tells you exactly where a file or folder is on the system, starting from the root directory (`/`). This path will work no matter where you are in the system because it starts from the top.
A relative path tells you where a file is in relation to your current working directory. This only works if you’re already in /home/user/.
It explains why absolute paths let me access files without changing directories, how file permissions determine whether I can read a file. 

## References
None used for this challenge


# Grepping for a Needle in a Haystack
The challenge asks to search a very large file (/challenge/data.txt) for the hidden flag.

## The Solve 
I solved it by running `grep pwn.college /challenge/data.txt` to scan the file for lines that contain that prefix. Because the file is large, grep quickly finds and prints only the matching lines.

code:
```
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{MY1RHI3jrsXB0UckXa37V59T0ue.QX3EDO0wiMwEzNzEzW}
```

## What I learnt
I learned when and why to use grep instead of cat for large files: grep filters lines by pattern, saving time and output. I reinforced the idea of using absolute paths to target files I can’t `cd` into, and I practiced simple pattern matching. I also learned a few useful grep options (like -n for line numbers and -m to limit matches) that make searching large files more efficient.

## References
None used for this challenge


# Comparing Files
Compare `/challenge/decoys_only.txt` (100 fake flags) with `/challenge/decoys_and_real.txt` (those 100 plus one real flag).
Extract the single line that's in the second file but not the first — that's the real flag.

## The Solve
Solve it by using `diff` to compare the two files and show the differences. The output will show which lines were added, removed, or changed; the real flag will appear as the line present in the second file but not the first. 

code:
```
hacker@commands~comparing-files:~$ diff /challenge/decoys_only.txt /challenge/decoys_and_real.txt
95a96
> pwn.college{UPqT3XpPhiLYjY1EgqAMBD594Ue.01MwMDOxwiMwEzNzEzW}
```

## What I learnt
I learned that `diff` compares files line by line and how to interpret its output, using symbols like `<` to show lines found only in the first file, and `>` for lines found only in the second file. It also uses notations like `2c2` to indicate a line was changed, or `1a2` to show where a new line was added in the second file, making it easier to understand exactly what was modified.

## References
None used for this challenge


# Listing Files
The challenge asks to find the randomly named executable placed in `/challenge`

## The Solve
Run `ls /challenge` to see the directory contents — in this case, it prints `12125-renamed-run-15514 DESCRIPTION.md`. List the specific file with `ls /challenge/12125-renamed-run-15514` to confirm its presence, then execute it by running `/challenge/12125-renamed-run-15514`

code:
```
hacker@commands~listing-files:~$ ls /challenge
12125-renamed-run-15514  DESCRIPTION.md
hacker@commands~listing-files:~$ ls /challenge/12125-renamed-r
un-15514
/challenge/12125-renamed-run-15514
hacker@commands~listing-files:~$ /challenge/12125-renamed-run-15514
Yahaha, you found me! Here is your flag:
pwn.college{o3nQrlk1--G6kZHpGOV4K-c-y7T.QX4IDO0wiMwEzNzEzW}
```

## What I learnt
This exercise teaches basic filesystem navigation and how the `ls` command works. By default, `ls` lists files in the current directory, but if you give it a path, it shows the contents of that path instead. You also learn how command arguments change what `ls` does, and how to explore directories without needing to know exact filenames. Two helpful options are `-l`, which shows detailed file info like permissions and size, and `-a`, which includes hidden files. Overall, the challenge encourages exploring the filesystem methodically — a key skill for working in the shell and solving problems.

## References
None used for this challenge


# Touching Files
For this challenge create two files: /tmp/pwn and /tmp/college, and run /challenge/run to get the flag. 

## The Solve
To solve this level, we create two empty files at the exact paths `/tmp/pwn` and `/tmp/college` and then run the provided validator. The quickest way is `touch /tmp/pwn /tmp/college` which creates the files if they don’t already exist; alternatives include shell redirection (`> /tmp/pwn` and `> /tmp/college`), `echo -n "" > /tmp/pwn`, or `dd if=/dev/null of=/tmp/college`. After creating the files, run `/challenge/run` from the shell to trigger the checker and receive the flag. If anything fails, verify `/tmp` is writable with `ls -ld /tmp`, check file existence and metadata with `ls -l /tmp/pwn /tmp/college` or `stat`, and report any error output from `/challenge/run` for further debugging.

code:
```
hacker@commands~touching-files:~$ cd /tmp
hacker@commands~touching-files:/tmp$ touch pwn
hacker@commands~touching-files:/tmp$ touch college
hacker@commands~touching-files:/tmp$ /challenge/run
Success! Here is your flag:
pwn.college{o72hQfQTeNWCUKmutHaD8AU7BdJ.QXwMDO0wiMwEzNzEzW}
```

## What I learnt 
This exercise teaches how to create empty files using `touch` and shell redirection, where temporary files are typically placed (`/tmp`), and how to verify file existence, permissions, and ownership (`ls -l`, `stat`). It also highlights troubleshooting steps when a command fails (checking write permissions, file paths, and error messages) and shows that many small utilities (`touch`, `echo`, `dd`) can accomplish the same result—useful for scripting and automation in shell environments.

## References
None used for this challenge


# Removing Files
For this challenge, the challenge will create a delete_me file in the home directory. Delete it, then run `/challenge/check`, which will make sure you've deleted it and then give the flag.

# The Solve
Change to your home directory or reference it directly, remove the `delete_me` file, then run the validator. For example: `ls -la` to confirm the file exists, then `rm delete_me`. After the file is removed, run `/challenge/check` to let the challenge verify the deletion and return the flag. 

code:
```
hacker@commands~removing-files:~$ touch delete_me
hacker@commands~removing-files:~$ ls
delete_me  f  test
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{IsnGIkXzQBr3TJVNGkDntBsvktq.QX2kDM1wiMwEzNzEzW}
```

## What I learnt
This exercise teaches basic file deletion with `rm` and the importance of verifying file locations before removing them. Using `ls` and `pwd` to inspect directories, we learn that `rm` permanently removes files, and get introduced to common troubleshooting steps like checking file permissions (`ls -l` or `stat`) when a removal fails. It also reinforces the workflow of performing an action in the shell and then running a validator (`/challenge/check`) to confirm the expected state.

## References
None used for this challenge


# Moving Files
For this challenge we are to move the `/flag` file into `/tmp/hack-the-planet` and use `run /challenge/check` to check

# The Solve
To solve this challenge, start by making sure the destination directory exists using `mkdir -p /tmp/hack-the-planet`. After that, move the file using the `mv /flag /tmp/hack-the-planet/` command. You can confirm the file was successfully moved by checking the contents of the destination directory with `ls -l /tmp/hack-the-planet`. Finally, run the `/challenge/check` command to verify that the file has been moved correctly and receive your flag.

code:
```
hacker@commands~moving-files:~$ mv /flag /tmp/hack-the-planet
Correct! Performing 'mv /flag /tmp/hack-the-planet'.
hacker@commands~moving-files:~$ /challenge/check
Congrats! You successfully moved the flag to /tmp/hack-the-planet! Here it is:
pwn.college{0bGHFf9zHkgXypx_gi1m7S50B25.0VOxEzNxwiMwEzNzEzW}
```

# What I learnt
This challenge teaches how the `mv` command is used not only to rename files but also to move them between directories. It also emphasises the importance of ensuring the destination directory exists, which can be done with `mkdir -p` to avoid errors. The exercise encourages verification of the operation using `ls` to check the file's new location, and `cat` to inspect the file contents if required. 

## References
None used for this challenge


# Hidden Files

code:
```
hacker@commands~hidden-files:~$ cd /
hacker@commands~hidden-files:/$ ls
bin        dev   lib    libx32  nix   root  srv  usr
boot       etc   lib32  media   opt   run   sys  var
challenge  home  lib64  mnt     proc  sbin  tmp
hacker@commands~hidden-files:/$ ls -a
.                     bin        etc    lib64   nix   run   tmp
..                    boot       home   libx32  opt   sbin  usr
.dockerenv            challenge  lib    media   proc  srv   var
.flag-37861233524415  dev        lib32  mnt     root  sys
hacker@commands~hidden-files:/$ cat .flag-37861233524415
pwn.college{0UkVPqA-mTukATHib-2eQl8ZFiB.QXwUDO0wiMwEzNzEzW}
```


# An Epic Filesystem Quest
code:
```

```


# Making Directories
code:
```
hacker@commands~making-directories:~$ cd /tmp
hacker@commands~making-directories:/tmp$ ls
bin  hsperfdata_root  tmp.4mK6TfTSUV
hacker@commands~making-directories:/tmp$ mkdir pwn
hacker@commands~making-directories:/tmp$ ls
bin  hsperfdata_root  pwn  tmp.4mK6TfTSUV
hacker@commands~making-directories:/tmp$ cd pwn
hacker@commands~making-directories:/tmp/pwn$ touch college
hacker@commands~making-directories:/tmp/pwn$ ls
college
hacker@commands~making-directories:/tmp/pwn$ /challenge/run
Success! Here is your flag:
pwn.college{Eup8vq7tOERujElr0QdOuOHnXAd.QXxMDO0wiMwEzNzEzW}
```


# Making Directories
code:
```
hacker@commands~finding-files:~$ find /usr -name flag
/usr/local/lib/python3.8/dist-packages/pwnlib/flag
/usr/share/man/nl/man8/flag
hacker@commands~finding-files:~$ cat /usr/local/lib/python3.8/dist-packages/pwnlib/flag
cat: /usr/local/lib/python3.8/dist-packages/pwnlib/flag: Is a directory
hacker@commands~finding-files:~$ cat /usr/share/man/nl/man8/flag
pwn.college{InMv3xB2e6-tufH6cDyXReeqeO2.QXyMDO0wiMwEzNzEzW}
```
find / -name flag to search for flag in home directory but all the directories' permission is denied.
find /tmp -name flag and find /challenge -name flag also give permission denied.
find /usr -name flag gives 2 directories. (tmp,challenge and usr directories are checked as they were mentioned previously too)
cat /usr/local/lib/python3.8/dist-packages/pwnlib/flag doesnt give the flag.
cat /usr/share/doc/libdrm-amdgpu1/flag gives the flag.
/usr/local/lib/python3.8/dist-packages/pwnlib/flag
/usr/share/man/nl/man8/flag


# Linking Files
code:
```
hacker@commands~linking-files:~$ ln -s /flag /home/hacker/not-the-flag
hacker@commands~linking-files:~$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!
pwn.college{QV9VNh2rhdEfKh6MnvvCQ-eJFKc.QX5ETN1wiMwEzNzEzW} 
```
## Reference
https://www.youtube.com/watch?v=m55AtwjBXpE&list=PL-ymxv0nOtqqRAz1x90vxNbhmSkeYxHVC
