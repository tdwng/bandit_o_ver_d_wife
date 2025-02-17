# BANDIT 23 

## INTRO

## ANALYZE

## SOLVE

- Dưới đây là cách làm. Mọi thứ sẽ update trong phần analyze sau.
```bash
bandit23@bandit:~$ mktemp -d
/tmp/tmp.ut6VAVbAJq
bandit23@bandit:~$ cd /tmp/tmp.ut6VAVbAJq
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ nano bandit24_pass.sh
Unable to create directory /home/bandit23/.local/share/nano/: No such file or directory
It is required for saving/loading search history or cursor positions.

bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ ls
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ ls
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ nano bandit24_pass.sh
Unable to create directory /home/bandit23/.local/share/nano/: No such file or directory
It is required for saving/loading search history or cursor positions.

bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ ls
bandit24_pass.sh
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ chmod +rx bandit24_pass.sh
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ chmod 777 /tmp/tmp.ut6VAVbAJq
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ ls
bandit24_pass.sh
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ cd ..
bandit23@bandit:/tmp$ ls
ls: cannot open directory '.': Permission denied
bandit23@bandit:/tmp$ cd tmp.ut6VAVbAJq
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ ls
bandit24_pass.sh
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ touch password
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ chmod +rwx password
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ ls -la
total 17016
drwxrwxrwx 2 bandit23 bandit23     4096 Feb 17 15:53 .
drwxrwx-wt 1 root     root     17412096 Feb 17 15:53 ..
-rwxrwxr-x 1 bandit23 bandit23       74 Feb 17 15:52 bandit24_pass.sh
-rwxrwxr-x 1 bandit23 bandit23        0 Feb 17 15:53 password
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ cp bandit24_pass.sh .
cp: 'bandit24_pass.sh' and './bandit24_pass.sh' are the same file
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ ls
bandit24_pass.sh  password
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ mkdir reverse
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ cp bandit24_pass.sh /reverse
cp: cannot create regular file '/reverse': Permission denied
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ ls
bandit24_pass.sh  password  reverse
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ chmod +rw reverse
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ cp bandit24_pass.sh /reverse
cp: cannot create regular file '/reverse': Permission denied
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ cd ..
bandit23@bandit:/tmp$ cd /tmp/tmp.ut6VAVbAJq
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ ls
bandit24_pass.sh  password  reverse
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ rmdir reverse/
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ mv bandit24_pass.sh /var/spool/bandit24/bandit24_pass.sh
mv: cannot move 'bandit24_pass.sh' to '/var/spool/bandit24/bandit24_pass.sh': Operation not permitted
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ cp bandit24_pass.sh /var/spool/bandit24/foo
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ cat password
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ cat password
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ cat password
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ ls -l
total 4
-rwxrwxr-x 1 bandit23 bandit23 74 Feb 17 15:52 bandit24_pass.sh
-rwxrwxr-x 1 bandit23 bandit23  0 Feb 17 15:53 password
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ cat password
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ cat password \
>
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ cat password
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ cat password
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ ls -l
total 4
-rwxrwxr-x 1 bandit23 bandit23 74 Feb 17 15:52 bandit24_pass.sh
-rwxrwxr-x 1 bandit23 bandit23  0 Feb 17 15:53 password
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ chmod 777 bandit24_pass.sh
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ chmod 777 password
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ ls
bandit24_pass.sh  password
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ ls -l
total 4
-rwxrwxrwx 1 bandit23 bandit23 74 Feb 17 15:52 bandit24_pass.sh
-rwxrwxrwx 1 bandit23 bandit23  0 Feb 17 15:53 password
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ cp bandit24_pass.sh /var/spool/bandit24
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ cp bandit24_pass.sh /var/spool/bandit24/foo
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$ cat password
gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8
bandit23@bandit:/tmp/tmp.ut6VAVbAJq$
```
- Flag :
```
gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8
```
