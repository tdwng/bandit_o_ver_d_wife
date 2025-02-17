# BANDIT 5

## INTRO 

- File nằm trong thư mục inhere

- Có định dạng không phải executable, là loại human-readable.

- File có kích cỡ 1033 bytes.

## SOLVE 

- Có thể dùng lệnh **find .** để tìm trong đường dẫn hiện tại, -type f để xác định loại cần tìm là file, -size 1033c ( 1033 characters ) để xác định 

```bash
bandit5@bandit:~/inhere$ find . -type f -size 1033c
./maybehere07/.file2
bandit5@bandit:~/inhere$ cat ./maybehere07/.file2
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG








                                        bandit5@bandit:~/inhere$
```

## Và đây là kết quả :

```
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```