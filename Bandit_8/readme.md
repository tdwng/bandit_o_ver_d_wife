# BANDIT 8

## INTRO

- Mật khẩu cho cấp độ tiếp theo được lưu trữ trong tệp data.txt và là dòng văn bản duy nhất chỉ xuất hiện một lần.

## 

### Ta sẽ sử dụng 2 command là **sort** và **uniq** để hoàn thành bài này.

### sort 

- Dùng để sắp xếp

- Cú pháp :
```bash 
sort [options] [file]
```

- Options chính của sort gồm :

1. -n : sắp xếp theo số ( numeric )

2. -r : sắp xếp ngược ( reverse )

3. -u : Loại bỏ các dòng trùng lặp ( giữ lại dòng đầu )

4. -k : sắp xếp theo cột cụ thể, vd **sort -k2 file.txt**

5. -M : sắp xếp theo tháng 

6. -V : sắp xếp theo phiên bản

### uniq

- Dùng để đếm

- Cú pháp :
```bash
uniq [options] [file]
```
- Options chính của uniq gồm :

1. -c : đếm số lần xuất hiện của mỗi dòng

2. -d : chỉ hiển thị dòng trùng lặp ( bỏ các dòng chỉ có 1 lần )

3. -u : hiển thị dòng chỉ xuất hiện duy nhất 1 lần 

4. -i : không phân biệt chữ hoa hay thường 

5. -f [n] : bỏ qua n cột đầu khi so sánh ( vd : uniq -f 2 file.txt là bỏ qua 2 cột đầu )

6. -s [n] : bỏ qua n kí tự đầu mỗi dòng

## SOLVE 

- Từ mục analyze, dễ dàng có được command ta cần :
```bash
sort data.txt | uniq -u 
```

- Kết quả :
```bash 
bandit8@bandit:~$ sort data.txt | uniq -u
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
bandit8@bandit:~$
```
- Flag :
```
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
```