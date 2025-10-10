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
hacker@processes~killing-misbehaving-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 20:11 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/bin/sleep 6h
root           7       1  0 20:11 ?        00:00:00 /run/dojo/bin/sleep 6h
root         137       1  0 20:11 ?        00:00:00 /bin/bash /challenge/.init
root         138       1  0 20:11 ?        00:00:00 /bin/bash /challenge/.init
root         139       1  0 20:11 ?        00:00:00 su -c exec /challenge/decoy > /tmp/flag_fifo hacker
root         140     138  0 20:11 ?        00:00:00 sleep 6h
root         141     137  0 20:11 ?        00:00:00 sleep 6h
hacker       142     139  0 20:11 ?        00:00:00 /usr/bin/python /challenge/decoy
hacker       153       1  0 20:11 ?        00:00:00 /nix/store/g0q8n7xfjp7znj41hcgrq893a9m0i474-ttyd-1.7.7/bin/ttyd --port 7681 --interface 0.0.0.
hacker       157     153  0 20:11 pts/0    00:00:00 /run/dojo/bin/bash --login
hacker       167     157  0 20:12 pts/0    00:00:00 ps -ef
hacker@processes~killing-misbehaving-processes:~$  kill 142
hacker@processes~killing-misbehaving-processes:~$ /challenge/run
Sending the flag to /tmp/flag_fifo!
-------------------------------------------------------------------------------------------------------------------------------------------------------------------
hacker@processes~killing-misbehaving-processes:~$  cat /tmp/flag_fifo
pwn.college{hz9CJ--YOZUvGnBCjh8zjTet9k4jSQJk21dPQ3XKl-jUuaZ}
pwn.college{1iJFejqjybV4Nx3fnE4JLOEXUF2kTsH7SSxwVxSU8a6rF-F}
pwn.college{X4HN38ecj20ZTL8E0hyrEVhT-ImeIusSCL2pFnrWWGbw-Zz}
pwn.college{wvYOURDT3iGEHtQ0eAlLvpupkrQzJlfAnVYCFqrClKUmv3E}
pwn.college{jH8NTBzQR0QVLoSV.3DMf3co-gb-DmNrI8y5MwxXklIlwGu}
pwn.college{kEx1.QZ2Nz6qRuE439.MmsiEMGB30uR7HI2bCL1RPmpnqHW}
pwn.college{E.hggrH6AE4GoMfva8WSdBOHRIlw3kMB.b.skwN8vpbf2mn}
pwn.college{Tik7F94pQpWLiOdL9Ii7HEKwTdC9BeuxNiAFXIhJnQsU2zd}
pwn.college{Rldf94nmWo7AU.VfSSv3N87foa6NKMAMWPo59V29Po7-vjZ}
pwn.college{Sd2FpdhPxkQX.ipeKkUAk9lcbeEjFdZ67kGvzrfYmo.tBQ3}
pwn.college{hSfk-YP4kWFPiw-QvpEuJah2zCm5JU.e7vTKHX7wIPwNFs6}
pwn.college{wkWE4OnWDh8LEOhBS1HXO4SNFKOLNHLtz8YswxWWok5l15J}
pwn.college{W7BYvVYtN7iFVc-7rqc-atj-v0HxCqtLOjkPfndBUEnbOt.}
pwn.college{Us4iYeRHdEk.DT2G1GfrhEYT0wC8fbaFyU9USLLmF4BUgq9}
pwn.college{C3LjSBitEzv.RPnLPp6MlV3V-c-9Y9Dtj9pdjVc94xsQl9j}
pwn.college{9WVXnYTLBN7HKx71edwMqSvE9zlZSj05xQIp0U6TRSBXpew}
pwn.college{rgxVGfZLVKVozj94AYkQVh.QOjA8TD8FNLEPECTwmMzLXQq}
pwn.college{8FLdWdPZGI6kwsMaNMaK7pUpGuUItfSRLys5WAmbco3bC8d}
pwn.college{vAEBwptOwUmabBsUuPjOH8nEmnugQ2JmOSSZTJ0vVL6S5fe}
pwn.college{cVQDBUuOBx1mjZP54de0Gt.awsHEKh9Iu-53j2ZWKTKKhRh}
pwn.college{rKiDlrBHqOUdh2QfuzqXR-Ij2waIL.-OgSEeOdiLKHohIc8}
pwn.college{5NpZ7uI.QfSAflXaWQ2IjrB7sJzaq1XqGyrgdokP.J3aZt6}
pwn.college{5bOU7YgJWyAtO7JK3OkR5KM0-KWp3399kBR3ozrMtsTqzke}
pwn.college{f0q4cji2ZqSO5bEYDEjA9OkcaaRllhAydg2y51dBuSojxzi}
pwn.college{yvNADk51LvQ2VS80Z2QmMkiEu5nlu1B3z.l5wxXihWEtIVi}
pwn.college{mp9lns.s6ysOvkM40Md.dDZz88dKl3omaqSmMRxr2pq2Vz2}
pwn.college{MVlAcSMWxdX2eRh4rs5fqMaPOSxYIaIAeX2cPj95fXoujJY}
pwn.college{FEoyYeBCDVWt9Mfj.LYmwWEQLsJRnZWQZmVxdNRSzCvvdZD}
pwn.college{KyBafVy5Vm.m-dxC1iqV3QRLVxDiqJFguE5CK6eL7hKuEkj}
pwn.college{J-YvUi.Ehh4X5WTscwf6-O-RZyNc67YSrZGU6xxVETRsq8Y}
pwn.college{LRqp9Y2bP53mE7nslsb3YutHxeHbbJuJinXhnWm2pYSS06L}
pwn.college{GG62YNg3P9uBHE51T8oUk7D1P-rkT693fziaIMSBP8MdFEJ}
pwn.college{S2gGgX5L3krvLUmlWeqD4XdN1A0zVRHu5xTi8bENBQYR--H}
pwn.college{su0ty1a97RxlDGAB7QBbCwKJZoLnPhluulxNxJ54wyQtL8H}
pwn.college{dhTvU6V3oJNADwvK0Zp5wnRopWJtIZwKGiOy6zGmgEd6S2j}
pwn.college{gXzBFsPOUGN-LG5OYWeZu7qZwtavKJHtGbuKTPpApjyN3fw}
pwn.college{agRi7E2w-d6Ig0azJ7EoDPayzpE5A51u9PBAXUq1tnPqcIV}
pwn.college{sJfn4-TTaG3UB6tz0HBsIZh6Gcl07TnObGoFQOYJF8icqcG}
pwn.college{6g-ES9CIxkRYy.LUmbuKkf3nwra6KaUyJ-EpdVOUg3N4D0C}
pwn.college{GrsTlUDp9BTVLf9S15S4i-KJX0jHDwZjS6613LY2jE7hl8X}
pwn.college{fAncfTdkA9U7QJpTbfJO00DgNXgpqt2lbMAhi2o9nVvi-5h}
pwn.college{reQgOEMxp8cDziBjRb.RLlKp4oHlfgm9r.WSm2dmYPwcA59}
pwn.college{BHoKaqGJ1ZcLfx.BQjCDPfXDqZhgJQ4cdgX0AD8Oiu10hwp}
pwn.college{NAMEaJqulRB4rFdQJkh7zMY41RExaKb189-ZjZT2xHlURG9}
pwn.college{idtDyDgsu86RYquYI7AXFTqNUYGH9n9MS1S1IaPLpxmtWPc}
pwn.college{FsbDbaInFMyGNbu466WqmS2zFXTo04-sHXXZTQoEDOKz9V-}
pwn.college{Ieu1kBFpUMbcR3BrceZoJgoHIBe3tiFjUhqrwcyHtXPtXX7}
pwn.college{QMjgGiYWGa7bO2KZc2JQoNiW2I.Rp3WyRsfQ.SZSAKTih5P}
pwn.college{n1Rmd.uvGf3H-EkFj9WFAfRJr54y0icCPsqG0v0RzNvCv6F}
pwn.college{xCQLhaj.olK2H0gT3HHh9OEcd9d0vn9LxXRqM86lRC1Qn1x}
pwn.college{hufPGz6RuPJXdt6v6wxM4IghYJCv4b3T-i.87W7MQNf3.Be}
pwn.college{LgtAFMAzLK5-bUMfxw-xpo-Qajf4Bem5pFLOtYVgcDZb1US}
pwn.college{02nCfJWCDJTZge4Vh6F.9W2Uky7xt1IPUU60iaGPz4uQwud}
pwn.college{fxIWF16O3lCzNF8fjFtEpJx35ExYSKHS1nVOlAit.q0kHCx}
pwn.college{jjV1C8fn.TioxqMb8iejK67epoKLgMd4siyBgQpQf9LjVy1}
pwn.college{lneUZuDOFDy9NogsA445q-BzZdjuGcGVUuOQziyvgn9lS1N}
pwn.college{fEk3ysAn-kygCVQEWWih89lkmJLZTI.M-DBABXr1gbH2ALz}
pwn.college{72dngdGaMe7.5OQ7vsdMP.UrQI-w3drgHnuNNx80b-nFUD5}
pwn.college{wdRqXvB7as6NCCgPmp82d4TCGc6viqYdgCS51c2S5N9NgZi}
pwn.college{cpOOVtucvSTVqrXed8ayb4AYzEEqjNMnvkodRcQGVGCLTj7}
pwn.college{XLSdDygQzq40FHR-24f1WgZ6yI3HfoqBKy7ZBmm30dHrnr-}
pwn.college{HMlVWI0yoKThyAj.UmK2y2s-FwD9A0qNWkzl8c6x7y2fwUx}
pwn.college{TeKx811pgifTVEksTfTxBqCdCKyMUHEhRZ.DlL7iWTLOGNP}
pwn.college{qxzySE2e3l6qHJ5FWj0GCGgD9Da1UmRDVOamPge-u4ls4yA}
pwn.college{8oCkLY-sQ7upUphoCHEFTS0MBVjZNbB2KZK9ioi4G0cJm8C}
pwn.college{OuYflqijU0zLaWjf1y1J1O.WSTd3ttnjsmeXmP7sZIx4Mij}
pwn.college{FWb-Si0Ck8pMmgVzMZc0Ar2KezHjgJT.ULzIRaVcLHMmfmJ}
pwn.college{BSNZrH9NZqi2MUCoXAW3WtVr5nDI7goFqJKstDzm62ysRN-}
pwn.college{6q-MSznZqGOaZ6nahMZe4sl882pHL27guUsSCzoCPYIYnVD}
pwn.college{Ks9QVMtiVKcqd5R3kT9hdzS.CBEvuqHYso-9pylRBkNHB0A}
pwn.college{bI1dW-AmPFM.myX9iy0jDuv5c1XLu4lB494p9aF92CMQcNO}
pwn.college{QtIR9oEOXbkkWWs0OYL6Ke7OgUgTYeHTpo-7C44VEViwMs1}
pwn.college{aT3S-FtkCLLHwyyUKK8lrsxhmO4RsDsznc.GefMfTHU6QTK}
pwn.college{BRVIJpeSpvgiqqsPJUPnl0aRi9G8lBHZ-udE-FQZk2MxwVv}
pwn.college{JrmmR5kUStT1ObnHwws3ysQ7jEaoPR5lutiB2mY103hs3mp}
pwn.college{wmJr7oo13NDC6whLj.-fgliP99aHUeoOyoEnmL5.7VyTVlX}
pwn.college{5Ni0AuVxIQem17EfqKoRWVdoIVjf.CpRJQE.QFQkLMYJ1IW}
pwn.college{8UC3gcyfNkzTwnJRskjGuf99chUk3VoIF4lfRSa2eym5akz}
pwn.college{8GmljCnc9jrKrk1IE47Sf6nNHpIAStOVRvxcLr7ox8OqAFs}
pwn.college{at-IT5rI0QFplomcbi5xKI13BWsK1VYkw8emjbLOfZ3jhzz}
pwn.college{H0sOT5TiIrjMNk6toQmIddliG5c2PoLzzLZXjy8oOvKZcd2}
pwn.college{4EDjRQT0RQRsYNEGZP2lu3vo4mUmumlE5X1NEW2vZfXCY-C}
pwn.college{hMX1Fpv-e.jhlG7sHf8YLDX-Bif8OCfVX5Bj75QUfA1u4Au}
pwn.college{vMZnJAJrbMcbEYbcK.-lDRLdXqbHHuLXqQimoifh7nmnSc-}
pwn.college{qrExOsYYiCNwzyOprTdzgLcRz-nmbCnVhIjTH3QIfrtpaf9}
pwn.college{94VOO2d9BLeqmChxeT82AZxGhVdEPhWgVqrSaDhonqPVbp8}
pwn.college{hjDHUWTmZzSXIZ0WCyJLvVbUSAVu1I8s8K5SnLlY5KZEpd-}
pwn.college{rSZJ8fLzIv5uUf9nFY.7PbiB1Lz1-DwDRS4MrC5REuXVcnq}
pwn.college{3ndtjvbct3HZnVXjv1CKSDL6d.wLMEnkrYsvFMPu3tlGFJt}
pwn.college{cLghZ4dNqtvMeiVcnqm04AC3PTfTi.yD42R5iopumcdW7Xk}
pwn.college{BC2A6mAdVRhXB06WZKbnaLGqpGOytNsZ1E9cGEvyFIkRbwy}
pwn.college{jOTJK-fOUMlWDpF20tXjjq.V99Mw8AhrC1udmMrDK6DZ-UH}
pwn.college{6xQxxOnaPOLyeRPnf04w-tTNpzKG5TcEcwWDmjgrINFn-3Z}
pwn.college{vPGFfhfKTiK0.bd-eJvF5BCAqF5ZUNFlEUOncTddgLo7EYO}
pwn.college{34Wjs5HXsA2LTwP5YtBxTauqRNvWE3rOeUzdsnA8wGvYvoK}
pwn.college{8K9XyVrevMvMf0m5OKrgaDuHCZrqIkAdJQccff.YapeTsb1}
pwn.college{.xcc0aPmhPOsQRGTA3b24Ezx4SA.cqPQLo5RvrAeO8JzMSG}
pwn.college{yU-RU349.-ioPmLsvG0Mj.Jprqy0HOT80VxqsdgDJt9hP6p}
pwn.college{aPPUig1byWDkl-5IlHGbE0tnCzz98z9SH3M9CG9gGjAYUky}
pwn.college{xluqg4B3XyLeogheuj5xqVPed8-S5ZvBRllD4Z0sj503s6Y}
pwn.college{o0s.uwHdxIIavD2eAf12eH3G5z9zQsXzgopaHYwnKDXH8vU}
pwn.college{h88sZZy8OrWK1PkgY-HrfwV2V1YwBEMJ9wirlbdEL56sREP}
pwn.college{Z2-RJezCU2WHQOAaFLEhKgIjS2VKYBjycTfsvCJPgLlnRcg}
pwn.college{golgC8s7bcijdvYlJn23Cj6niKFxAlOnvt7jWellDdB5zZG}
pwn.college{RpI8Ndz0SkC3JuCxfDgUmQza-IyuJkEP-KNkmVRbqQTjdXv}
pwn.college{xjqWIrO195I9NDE0Pd4ek8-JaqpmZT40yG5iyi90X5oDBSg}
pwn.college{ax1D..CIOx4qypCSY0lUJamlvYCIeY4Rmk8j3FVt.SP4uxX}
pwn.college{WU3ojI2jTY2pgoC5DIW7nAXq1kH.gtbo3W-4O8E3AviHmjt}
pwn.college{FrRGN2E-KEkHOdXtKGkYSCQ0X6p5.vKOZ7HWMojOxeuLE4m}
pwn.college{K1OjSrexL.TR6OA4bIBPXHJu8n0y7yliV03nHc0AFdENVs1}
pwn.college{nyrHZugVHlN6.tnZuUM05r4DMw9yvXN1CKW5fG5UTdFIgAP}
pwn.college{Ayv-gmN6ylNfOdXKPgNZkqsDZYvCVpFSNNKHCeYjgSMoaD-}
pwn.college{7dk8.VT8QOQ8Z0rT05s7TjtwjW1nmM0k7GNC3bpGL6-5u4r}
pwn.college{OsUfOo9mxdf7MO-JlHJBesJ-I1gayG3r74ffUJL6CevfINo}
pwn.college{beuA7ov879I2You-pY8Y3zHc0Xp01VlJuMXowQ3Md.BJT3F}
pwn.college{8fayRI5evaz.im1ULDew4oKIcRJh69rsCSuZGWuz72WQVWp}
pwn.college{eYN2h0nScHM-Rh1CtfAIHas0JO9PWgiKddfmZ3IznzcXWmS}
pwn.college{4eZY73xrKuV.YGFC30Xtnc5VYxe7w1N.tHHI6tLSU20zPjf}
pwn.college{i83sDLJciRp810HFuvKP5PuEg8rxH4TFprbO8iku.hXKCta}
pwn.college{L0azICM81CZDpWBLs9MHcLV2JPLyHKFpMS4C2wCB4xPN8yE}
pwn.college{gWSdjWku5kX5Qs9kUINPWEAWXi6vd4pAZCIf3RBN7hEDw4Q}
pwn.college{OKHgMYYtt7kq6kRkUADR6npKxE53Ma0pm.TKwGZGs2Sidjb}
pwn.college{5jryJEEjanWH85Fe4CijQf91UwvI5odrOWayHzMbwGznkRz}
pwn.college{czW3c9C5BWIBSNE5yWuf64sxu1gzNkVVnOuqPBnvP1CFO.M}
pwn.college{nL7C7AeTYGEwRHcuhCSxhLP-7yFDuSCZEJvYJmSr4h2A4lk}
pwn.college{nFIj.PRiJG5C43fe65ObktLomA7sv1.EljhtGsGXt7fTvaQ}
pwn.college{8FdKzgugAvw7Rc-4H1mR-OW2cMUOz.s8ubf.nX.8QFQGkZJ}
pwn.college{ji7RVC9ya4FEx04jdYOhkYgf2X8y.4YS2eVWTfA9c3.NCds}
pwn.college{FZs2lBESSI1mZNRyfmwZladiLYIsFDXSEB.4T3R6mHRW88R}
pwn.college{4ySPPqpfzHSxO30VgMvF0-LhahvMUrJUGGriVH8GjlcaiFQ}
pwn.college{D3dERT8M0z-eqh-fg6E0ZgSvysrDsLmrGUL8Ul8lMPWWrEM}
pwn.college{ND-OALOMQkxAn.KYsPIAd4MM4s65yOUOWoQD4nAKlX0p0Su}
pwn.college{JtX4vir322d96AP4S-N1Qu4YwZqfscM3AAwFWbgxywRQTBy}
pwn.college{1B4Hmxc7z13XPUBhk-lUu8TCF315cFMJV1VhztiJL.ZGzYn}
pwn.college{0pPsnvdNKhB6s4ytyOA5k4pT0NT.0FNzMDOxwiMwEzNzEzW}
^C
hacker@processes~killing-misbehaving-processes:~$ /challenge/run
Sending the flag to /tmp/flag_fifo!
-------------------------------------------------------------------------------------------------------------------------------------------------------------------
hacker@processes~killing-misbehaving-processes:~$ cat /tmp/flag_fifo
pwn.college{0pPsnvdNKhB6s4ytyOA5k4pT0NT.0FNzMDOxwiMwEzNzEzW}
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
