# BANDIT 28

## INTRO

## SOLVE

- Các lệnh :

1. git log : hiển thị commit log 
2. git show < commit > : show nội dung commit

```bash
bandit28@bandit:~$ mktemp -d
/tmp/tmp.gauibGAYx6 
bandit28@bandit:~$ cd /tmp/tmp.gauibGAYx6 
bandit28@bandit:/tmp/tmp.gauibGAYx6$ git clone ssh://bandit28-git@localhost/home/bandit28-git/repo
...
bandit28-git@localhost's password: 
...
bandit28@bandit:/tmp/tmp.gauibGAYx6$ ls
repo
bandit28@bandit:/tmp/tmp.gauibGAYx6$ cd repo
bandit28@bandit:/tmp/tmp.gauibGAYx6/repo$ ls -la
total 16
drwxr-sr-x 3 bandit28 root 4096 Jul  3 12:30 .
drwx--S--- 3 bandit28 root 4096 Jul  3 12:30 ..
drwxr-sr-x 8 bandit28 root 4096 Jul  3 12:30 .git
-rw-r--r-- 1 bandit28 root  111 Jul  3 12:30 README.md
bandit28@bandit:/tmp/tmp.gauibGAYx6/repo$ cat README.md 
# Bandit Notes
Some notes for level29 of bandit.

## credentials

- username: bandit29
- password: xxxxxxxxxx
bandit28@bandit:/tmp/tmp.gauibGAYx6/repo$ git log
commit edd935d60906b33f0619605abd1689808ccdd5ee
Author: Morla Porla <morla@overthewire.org>
Date:   Thu May 7 20:14:49 2020 +0200

    fix info leak

commit c086d11a00c0648d095d04c089786efef5e01264
Author: Morla Porla <morla@overthewire.org>
Date:   Thu May 7 20:14:49 2020 +0200

    add missing data

commit de2ebe2d5fd1598cd547f4d56247e053be3fdc38
Author: Ben Dover <noone@overthewire.org>
Date:   Thu May 7 20:14:49 2020 +0200

    initial commit of README.md
bandit28@bandit:/tmp/tmp.gauibGAYx6/repo$ git show edd935d60906b33f0619605abd1689808ccdd5ee
commit edd935d60906b33f0619605abd1689808ccdd5ee
Author: Morla Porla <morla@overthewire.org>
Date:   Thu May 7 20:14:49 2020 +0200

    fix info leak

diff --git a/README.md b/README.md
index 3f7cee8..5c6457b 100644
--- a/README.md
+++ b/README.md
@@ -4,5 +4,5 @@ Some notes for level29 of bandit.
 ## credentials
 
 - username: bandit29
-- password: bbc96594b4e001778eee9975372716b2
+- password: xxxxxxxxxx
```