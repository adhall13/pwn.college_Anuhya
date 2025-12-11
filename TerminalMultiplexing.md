# Launching Screen
code:
```
hacker@terminal-multiplexing~launching-screen:~$ screen

                                              Screen version 5.0.1 (build on 2025-05-15 15:05:07) 
Copyright (c) 2025 Alexander Naumov
Copyright (c) 2018-2024 Alexander Naumov, Amadeusz Slawinski
Copyright (c) 2015-2017 Juergen Weigert, Alexander Naumov, Amadeusz Slawinski
Copyright (c) 2010-2014 Juergen Weigert, Sadrul Habib Chowdhury
Copyright (c) 2008-2009 Juergen Weigert, Michael Schroeder, Micah Cowan, Sadrul Habib Chowdhury
Copyright (c) 1993-2007 Juergen Weigert, Michael Schroeder
Copyright (c) 1987 Oliver Laumann

This program is free software; you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the
Free Software Foundation; either version 3, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or
FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program (see the file COPYING); if not, see
https://www.gnu.org/licenses/, or contact Free Software Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02111-1301  USA.

Send bugreports, fixes, enhancements, t-shirts, money, beer & pizza to screen-devel@gnu.org

[Press Space for next page or Return to end.]

Congratulations! You're inside a screen session!
Here's your flag:
pwn.college{kKn4dXB8A6FEeDRRXDkRebdHvla.0VN4IDOxwiMwEzNzEzW}
```


# Detaching and Attaching 
code:
```
hacker@terminal-multiplexing~detaching-and-attaching:~$ screen
(Ctrl-A then type d)
hacker@terminal-multiplexing~detaching-and-attaching:~$ screen
[detached from 147.pts-0.terminal-multiplexing~detaching-and-attaching]
hacker@terminal-multiplexing~detaching-and-attaching:~$ /challenge/run
Found detached screen session: 147.pts-0.terminal-multiplexing~detaching-and-attaching
Sending flag to your screen session...

Flag sent! Now reattach to your screen session with:

  screen -r

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching:~$ screen -r
hacker@terminal-multiplexing~detaching-and-attaching:~$
hacker@terminal-multiplexing~detaching-and-attaching:~$ echo Yes! Flag is: pwn.college{cuBqGDCjeYIfkfG6-Fc6fqat9ib.0lN4IDOxwiMwEzNzEzW}
Yes! Flag is: pwn.college{cuBqGDCjeYIfkfG6-Fc6fqat9ib.0lN4IDOxwiMwEzNzEzW}
```
note: You detach by pressing Ctrl-A, followed by d (for detach). 


# Finding Sessions
code:
```
hacker@terminal-multiplexing~finding-sessions:~$ screen -ls
There are screens on:
        158.pts-0.terminal-multiplexing~launching-screen     (Remote or dead)
        147.pts-0.terminal-multiplexing~detaching-and-attaching       (Remote or dead)
        144.session_7fe440c43d312df6    (Remote or dead)
        147.session_07b83170669a95a8    (Remote or dead)
        150.session_78c3e88d7b9b3941    (Remote or dead)
        145.session_6c2c72bcabbbcb43    (Remote or dead)
        148.session_9b59daff168d2439    (Remote or dead)
        151.session_d597dd0023c250c0    (Remote or dead)
        145.session_6ef46c0f8dbdc312    (Remote or dead)
        148.session_741f09c057d764a8    (Remote or dead)
        151.session_d6e0f87054d7d5c2    (Remote or dead)
        144.session_31b74905110d038d    (Detached)
        147.session_3e2247b9d810a6cd    (Detached)
        150.session_8c8d43626738de84    (Detached)
14 Sockets in /home/hacker/.screen.
hacker@terminal-multiplexing~finding-sessions:~$ screen -r 144.session_31b74905110d038d
hacker@terminal-multiplexing~finding-sessions:~$  echo 'Congratulations! You found the right session!'
Congratulations! You found the right session!
hacker@terminal-multiplexing~finding-sessions:~$  echo pwn.college{8ajVLmfmyIxcIH9I94052PnLXpm.01N4IDOxwiMwEzNzEzW}
```


