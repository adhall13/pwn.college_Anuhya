# INTRO TO COMMANDS
For this challenge, we must invoke the hello command to get the flag

## The Solve
Here, I executed the command, which simply prints the username (hacker) to the terminal. When the command terminates, the shell once again will display the prompt, ready for the next command. In this level, I invoked the hello command to get the flag.

code:
```
hacker@hello~intro-to-commands:~$ hello
Success! Here is your flag:
pwn.college{gZsLiKKwezyOlrMwavgNQNgx0dw.QX3YjM1wiMwEzNzEzW}
```

flag: `pwn.college{gZsLiKKwezyOlrMwavgNQNgx0dw.QX3YjM1wiMwEzNzEzW}`

## References 
None used for this challenge


# INTRO TO ARGUMENTS
For this challenge, we must invoke the hello command with a single argument of hackers to get the flag

## The Solve

code:
```
hacker@hello~intro-to-arguments:~$ hello hackers
Success! Here is your flag:
pwn.college{8MG-Ox5VbqdRqBn4B1AYAF5GMAh.QX4YjM1wiMwEzNzEzW}
```

flag: `pwn.college{8MG-Ox5VbqdRqBn4B1AYAF5GMAh.QX4YjM1wiMwEzNzEzW}`

## References 
None used for this challenge


# Command History
For this challenge, we must grab the flag injected in history.

## The Solve
Using the up and down arrow keys, I navigated through the saved commands. For this task, I obtained the flag that had been added to my history by opening a terminal, using the up arrow key, and extracting the flag.

code:
```
hacker@hello~command-history:~$ the flag is pwn.college{UA0fqGDntxXkaYZARtxdCvHsU9i.0lNzEzNxwiMwEzNzEzW}
```
flag: `pwn.college{UA0fqGDntxXkaYZARtxdCvHsU9i.0lNzEzNxwiMwEzNzEzW}`

## References 
None used for this challenge
