# BANDIT 10

## INTRO

- Mật khẩu cho cấp độ tiếp theo được lưu trữ trong tệp data.txt , chứa dữ liệu được mã hóa base64

## SOLVE  

- Chúng ta chỉ cần dùng option -d ( decode ) của base64.
```bash
bandit10@bandit:~$ cat data.txt | base64 -d
The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
bandit10@bandit:~$
```

- Và flag là :
```
dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```
