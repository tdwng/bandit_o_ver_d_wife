# BANDIT 13

## INTRO

- Mật khẩu có trong /etc/bandit_pass/bandit14 và chỉ có thể dc đọc bởi user bandit14. Ta nhận được ssh key có thể login vào level tiếp theo. 

## SOLVE

- Ta thấy có một khóa RSA khi đăng nhập vào bandit13.

- Làm như hình  :
```bash
bandit13@bandit:~$ ssh -i sshkey.private bandit14@localhost -p 2220



bandit14@bandit:~$ cat ./etc/bandit_pass/bandit14
cat: ./etc/bandit_pass/bandit14: No such file or directory
bandit14@bandit:~$ cd /etc
bandit14@bandit:/etc$ cd bandit_pass/
bandit14@bandit:/etc/bandit_pass$ ls
bandit0   bandit13  bandit18  bandit22  bandit27  bandit31  bandit6
bandit1   bandit14  bandit19  bandit23  bandit28  bandit32  bandit7
bandit10  bandit15  bandit2   bandit24  bandit29  bandit33  bandit8
bandit11  bandit16  bandit20  bandit25  bandit3   bandit4   bandit9
bandit12  bandit17  bandit21  bandit26  bandit30  bandit5
bandit14@bandit:/etc/bandit_pass$ cat bandit14
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
```
- Flag :
```
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
```
