# BANDIT 20 

## INTRO 

## SOLVE

- Ta sẽ chạy kết nối đến localhost, ngăn echo xuống dòng trong command ghi mật khẩu và thực hiện trong background.
```bash
bandit20@bandit:~$ echo -n "0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO" | nc -l -p 1234 &
[1] 3019322
bandit20@bandit:~$ ./suconnect 1234
Read: 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
Password matches, sending next password
EeoULMCra2q0dSkYj561DX7s1CpBuOBt
[1]+  Done                    echo -n "0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO" | nc -l -p 1234
bandit20@bandit:~$
```
- Flag :
```
EeoULMCra2q0dSkYj561DX7s1CpBuOBt
```