# Switching Windows
code:
```
hacker@terminal-multiplexing~switching-windows:~$ screen -ls
There are screens on:
        158.pts-0.terminal-multiplexing~launching-screen        (Remote or dead)
        147.pts-0.terminal-multiplexing~detaching-and-attaching (Remote or dead)
        144.session_7fe440c43d312df6    (Remote or dead)
        147.session_07b83170669a95a8    (Remote or dead)
        150.session_78c3e88d7b9b3941    (Remote or dead)
        145.session_6c2c72bcabbbcb43    (Remote or dead)
        148.session_9b59daff168d2439    (Remote or dead)
        151.session_d597dd0023c250c0    (Remote or dead)
        145.session_6ef46c0f8dbdc312    (Remote or dead)
        148.session_741f09c057d764a8    (Remote or dead)
        151.session_d6e0f87054d7d5c2    (Remote or dead)
        144.session_31b74905110d038d    (Remote or dead)
        147.session_3e2247b9d810a6cd    (Remote or dead)
        150.session_8c8d43626738de84    (Remote or dead)
        135.challenge_session   (Detached)
15 Sockets in /home/hacker/.screen.
hacker@terminal-multiplexing~switching-windows:~$ screen -r 135.challenge_session
 cat <<MSG
Welcome to the window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-A 0 to switch to window 0!
MSG
hacker@terminal-multiplexing~switching-windows:~$  cat <<MSG
> Welcome to the window switching challenge!
> You are currently in window 1.
> The flag is hidden in window 0.
> Use Ctrl-A 0 to switch to window 0!
> MSG
Welcome to the window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-A 0 to switch to window 0!
hacker@terminal-multiplexing~switching-windows:~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{4x3hHSI-3s8RGhBrExde2YZQFan.0FO4IDOxwiMwEzNzEzW}
> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{4x3hHSI-3s8RGhBrExde2YZQFan.0FO4IDOxwiMwEzNzEzW}
```


# Detaching and Attaching (tmux)
code:
```
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux
[detached (from session 0)]
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ /challenge/run
Found detached tmux session: 0
Sending flag to your tmux session...

Flag sent! Now reattach to your tmux session with:
  tmux attach

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux a
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$  echo Congratulations, here is your flag: pwn.college{IGOe1EdUGzohPiT7tdWN826ZA2A.0VO4IDOxwiMwEzNzEzW}
Congratulations, here is your flag: pwn.college{IGOe1EdUGzohPiT7tdWN826ZA2A.0VO4IDOxwiMwEzNzEzW}
```
flag: 
note:
Launch tmux
Detach from it.
Run /challenge/run (this will send the flag to your detached session!)
Reattach to see your prize


# Switching Windows (tmux)
code:
```
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux
[detached (from session 0)]
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ /challenge/run
Found detached tmux session: 0
Sending flag to your tmux session...

Flag sent! Now reattach to your tmux session with:
  tmux attach

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux a
```

```
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$  echo Congratulations, here is your flag: pwn.college{4b7bJVvVaWQFlxHwFS-4IVQXya1.0VO4IDOxwCM4kjNzEzW}
Congratulations, here is your flag: pwn.college{4b7bJVvVaWQFlxHwFS-4IVQXya1.0VO4IDOxwCM4kjNzEzW}
```

flag: `pwn.college{QTJW_TkvQeZwsR3-DxvrbjEr4-v.0FM5IDOxwiMwEzNzEzW} `


note:
use Ctrl-B w = This will show a window picker, allowing you to choose Window 0 and retrieve the flag

Ctrl-B c - Create a new window
Ctrl-B n - Next window
Ctrl-B p - Previous window
Ctrl-B 0 through Ctrl-B 9 - Jump to window 0-9
Ctrl-B w - See a nice window picker

Tmux shows your windows at the bottom in a status bar that looks like:

[0] 0:bash* 1:bash

The * shows your current window, and each entry also shows the process that the window was created to run.
