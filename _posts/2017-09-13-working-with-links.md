---
type : post
title : 'Working with Links'
tags : [RHCSA, RHCSA_mod1, system management, using essential tools, ls -il, ln, ln -s]
---

The `ln` command is used to create both hardlinks and symbolic links. To create a symbolic
link, we need only add the `-s` option. The `-i` option of the `ls` command shows us the inode
number.

```console
[root@testBed somu]# ln /etc/hosts computers
[root@testBed somu]# ls -il /etc/hosts computers
8388733 -rw-r--r--. 2 root root 158 Jun 7 2013 computers
8388733 -rw-r--r--. 2 root root 158 Jun 7 2013 /etc/hosts
[root@testBed somu]# ln -s computers newcomputers
[root@testBed somu]# ls -il /etc/hosts computers newcomputers
8388733 -rw-r--r--. 2 root root 158 Jun 7 2013 computers
8388733 -rw-r--r--. 2 root root 158 Jun 7 2013 /etc/hosts
27604468 lrwxrwxrwx. 1 root root 9 Sep 7 19:26 newcomputers -> computers
[root@testBed somu]# rm -f computers
[root@testBed somu]# ls -il /etc/hosts newcomputers
8388733 -rw-r--r--. 1 root root 158 Jun 7 2013 /etc/hosts
27604468 lrwxrwxrwx. 1 root root 9 Sep 7 19:26 newcomputers -> computers
[root@testBed somu]# exit
exit
[somu@testBed ~]$ ln /etc/shadow mydata
ln: failed to create hard link 'mydata' => '/etc/shadow': Operation not permitted
[somu@testBed ~]$ ls -l /etc/shadow
----------. 1 root root 1375 Sep 5 21:04 /etc/shadow
```

When the hardlink _computers_ to the inode associated with `/etc/hosts` is deleted, the associated symbolic link of _newcomputers_ becomes invalid.

Finally, RHEL 7 onwards, a user may only create a link to a file/directory that it at least has a read permission to. Thus, any user won’t be able to create a link to `/etc/shadow` as it has no permissions for anybody.