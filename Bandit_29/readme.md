# BANDIT 29

## INTRO

## SOLVE

- Các lệnh cần biết :

1. git branch : liệt kê, tạo hoặc xóa branch 
2. git checkout/ git switch + (branch_name) : đổi branch
3. git merge : nối nhánh

```bash
bandit29@bandit:~$ mktemp -d
/tmp/tmp.ghd4YajYBA 
bandit29@bandit:~$ cd /tmp/tmp.ghd4YajYBA
bandit29@bandit:/tmp/tmp.ghd4YajYBA$ git clone ssh://bandit29-git@localhost/home/bandit29-git/repo
bandit29@bandit:/tmp/tmp.ghd4YajYBA$ ls
repo
bandit29@bandit:/tmp/tmp.ghd4YajYBA$ cd repo
bandit29@bandit:/tmp/tmp.ghd4YajYBA/repo$ ls -la
total 16
drwxr-sr-x 3 bandit29 root 4096 Jul  3 12:50 .
drwx--S--- 3 bandit29 root 4096 Jul  3 12:50 ..
drwxr-sr-x 8 bandit29 root 4096 Jul  3 12:50 .git
-rw-r--r-- 1 bandit29 root  131 Jul  3 12:50 README.md
bandit29@bandit:/tmp/tmp.ghd4YajYBA/repo$ cat README.md 
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: <no passwords in production!>
bandit29@bandit:/tmp/tmp.ghd4YajYBA/repo$ git branch -a
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/dev
  remotes/origin/master
  remotes/origin/sploits-dev
 bandit29@bandit:/tmp/tmp.ghd4YajYBA/repo$ git checkout dev
Branch dev set up to track remote branch dev from origin.
Switched to a new branch 'dev'
bandit29@bandit:/tmp/tmp.ghd4YajYBA/repo$ ls -la
total 20
drwxr-sr-x 4 bandit29 root 4096 Jul  3 13:01 .
drwx--S--- 3 bandit29 root 4096 Jul  3 12:50 ..
drwxr-sr-x 2 bandit29 root 4096 Jul  3 13:01 code
drwxr-sr-x 8 bandit29 root 4096 Jul  3 13:01 .git
-rw-r--r-- 1 bandit29 root  134 Jul  3 13:01 README.md
bandit29@bandit:/tmp/tmp.ghd4YajYBA/repo$ cat README.md 
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: ( ko show nữa )
```
