---
layout 	:	post
title	:	"Finding Files"
tags	:	[RHCSA, RHCSA_mod1, system management, using essential tools, find, which, locate, updatedb]
---

## 2.2 Finding Files

The `find` command is used to find a file within a folder and its subdirectories. When the starting point of the search is the root directory (/) then find will search the entire file system.
While the utility is extremely thorough, this may cause delays due to remote devices on the network mounted on the file system.

```sh
$ find / -name "passwd"
```

If you’re trying to find the location of a binary file, a better command would be `which` command, as it directly shows the location of the binary. However, be careful as it only works with
binaries.

```sh
$ which passwd
/usr/bin/passwd
```

Contrastingly, the command `whereis` not only gives us the location of the binary, but the location of the complete environment of the binary!

```sh
$ whereis passwd
passwd: /usr/bin/passwd /etc/passwd /usr/share/man/man1/passwd.1.gz /usr/share/man/man5/passwd.5.gz
```

Another similar utility is called `locate` which shows all files that have the string provided to it in its name. Note, however, that `locate` operates on a database, invoked for refresh by `updatedb`, that must be updated (especially after the creation of a new file) to show relevant results.

```sh
[root@testBed Documents]# touch sinha
[root@testBed Documents]# ls
sinha
[root@testBed Documents]# locate sinha
/usr/share/vim/vim74/keymap/sinhala-phonetic_utf-8.vim
/usr/share/vim/vim74/keymap/sinhala.vim
[root@testBed Documents]# updatedb
[root@testBed Documents]# locate sinha
/home/somu/Documents/sinha
/usr/share/vim/vim74/keymap/sinhala-phonetic_utf-8.vim
/usr/share/vim/vim74/keymap/sinhala.vim
```