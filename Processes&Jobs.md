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


# Suspending Processes
code:
```
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         146     136  0 21:44 pts/0    00:00:00 bash /challenge/run
root         148     146  0 21:44 pts/0    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can 
background me with Ctrl-Z or, if you're not ready to do that for whatever 
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         146     136  0 21:44 pts/0    00:00:00 bash /challenge/run
root         153     136  0 21:44 pts/0    00:00:00 bash /challenge/run
root         155     153  0 21:44 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{Q0maaHhDZ0nV4O7f5dcruX__To8.QX1QDO0wiMwEzNzEzW}
```


# Resuming Processes
code:
```
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with 
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg
/challenge/run
I'm back! Here's your flag:
pwn.college{U47gaowaRut60onX6L7KQoVis5K.QX2QDO0wiMwEzNzEzW}
Don't forget to press Enter to quit me!

Goodbye!
```


# Backgrounding Processes
code:
```
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         146 S+   bash /challenge/run
root         148 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the 
background, and then launch a new version of me! You can background me with 
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to 
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~backgrounding-processes:~$ 


Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out.

hacker@processes~backgrounding-processes:~$ 
hacker@processes~backgrounding-processes:~$ 

hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         146 S    bash /challenge/run
root         156 S    sleep 6h
root         157 S+   bash /challenge/run
root         159 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{04Q0au0UNfvvdSaQSVPPh3iG0QX.QX3QDO0wiMwEzNzEzW}
```


# Foregrounding Processes
code:
```
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the 
background, and *then* foreground it without re-suspending it! You can 
background me with Ctrl-Z (and resume me in the background with 'bg') or, if 
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~foregrounding-processes:~$ 


Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out. After that, resume me into the foreground with 'fg'; 
I'll wait.

hacker@processes~foregrounding-processes:~$ fg
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{w7lxoLRillNIFBVglAE1gHXQV2Y.QX4QDO0wiMwEzNzEzW}
```


# Starting Backgrounded Processes
code:
```
hacker@processes~starting-backgrounded-processes:~$ /challenge/run
You've started me in the foreground! You must start me in the background (by 
appending '&' to the command) to get the flag!
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 149
hacker@processes~starting-backgrounded-processes:~$ 


Yay, you started me in the background! Because of that, this text will probably 
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{kWBCAUwyUJP_sfP_cFiC-K388sN.QX5QDO0wiMwEzNzEzW}
```


# Process Exit Codes
code:
```
hacker@processes~process-exit-codes:~$ /challenge/get-code
Exiting with an error code!
hacker@processes~process-exit-codes:~$ echo $?
150
hacker@processes~process-exit-codes:~$ /challenge/submit-code 150
CORRECT! Here is your flag:
pwn.college{8GFUGDVlIa88Q6aOqTNuE8SquQ0.QX5YDO1wiMwEzNzEzW}
```
