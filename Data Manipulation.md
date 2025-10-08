 # Translating Characters
code:
```
hacker@data~translating-characters:~$ /challenge/run | tr 'A-Za-z' 'a-zA-Z'
yOUR CASE-SWAPPED FLAG:
pwn.college{4Gtyft5wFlAytfR2Q9W12N8soUA.01MxEzNxwiMwEzNzEzW}
```


# Deleting Characters
code:
```
hacker@data~deleting-characters:~$ /challenge/run
Your character-stuffed flag:
p%w^%n^%.%c^%o^%l^%le%g^%e^%{^%s%v^%s%Z^%A^%L^N%d^e^u^6^%2%B^%J^%Eg^%O^Lx%s^b%n%5%P^%4%rN^%.^0^%F%Nx^E^%z^%N%x^%wi^M^%w^E%z^N^%z^%Ez^%W%}^%%
hacker@data~deleting-characters:~$ /challenge/run | tr -d '^%'
Your character-stuffed flag:
pwn.college{svsZALNdeu62BJEgOLxsbn5P4rN.0FNxEzNxwiMwEzNzEzW}
```


# Deleting Newlines
code:
```
hacker@data~deleting-newlines:~$ /challenge/run | tr -d '\n'
Your line-split flag: pwn.college{Unybw9_jIEdjGGCx6kxbYoIICVG.0VNxEzNxwiMwEzNzEzW}
```


# Extracting the First Lines with Head
code:
```
hacker@data~extracting-the-first-lines-with-head:~$ /challenge/pwn | head -n 7 | /challenge/college
Congratulations, you piped the right codes!
pwn.college{MLZulJ-UAIheGtGe-kINPSLi6xR.0lNxEzNxwiMwEzNzEzW}
```


# Extracting Specific Sections of Text
code:
```
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run | cut -d ' ' -f 2 | tr -d '\n'
pwn.college{cAsXA-oXxEN4kbNdyzCxNadlf7J.01NxEzNxwiMwEzNzEzW}
```


# Sorting Data
code:
```
hacker@data~sorting-data:~$ sort /challenge/flags.txt | tail -n 1
pwn.college{Eb6IFXS4cUMdvGQUgYbWClxwYUi.0FM0MDOxwiMwEzNzEzW}
```
