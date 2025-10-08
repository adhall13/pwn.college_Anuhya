# Listing Processes
code:
```
hacker@processes~listing-processes:~$ ps auxww | grep challenge
root         132  0.0  0.0   4132  2560 ?        S    12:33   0:00 /challenge/22574-run-22164
hacker       212  0.0  0.0 230696  2560 pts/0    S+   12:42   0:00 grep --color=auto challenge
hacker@processes~listing-processes:~$ /challenge/22574-run-22164
Yahaha, you found me! Here is your flag:
pwn.college{ghZgG6FX7l8C3RX0NWKBR4_p4Li.QX4MDO0wiMwEzNzEzW}
```


# Killing Processes
code:
```
hacker@processes~killing-processes:~$ ps -eo pid,user,cmd | grep dont_run
    136 hacker   /challenge/dont_run
    163 hacker   grep --color=auto dont_run
hacker@processes~killing-processes:~$ kill 136
hacker@processes~killing-processes:~$ ps -eo pid,user,cmd | grep dont_run
    165 hacker   grep --color=auto dont_run
hacker@processes~killing-processes:~$ pgrep -a -f dont_run
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{0Ar9cYilHsFfHmeY5hTdxL1pDkl.QXyQDO0wiMwEzNzEzW}
```


# Interrupting Processes 
code:
```
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember, 
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{wj5oaLoIKalHDuoKpYsu0RnDYH_.QXzQDO0wiMwEzNzEzW}
```


# Killing Misbehaving Processes
code:
```

```


# 
code:
```

```


# 
code:
```

```


# 
code:
```

```


# 
code:
```

```


# 
code:
```

```
