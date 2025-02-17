# BANDIT 31

## SOLVE

- Git Ignore có thể tìm hiểu trên GitHub

- 
```bash
bandit31@bandit:~$ mktemp -d
/tmp/tmp.IhtWdYHfZb
bandit31@bandit:~$ cd /tmp/tmp.IhtWdYHfZb
bandit31@bandit:/tmp/tmp.IhtWdYHfZb$ git clone ssh://bandit31-git@localhost/home/bandit31-git/repo
bandit31@bandit:/tmp/tmp.IhtWdYHfZb$ ls
repo
bandit31@bandit:/tmp/tmp.IhtWdYHfZb$ cd repo
bandit31@bandit:/tmp/tmp.IhtWdYHfZb/repo$ ls -la
total 20
drwxr-sr-x 3 bandit31 root 4096 Jul  3 13:13 .
drwx--S--- 3 bandit31 root 4096 Jul  3 13:13 ..
drwxr-sr-x 8 bandit31 root 4096 Jul  3 13:13 .git
-rw-r--r-- 1 bandit31 root    6 Jul  3 13:13 .gitignore
-rw-r--r-- 1 bandit31 root  147 Jul  3 13:13 README.md
bandit31@bandit:/tmp/tmp.IhtWdYHfZb/repo$ cat README.md 
This time your task is to push a file to the remote repository.

Details:
    File name: key.txt
    Content: 'May I come in?'
    Branch: master
    bandit31@bandit:/tmp/tmp.IhtWdYHfZb/repo$ echo 'May I come in?' > key.txt
bandit31@bandit:/tmp/tmp.IhtWdYHfZb/repo$ ls -la
total 24
drwxr-sr-x 3 bandit31 root 4096 Jul  3 13:17 .
drwx--S--- 3 bandit31 root 4096 Jul  3 13:13 ..
drwxr-sr-x 8 bandit31 root 4096 Jul  3 13:13 .git
-rw-r--r-- 1 bandit31 root    6 Jul  3 13:13 .gitignore
-rw-r--r-- 1 bandit31 root   15 Jul  3 13:17 key.txt
-rw-r--r-- 1 bandit31 root  147 Jul  3 13:13 README.md
bandit31@bandit:/tmp/tmp.IhtWdYHfZb/repo$ cat key.txt 
May I come in?
bandit31@bandit:/tmp/tmp.IhtWdYHfZb/repo$ cat .gitignore 
*.txt
bandit31@bandit:/tmp/tmp.IhtWdYHfZb/repo$ git add -f key.txt
bandit31@bandit:/tmp/tmp.IhtWdYHfZb/repo$ git commit -a
Unable to create directory /home/bandit31/.nano: Permission denied
It is required for saving/loading search history or cursor positions.

Press Enter to continue

[master 35298de] Key file
 1 file changed, 1 insertion(+)
 create mode 100644 key.txt
 ```
- Chạy lệnh git push -u origin master là có flag.
