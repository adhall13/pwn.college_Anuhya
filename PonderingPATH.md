# The PATH Variable
code:
```
hacker@path~the-path-variable:~$ PATH="" /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{sQd8xLQHPRl7ObgmIoUqxLUC4qy.QX2cDM1wiMwEzNzEzW}
```


# Setting PATH
code:
```
hacker@path~setting-path:~$ PATH=/challenge/more_commands /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{EVuDQu_6yAkYlP-Ju4whs6AtaLy.QX1cjM1wiMwEzNzEzW}
```


# Finding Commands
code:
```
hacker@path~finding-commands:~$ which win
/challenge/paths/31503/win
hacker@path~finding-commands:~$ cat //challenge/paths/31503/win
#!/bin/bash

/bin/fold -s <<< "Search for the flag in the same directory in which I am located!"
hacker@path~finding-commands:~$ cat "$(dirname "$(which win)")/flag"
pwn.college{whFSx69K-tWuyS-l3uUe5B2JYtu.01NzEzNxwiMwEzNzEzW}
```


# Adding Commands
code:
```
hacker@path~adding-commands:~$ mkdir -p /tmp/mybin
hacker@path~adding-commands:~$ cat > /tmp/mybin/win <<'EOF'
> #!/bin/bash
> /bin/cat /flag
> EOF
hacker@path~adding-commands:~$ chmod +x /tmp/mybin/win
hacker@path~adding-commands:~$ PATH=/tmp/mybin /challenge/run
Invoking 'win'....
pwn.college{Qy3KMGvZNG5taSv5RZgJP-MufIp.QX2cjM1wiMwEzNzEzW}
```


# Hijacking Commands
code:
```

```
