# BANDIT 9

## INTRO

- Mật khẩu cho cấp độ tiếp theo được lưu trữ trong tệp data.txt dưới dạng một trong số ít chuỗi mà con người có thể đọc được, bắt đầu bằng một số ký tự '='.

## ANALYZE

- **strings** là command dùng để lọc các chuỗi có thể đọc được.

- Công thức : 
```bash
strings [file]
```

## SOLVE 

- **strings** và **grep** thôi, đơn giản như sau :
```bash 
strings data.txt | grep "==="
```

- Rất nhanh, ta có kết quả :
```bash
bandit9@bandit:~$ strings data.txt | grep "==="
}========== the
3JprD========== passwordi
~fDV3========== is
D9========== FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
bandit9@bandit:~$
```

- Flag :
```
FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
```
