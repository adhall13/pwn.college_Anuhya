# Changing File Ownership
code:
```
hacker@permissions~changing-file-ownership:~$ chown hacker /flag
hacker@permissions~changing-file-ownership:~$ cat /flag
pwn.college{E2L6fE4IC_m-I6S3O6oYJ73JZTL.QXxEjN0wiMwEzNzEzW}
```
note: `chown` stands for change owner

# Groups and Files
code:
```
hacker@permissions~groups-and-files:~$ chgrp hacker /flag
hacker@permissions~groups-and-files:~$ cat /flag
pwn.college{cVlBWvNtDeoHVyNWLhvcweOyQZl.QXxcjM1wiMwEzNzEzW}
```
note: `chgrp` = change group. It changes the group owner of a file.

# Fun with Group Names
code:
```
hacker@permissions~fun-with-groups-names:~$ id -gn
grp14551
hacker@permissions~fun-with-groups-names:~$ chgrp "$(id -gn)" /flag
hacker@permissions~fun-with-groups-names:~$ cat /flag
pwn.college{sFaimmSfSdk018iBCix4-oqUl0X.QXycjM1wiMwEzNzEzW}
```


# 
code:
```
hacker@permissions~fun-with-groups-names:~$ id -gn
grp14551
hacker@permissions~fun-with-groups-names:~$ chgrp "$(id -gn)" /flag
hacker@permissions~fun-with-groups-names:~$ cat /flag
pwn.college{sFaimmSfSdk018iBCix4-oqUl0X.QXycjM1wiMwEzNzEzW}
```
note: 
- `id -gn` prints the primary group name
- `id -nG` prints all group names
- `chgrp group /flag` changes the group


# Changing Permissions
code:
```
hacker@permissions~changing-permissions:~$ chmod o+r /flag
hacker@permissions~changing-permissions:~$ cat /flag
pwn.college{AhNpUxAUSmW75nBK8eV2NA0b1Ku.QXzcjM1wiMwEzNzEzW}
```
note:
change file modes with `chmod` (stands for change mode)
u+r, as above, adds read access to the user's permissions
g+wx, adds write and execute access to the group's permissions
o-w, removes write access for other users
a-rwx, removes all permissions for the user, group, and world


# Executable Files
code:
```
hacker@permissions~executable-files:~$ ls -l /challenge/run
-r--r--r-x 1 hacker hacker 32 Jan 14  2025 /challenge/run
hacker@permissions~executable-files:~$ chmod a+x /challenge/run
hacker@permissions~executable-files:~$ ls -l /challenge/run
-r-xr-xr-x 1 hacker hacker 32 Jan 14  2025 /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
Successful execution! Here is your flag:
pwn.college{EJuFo_SXfladvAwelgXBJEGRbOA.QXyEjN0wiMwEzNzEzW}
```


# Permission Tweaking Practice
code:
```

```


# Permission Setting Practice
code:
```

```


# The SUID Bit
code:
```

```
