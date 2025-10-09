# Becoming root with su
code:
```
hacker@users~becoming-root-with-su:~$ su
Password: 
root@users~becoming-root-with-su:/home/hacker# cat /flag
pwn.college{oUjS78eJNfSuEl46iFOZvs3kX5E.QX1UDN1wiMwEzNzEzW}
```
note: passowrd is 'hack-the-planet'

# Other users with su
code:
```
hacker@users~other-users-with-su:~$ su zardus
Password: 
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{ozdefK0_IMCPcZdeS0gHFnQDbiL.QX2UDN1wiMwEzNzEzW}
```
note: passowrd is 'dont-hack-me'


# Cracking passwords
code:
```
hacker@users~cracking-passwords:~$ cat /challenge/shadow-leak
root:*:20182:0:99999:7:::
daemon:*:20182:0:99999:7:::
bin:*:20182:0:99999:7:::
sys:*:20182:0:99999:7:::
sync:*:20182:0:99999:7:::
games:*:20182:0:99999:7:::
man:*:20182:0:99999:7:::
lp:*:20182:0:99999:7:::
mail:*:20182:0:99999:7:::
news:*:20182:0:99999:7:::
uucp:*:20182:0:99999:7:::
proxy:*:20182:0:99999:7:::
www-data:*:20182:0:99999:7:::
backup:*:20182:0:99999:7:::
list:*:20182:0:99999:7:::
irc:*:20182:0:99999:7:::
gnats:*:20182:0:99999:7:::
nobody:*:20182:0:99999:7:::
_apt:*:20182:0:99999:7:::
systemd-timesync:*:20357:0:99999:7:::
systemd-network:*:20357:0:99999:7:::
systemd-resolve:*:20357:0:99999:7:::
mysql:!:20357:0:99999:7:::
messagebus:*:20357:0:99999:7:::
sshd:*:20357:0:99999:7:::
hacker::20357:0:99999:7:::
zardus:$6$F97C0nQ6/UVkETc1$U/j40rrnVCI2QBBx7dS0u3YpTDoz60HZ4JAJvyV/ZS1iUf7pqsL5eH2gV7OMLulCnSYIakvO9awHe5s4MDKz60:20370:0:99999:7:::
hacker@users~cracking-passwords:~$  john /challenge/shadow-leak
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
0g 0:00:00:01 17% 1/3 0g/s 300.0p/s 300.0c/s 300.0C/s Zardus99999g..Zardus/
0g 0:00:00:12 0% 2/3 0g/s 288.4p/s 288.4c/s 288.4C/s kelly..snickers
aardvark         (zardus)
1g 0:00:00:20 100% 2/3 0.04904g/s 285.5p/s 285.5c/s 285.5C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$ su zardus
Password: 
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{I_-dRk3FWf7zXhdwZpcqCA5I5YK.QX3UDN1wiMwEzNzEzW}
```
note: passowrd is 'aardvark'


# Using sudo 
code:
```
hacker@users~using-sudo:~$ cat /flag
cat: /flag: Permission denied
hacker@users~using-sudo:~$ sudo cat /flag
pwn.college{086RT7bgMaQ0P3Lj7zeTTtA4hcS.QX4UDN1wiMwEzNzEzW}
```
