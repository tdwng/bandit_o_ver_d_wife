# BANDIT 14 

## INTRO 

- The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost. 

## SOLVE 

- Dùng bash đơn giản thôi :v
```bash
bandit14@bandit:~$ echo "MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS" | nc localhost 30000
Correct!
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo

bandit14@bandit:~$
```
- Flag :
```
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
```
