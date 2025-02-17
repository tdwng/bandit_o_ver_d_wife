# BANDIT 11

## INTRO

- Mật khẩu cho cấp độ tiếp theo được lưu trữ trong tệp data.txt , trong đó tất cả các chữ cái thường (az) và chữ cái hoa (AZ) đã được rotated by 13 positions.

## SOLVE 

- Trong bài là hình thức mã hóa ROT13. Ta dùng translate character để giải bài này như sau :

```bash
bandit11@bandit:~$ cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
The password is 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
bandit11@bandit:~$
```

- Flag :
```
7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
```
