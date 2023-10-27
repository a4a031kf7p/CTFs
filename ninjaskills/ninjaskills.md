> a4a031kf7p | Fri Oct 27 11:41:55 AM -03 2023

# Ninja Skills

Practise your Linux skills and complete the challenges.

[Link to room](https://tryhackme.com/room/ninjaskills)

```
[new-user@ip-10-10-100-140 ~]$ find / -type f \( -name 8V2L -o -name bny0 
-o -name c4ZX -o -name D8B3 -o -name FHl1 -o -name oiMO -o -name P
FbD -o -name rmfX -o -name SRSq -o -name uqyw -o -name v2Vb -o -na
me X1Uy \) -exec ls -l {} \; 2>/dev/null
```

Certainly, let me explain the `find` command you provided step by step:

1.1 `find`: This is the command itself, used for searching files and directories.

1.2 `/`: This is the starting directory for the search. In this case, you're searching from the root directory, which means it will search the entire filesystem.

1.3 `-type f`: This option specifies that you're looking for files (not directories).

1.4 `(`: The opening parenthesis starts a group of OR conditions.

1.5 `-name 8V2L -o -name bny0 -o -name c4ZX -o -name D8B3 -o -name FHl1 -o -name oiM0 -o -name PFbD -o -name rmfX -o -name SRSq -o -name uqyw -o -name v2Vb -o -name X1Uy`: These are a series of `-name` conditions, each separated by the `-o` operator (which means "or"). This list specifies the names of the files you want to find. If any of these names match, the file will be included in the results.

1.6 `)`: The closing parenthesis ends the group of OR conditions.

1.7 `2>/dev/null`: This part redirects

standard error (stderr) to `/dev/null`, which effectively discards any error messages. It's used to suppress error messages that might occur if `find` encounters directories or files it doesn't have permission to access.

- ```\( \)``` the backslashes \ are used as escape characters. They are used to escape the following characters ( and ) which are normally special characters in the shell and could have a special meaning. By using the backslashes, you're telling the shell to treat these characters as literal parentheses rather than as part of the shell's syntax.

Here's how the ```\( and \)``` are used in your command:

- ```\( ... \)```: These pairs of escaped parentheses are used to group together multiple -name conditions. The unescaped ( and ) characters are special to the shell and are used for grouping and subshell creation. By escaping them, you tell the shell to treat them as part of the find command's syntax, specifically for grouping the OR conditions.

1.8 The `-exec` option in the `find` command allows you to perform an action on the files or directories that match the search criteria. In your case, you're using `-exec` to execute the `ls -l` command on the matched files. The `{}` is a placeholder that will be replaced by the path of each matched file.

- `-exec ls -l {} \;`: After finding each matching file, it executes the `ls -l` command on that file. The `{}` gets replaced by the path of the file, and `\;` signifies the end of the `-exec` action.

---

```
[new-user@ip-10-10-100-140 ~]$ find / -type f -group best-group \( -name 8
V2L -o -name bny0 -o -name c4ZX -o -name D8B3 -o -name FHl1 -o -na
me oiMO -o -name PFbD -o -name rmfX -o -name SRSq -o -name uqyw -o
 -name v2Vb -o -name X1Uy \) -exec ls -l {} \; 2>/dev/null
-rw-rw-r-- 1 new-user best-group 13545 Oct 23  2019 /mnt/D8B3
-rw-rw-r-- 1 new-user best-group 13545 Oct 23  2019 /home/v2Vb
[new-user@ip-10-10-100-140 ~]$ 
```
- find search for files in a directory hierarchy
- -group gname

File belongs to group gname (numeric group ID allowed).

---

```
[new-user@ip-10-10-100-140 ~]$ find / -type f \( -name 8V2L -o -name bny0 
-o -name c4ZX -o -name D8B3 -o -name FHl1 -o -name oiMO -o -name P
FbD -o -name rmfX -o -name SRSq -o -name uqyw -o -name v2Vb -o -na
me X1Uy \) -exec egrep "[0-9]{1,3}\.[0-9{1,3}\.]" {} \; 2>/dev/nul
l
wNXbEERat4wE0w/O9Mn1.1.1.1VeiSLv47L4B2Mxy3M0XbCYVf9TSJeg905weaIk
[new-user@ip-10-10-100-140 ~]$ 
```
- egrep print lines that match patterns
- `[0-9]` digits between 0 & 9;
- `{1,3}` between one & three;
- `\.` escaped special characters;

In this case, I only need half the IP.

---

```
[new-user@ip-10-10-100-140 ~]$ find / -type f \( -name 8V2L -o -na
me bny0 -o -name c4ZX -o -name D8B3 -o -name FHl1 -o -name oiMO -o
 -name PFbD -o -name rmfX -o -name SRSq -o -name uqyw -o -name v2V
b -o -name X1Uy \) -exec sha1sum {} \; 2>/dev/null
2c8de970ff0701c8fd6c55db8a5315e5615a9575  /mnt/D8B3
9d54da7584015647ba052173b84d45e8007eba94  /mnt/c4ZX
d5a35473a856ea30bfec5bf67b8b6e1fe96475b3  /var/FHl1
57226b5f4f1d5ca128f606581d7ca9bd6c45ca13  /var/log/uqyw
256933c34f1b42522298282ce5df3642be9a2dc9  /opt/PFbD
5b34294b3caa59c1006854fa0901352bf6476a8c  /opt/oiMO
4ef4c2df08bc60139c29e222f537b6bea7e4d6fa  /media/rmfX
0323e62f06b29ddbbe18f30a89cc123ae479a346  /etc/8V2L
acbbbce6c56feb7e351f866b806427403b7b103d  /etc/ssh/SRSq
7324353e3cd047b8150e0c95edf12e28be7c55d3  /home/v2Vb
59840c46fb64a4faeabb37da0744a46967d87e57  /X1Uy
[new-user@ip-10-10-100-140 ~]$ 
```
- sha1sum compute and check SHA1 message digest

We get all the hashes and we find the file by hand.

---

```
[new-user@ip-10-10-100-140 ~]$ find / \( -name 8V2L -o -name bny0 
-o -name c4ZX -o -name D8B3 -o -name FHl1 -o -name oiMO -o -name P
FbD -o -name rmfX -o -name SRSq -o -name uqyw -o -name v2Vb -o -na
me X1Uy \) -exec wc -l {} \; 2>/dev/null
209 /mnt/D8B3
209 /mnt/c4ZX
209 /var/FHl1
209 /var/log/uqyw
209 /opt/PFbD
209 /opt/oiMO
209 /media/rmfX
209 /etc/8V2L
209 /etc/ssh/SRSq
209 /home/v2Vb
209 /X1Uy
[new-user@ip-10-10-100-140 ~]$ 
```
- wc print newline, word, and byte counts for each file
- `-l` print the newline counts;

The file with 230 lines was not found. by deletion, we see that `bny0` is not in the list, does this indicate that it is hidden? or does it not exist? not sure.

---
```
[new-user@ip-10-10-100-140 ~]$ find / -type f \( -name 8V2L -o -na
me bny0 -o -name c4ZX -o -name D8B3 -o -name FHl1 -o -name oiMO -o
 -name PFbD -o -name rmfX -o -name SRSq -o -name uqyw -o -name v2V
b -o -name X1Uy \) -exec ls -ln {} \; 2>/dev/null | grep 502
-rw-rw-r-- 1 501 502 13545 Oct 23  2019 /mnt/D8B3
-rw-rw-r-- 1 501 502 13545 Oct 23  2019 /home/v2Vb
-rw-rw-r-- 1 502 501 13545 Oct 23  2019 /X1Uy
[new-user@ip-10-10-100-140 ~]$ 
```
- ls list directory contents
- `-l`  use a long listing format;
- `-n` like -l, but list numeric user and group IDs;

---

```
[new-user@ip-10-10-100-140 ~]$ find / -executable \( -name 8V2L -o
 -name bny0 -o -name c4ZX -o -name D8B3 -o -name FHl1 -o -name oiM
O -o -name PFbD -o -name rmfX -o -name SRSq -o -name uqyw -o -name
 v2Vb -o -name X1Uy \) -exec ls -l {} \; 2>/dev/null
-rwxrwxr-x 1 new-user new-user 13545 Oct 23  2019 /etc/8V2L
[new-user@ip-10-10-100-140 ~]$ 
```
- find search for files in a directory hierarchy
- `-executable` Matches files which are executable;
