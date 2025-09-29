# Cat: not the pet, but the command! 
code:
```
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{kM4GGFNbFPR32lS05QbwEvwffO_.QXxcTN0wiMwEzNzEzW}
```


# Catting Absolute Paths
code:
```
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{I4kRY-pqIOMFBUDfUjjj2Z6BD45.QX5ETO0wiMwEzNzEzW}
```


# More Catting Practice
code:
```
hacker@commands~more-catting-practice:~$ cat /usr/share/fish/flag
pwn.college{YPhsT8k1JdxxetS51Y5eph4ULVW.QXwITO0wiMwEzNzEzW}
```


# Grepping for a Needle in a Haystack
code:
```
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{MY1RHI3jrsXB0UckXa37V59T0ue.QX3EDO0wiMwEzNzEzW}
```


# Comparing Files
code:
```
hacker@commands~comparing-files:~$ diff /challenge/decoys_only.txt /challenge/decoys_and_real.txt
95a96
> pwn.college{UPqT3XpPhiLYjY1EgqAMBD594Ue.01MwMDOxwiMwEzNzEzW}
```


# Listing Files
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


# Touching Files
code:
```
hacker@commands~touching-files:~$ cd /tmp
hacker@commands~touching-files:/tmp$ touch pwn
hacker@commands~touching-files:/tmp$ touch college
hacker@commands~touching-files:/tmp$ /challenge/run
Success! Here is your flag:
pwn.college{o72hQfQTeNWCUKmutHaD8AU7BdJ.QXwMDO0wiMwEzNzEzW}
```


# Removing Files
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


# Moving Files
code:
```
hacker@commands~moving-files:~$ mv /flag /tmp/hack-the-planet
Correct! Performing 'mv /flag /tmp/hack-the-planet'.
hacker@commands~moving-files:~$ /challenge/check
Congrats! You successfully moved the flag to /tmp/hack-the-planet! Here it is:
pwn.college{0bGHFf9zHkgXypx_gi1m7S50B25.0VOxEzNxwiMwEzNzEzW}
```


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
