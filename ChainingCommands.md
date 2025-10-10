# Chaining with Semicolons 
code:
```
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{AVp4pM4IYr0UByIQVcmtP1_CS4b.QX1UDO0wiMwEzNzEzW}
```


# Building on Success
code:
```
hacker@chaining~building-on-success:~$ /challenge/first-success && /challenge/second 
Nice chaining! Flag: pwn.college{k7GKU9c3_o53soEuM-7p5aftT0j.0lM0MDOxwiMwEzNzEzW}
```


# Handling Failure
code:
```
hacker@chaining~handling-failure:~$ /challenge/first-failure || /challenge/second
Nice chaining! Flag: pwn.college{cc4mgTBmFa5kMOiuLjuhX2kaDDq.01M0MDOxwiMwEzNzEzW}
```


# Your First Shell Script 
code:
```
hacker@chaining~your-first-shell-script:~$ echo '/challenge/pwn' > x.sh
hacker@chaining~your-first-shell-script:~$ echo '/challenge/college' >> x.sh
hacker@chaining~your-first-shell-script:~$ chmod +x x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{Qqw5I22PHbhCZwwqdQur7fAOCUE.QXxcDO0wiMwEzNzEzW}
```


# Redirecting Script Output
code:
```
hacker@chaining~redirecting-script-output:~$ echo '/challenge/pwn' > script.sh
hacker@chaining~redirecting-script-output:~$ echo '/challenge/college' >> script.sh
hacker@chaining~redirecting-script-output:~$ chmod +x script.sh
hacker@chaining~redirecting-script-output:~$ ./script.sh | /challenge/solve
./script.sh: /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/share/bashdb/bashdb-main.inc: No such file or directory
./script.sh: warning: cannot start debugger; debugging mode disabled
Correct! Here is your flag:
pwn.college{Udgm79vg4KEUooX7plqU0DPuAkz.QX4ETO0wiMwEzNzEzW}
```


# Executable Shell Scripts
code:
```
hacker@chaining~executable-shell-scripts:~$ printf '%s\n' 'exec /challenge/solve' > script.sh
hacker@chaining~executable-shell-scripts:~$ chmod +x script.sh
hacker@chaining~executable-shell-scripts:~$ ./script.sh
Congratulations on your shell script execution! Your flag:
pwn.college{EnepgrAC1cO7_rLhiMpYLRj0NGf.QX0cjM1wiMwEzNzEzW}
```


# Understanding Shebangs
code:
```
hacker@chaining~understanding-shebangs:~$ cat > /home/hacker/solve.sh <<'EOF'
> #!/bin/bash
> echo "hack the planet"
> EOF
hacker@chaining~understanding-shebangs:~$ chmod +x /home/hacker/solve.sh
hacker@chaining~understanding-shebangs:~$ /challenge/run
Testing your script...
Perfect! Your flag:
Flag: pwn.college{0l-FGOwaDpNsN3DkGRIIhDKbY4l.0VOzMDOxwiMwEzNzEzW}
```
note:
- A shebang (or hash-bang) is the character sequence #! followed by the path to an interpreter that tells the operating system which program should execute a script.
- The shebang (#!/bin/bash) must be the very first line of the file (no blank lines or spaces before it).
- Using <<'EOF' (quoted EOF) writes the contents literally (no variable/command expansion).
- echo prints a trailing newline — that is allowed. The output must match hack the planet (lowercase) otherwise the checker may fail.

# Scripting with Arguments
code:
```
hacker@chaining~scripting-with-arguments:~$ cat > /home/hacker/solve.sh <<'EOF'
> #!/bin/bash
> echo "$2 $1"
> EOF
hacker@chaining~scripting-with-arguments:~$ chmod +x /home/hacker/solve.sh
hacker@chaining~scripting-with-arguments:~$ /home/hacker/solve.sh pwn college
college pwn
hacker@chaining~scripting-with-arguments:~$ /home/hacker/solve.sh "one two" three
three one two
hacker@chaining~scripting-with-arguments:~$ /challenge/run
Correct! Your script properly reversed the arguments.
Here's your flag:
pwn.college{Q9dDRGGXHsn7lkUqpAiLDuA2AYo.0VNzMDOxwiMwEzNzEzW}
```


# Scripting with Conditionals
code:
```
hacker@chaining~scripting-with-conditionals:~$ printf '%s\n' 'if [ "$1" = "pwn" ]' 'then' '  printf "%s\n" "college"' 'fi' > /home/hacker/solve.sh
hacker@chaining~scripting-with-conditionals:~$ chmod +x /home/hacker/solve.sh
hacker@chaining~scripting-with-conditionals:~$ /challenge/run
Correct! Your script properly handles all the conditions.
Here's your flag:
pwn.college{cRW1ys6iWD_vToNL2-smQKBLIuP.0lNzMDOxwiMwEzNzEzW}
```


# Scripting with Default Cases
code:
```
hacker@chaining~scripting-with-default-cases:~$ printf '%s\n' 'if [ "$1" = "pwn" ]' 'then' '  printf "%s\n" "college"' 'else' '  printf "%s\n" "nope"' 'fi' > /home/hacker/solve.sh
hacker@chaining~scripting-with-default-cases:~$ chmod +x /home/hacker/solve.sh
hacker@chaining~scripting-with-default-cases:~$ /challenge/run
Correct! Your script properly handles the if/else conditions.
Here's your flag:
pwn.college{oVfBP_mFC17HoD3m_h_jTDYhI5x.01NzMDOxwiMwEzNzEzW}
```


# Scripting with Multiple Conditions
code:
```
hacker@chaining~scripting-with-multiple-conditions:~$ printf '%s\n' \
'case "$1" in' \
'  hack)  printf "%s\n" "the planet" ;;' \
'  pwn)   printf "%s\n" "college" ;;' \
'  learn) printf "%s\n" "linux" ;;' \
'  *)     printf "%s\n" "unknown" ;;' \
'esac' > /home/hacker/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ chmod +x /home/hacker/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ /challenge/run
Correct! Your script properly handles all the conditions with elif.
Here's your flag:
pwn.college{EXsw2LfA9ftq1P7XfSg5mMhZUHu.0FOzMDOxwiMwEzNzEzW}
```


#  Reading Shells Scripts
code:
```
hacker@chaining~reading-shell-scripts:~$ cat /challenge/run
#!/opt/pwn.college/bash

read GUESS
if [ "$GUESS" == "hack the PLANET" ]
then
        echo "CORRECT! Your flag:"
        cat /flag
else
        echo "Read the /challenge/run file to figure out the correct password!"
fi
hacker@chaining~reading-shell-scripts:~$ grep -nE 'password|pass|SECRET|secret|flag|echo|printf|base64|rev|tr' /challenge/run || true
6:      echo "CORRECT! Your flag:"
7:      cat /flag
9:      echo "Read the /challenge/run file to figure out the correct password!"
hacker@chaining~reading-shell-scripts:~$ echo "hack the PLANET" | /challenge/run
CORRECT! Your flag:
pwn.college{0MdY2sCtbUnw3cxtTPZYX86SIvn.0lMwgDOxwiMwEzNzEzW}
```
