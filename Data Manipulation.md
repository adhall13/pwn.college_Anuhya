# Translating Characters
The challenge requires to use a command-line utility to undo case swapping to reveal the correct flag.

## The Solve
code:
```
hacker@data~translating-characters:~$ /challenge/run | tr 'A-Za-z' 'a-zA-Z'
yOUR CASE-SWAPPED FLAG:
pwn.college{4Gtyft5wFlAytfR2Q9W12N8soUA.01MxEzNxwiMwEzNzEzW}
```

## What I learnt 
This challenge teaches the fundamental use of the `tr` command, short for translate or delete characters. I learned how to use `tr` with a range of characters (like a-z and A-Z) to perform a one-to-one character substitution, effectively demonstrating its power in quickly transforming streamed data according to a specific translation set.

## References
None used for this challenge


# Deleting Characters
The challenge requires to get output, but the output is polluted with decoy characters mixed aamong the real flag characters. You must use a command to filter out and permanently delete these distracting characters from the data stream before the flag can be read clearly.

## The Solve
code:
```
hacker@data~deleting-characters:~$ /challenge/run
Your character-stuffed flag:
p%w^%n^%.%c^%o^%l^%le%g^%e^%{^%s%v^%s%Z^%A^%L^N%d^e^u^6^%2%B^%J^%Eg^%O^Lx%s^b%n%5%P^%4%rN^%.^0^%F%Nx^E^%z^%N%x^%wi^M^%w^E%z^N^%z^%Ez^%W%}^%%
hacker@data~deleting-characters:~$ /challenge/run | tr -d '^%'
Your character-stuffed flag:
pwn.college{svsZALNdeu62BJEgOLxsbn5P4rN.0FNxEzNxwiMwEzNzEzW}
```

## What I learnt 
I learned the second major function of the `tr` command, which is character deletion using the `-d` flag. This is a critical skill for data sanitization, proving that pipes and filters can be used to clean up or extract targeted information from noisy or poorly formatted inputs, a common task in scripting and security.

## References
None used for this challenge


# Deleting Newlines

code:
```
hacker@data~deleting-newlines:~$ /challenge/run | tr -d '\n'
Your line-split flag: pwn.college{Unybw9_jIEdjGGCx6kxbYoIICVG.0VNxEzNxwiMwEzNzEzW}
```

## What I learnt 


## References
None used for this challenge


# Extracting the First Lines with Head
code:
```
hacker@data~extracting-the-first-lines-with-head:~$ /challenge/pwn | head -n 7 | /challenge/college
Congratulations, you piped the right codes!
pwn.college{MLZulJ-UAIheGtGe-kINPSLi6xR.0lNxEzNxwiMwEzNzEzW}
```

## What I learnt 


## References
None used for this challenge


# Extracting Specific Sections of Text
code:
```
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run | cut -d ' ' -f 2 | tr -d '\n'
pwn.college{cAsXA-oXxEN4kbNdyzCxNadlf7J.01NxEzNxwiMwEzNzEzW}
```

## What I learnt 


## References
None used for this challenge


# Sorting Data
code:
```
hacker@data~sorting-data:~$ sort /challenge/flags.txt | tail -n 1
pwn.college{Eb6IFXS4cUMdvGQUgYbWClxwYUi.0FM0MDOxwiMwEzNzEzW}
```

## What I learnt 


## References
None used for this challenge
