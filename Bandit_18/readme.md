# BANDIT 18

## INTRO 

- Update sau.

## SOLVE

- Bài này chơi khăm khi sửa bashrc để logout ngay lập tức. Ta có 2 hướng giải quyết sau :

1. Dùng lệnh trực tiếp khi ssh :
```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme
```

2. Mở shell :)))
```bash
linux@DELLG3:/mnt/c/Users/DBRR$ sshpass -p "x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO" ssh bandit18@bandit.labs.overthewire.org -p 2220 -t bash --noprofile --norc
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

bash-5.2$ ls
readme
bash-5.2$ cat readme
cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8
bash-5.2$
```
## Note : 

- Các option sau trong ssh khá quan trọng :

1. -t : Tạo pseudo TTY, cho phép chạy command tương tác.

2. --noprofile : Không load /etc/profile hoặc ~/.bash_profile để tránh bị cấu hình này reject

3. --norc : Không tải ~/.bashrc, tránh bị đăng xuất ngay lập tức :))))

- Nói chung trò này khá là troll, nhưng không đến nỗi troll người dùng khóc thét.
