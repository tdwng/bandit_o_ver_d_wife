# BANDIT 6

## INTRO

- Mật khẩu được lưu trữ đâu đó trên server và có các thuộc tính sau :

1. Thuộc sở hữu của bandit7

2. Thuộc sở hữu của nhóm bandit6

3. Size 33 bytes

## SOLVE 

- Vì thuộc sở hữu của bandit7, nhưng lại thuộc sở hữu của nhóm bandit6, nên find / sẽ là lựa chọn thích hợp nhất

- Sau đó là đến các options khác của nó. Lệnh chuẩn sẽ là 
```bash
find / -type f -user bandit7 -group bandit6 -size 33c
``` 

- Kết quả sẽ như sau :
```bash
bandit6@bandit:~$ find / -type f -size 33c -user bandit7 -group bandit6
find: ‘/drifter/drifter14_src/axTLS’: Permission denied
find: ‘/root’: Permission denied
find: ‘/snap’: Permission denied
find: ‘/tmp’: Permission denied
find: ‘/proc/tty/driver’: Permission denied
find: ‘/proc/1297085/task/1297085/fdinfo/6’: No such file or directory
find: ‘/proc/1297085/fdinfo/5’: No such file or directory
find: ‘/home/bandit31-git’: Permission denied
find: ‘/home/ubuntu’: Permission denied
find: ‘/home/bandit5/inhere’: Permission denied
find: ‘/home/bandit30-git’: Permission denied
find: ‘/home/drifter8/chroot’: Permission denied
find: ‘/home/drifter6/data’: Permission denied
find: ‘/home/bandit29-git’: Permission denied
find: ‘/home/bandit28-git’: Permission denied
find: ‘/home/bandit27-git’: Permission denied
find: ‘/lost+found’: Permission denied
find: ‘/etc/polkit-1/rules.d’: Permission denied
find: ‘/etc/multipath’: Permission denied
find: ‘/etc/stunnel’: Permission denied
find: ‘/etc/xinetd.d’: Permission denied
find: ‘/etc/credstore.encrypted’: Permission denied
find: ‘/etc/ssl/private’: Permission denied
find: ‘/etc/sudoers.d’: Permission denied
find: ‘/etc/credstore’: Permission denied
find: ‘/dev/shm’: Permission denied
find: ‘/dev/mqueue’: Permission denied
find: ‘/var/log/amazon’: Permission denied
find: ‘/var/log/unattended-upgrades’: Permission denied
find: ‘/var/log/chrony’: Permission denied
find: ‘/var/log/private’: Permission denied
find: ‘/var/tmp’: Permission denied
find: ‘/var/spool/cron/crontabs’: Permission denied
find: ‘/var/spool/bandit24’: Permission denied
find: ‘/var/spool/rsyslog’: Permission denied
find: ‘/var/cache/ldconfig’: Permission denied
find: ‘/var/cache/apt/archives/partial’: Permission denied
find: ‘/var/cache/pollinate’: Permission denied
find: ‘/var/cache/private’: Permission denied
find: ‘/var/cache/apparmor/2425d902.0’: Permission denied
find: ‘/var/cache/apparmor/baad73a1.0’: Permission denied
find: ‘/var/lib/polkit-1’: Permission denied
find: ‘/var/lib/amazon’: Permission denied
/var/lib/dpkg/info/bandit7.password
find: ‘/var/lib/apt/lists/partial’: Permission denied
find: ‘/var/lib/chrony’: Permission denied
find: ‘/var/lib/snapd/void’: Permission denied
find: ‘/var/lib/snapd/cookie’: Permission denied
find: ‘/var/lib/private’: Permission denied
find: ‘/var/lib/ubuntu-advantage/apt-esm/var/lib/apt/lists/partial’: Permission denied
find: ‘/var/lib/update-notifier/package-data-downloads/partial’: Permission denied
find: ‘/var/lib/udisks2’: Permission denied
find: ‘/var/crash’: Permission denied
find: ‘/boot/efi’: Permission denied
find: ‘/boot/lost+found’: Permission denied
find: ‘/sys/kernel/tracing’: Permission denied
find: ‘/sys/kernel/debug’: Permission denied
find: ‘/sys/fs/pstore’: Permission denied
find: ‘/sys/fs/bpf’: Permission denied
find: ‘/run/lock/lvm’: Permission denied
find: ‘/run/systemd/inaccessible/dir’: Permission denied
find: ‘/run/systemd/propagate/systemd-udevd.service’: Permission denied
find: ‘/run/systemd/propagate/systemd-resolved.service’: Permission denied
find: ‘/run/systemd/propagate/systemd-networkd.service’: Permission denied
find: ‘/run/systemd/propagate/irqbalance.service’: Permission denied
find: ‘/run/systemd/propagate/systemd-logind.service’: Permission denied
find: ‘/run/systemd/propagate/chrony.service’: Permission denied
find: ‘/run/systemd/propagate/polkit.service’: Permission denied
find: ‘/run/systemd/propagate/ModemManager.service’: Permission denied
find: ‘/run/systemd/propagate/fwupd.service’: Permission denied
find: ‘/run/lvm’: Permission denied
find: ‘/run/cryptsetup’: Permission denied
find: ‘/run/multipath’: Permission denied
find: ‘/run/screen/S-bandit19’: Permission denied
find: ‘/run/screen/S-bandit20’: Permission denied
find: ‘/run/screen/S-bandit25’: Permission denied
find: ‘/run/screen/S-bandit2’: Permission denied
find: ‘/run/screen/S-bandit23’: Permission denied
find: ‘/run/screen/S-bandit24’: Permission denied
find: ‘/run/sudo’: Permission denied
find: ‘/run/user/11000’: Permission denied
find: ‘/run/user/11012’: Permission denied
find: ‘/run/user/11027’: Permission denied
find: ‘/run/user/11005’: Permission denied
find: ‘/run/user/11016’: Permission denied
find: ‘/run/user/11024’: Permission denied
find: ‘/run/user/11013’: Permission denied
find: ‘/run/user/11032’: Permission denied
find: ‘/run/user/11006/systemd/inaccessible/dir’: Permission denied
find: ‘/run/user/11004’: Permission denied
find: ‘/run/user/11001’: Permission denied
find: ‘/run/user/11014’: Permission denied
find: ‘/run/user/11003’: Permission denied
find: ‘/run/user/11020’: Permission denied
find: ‘/run/user/11002’: Permission denied
find: ‘/run/user/11028’: Permission denied
find: ‘/run/user/11029’: Permission denied
find: ‘/run/user/11007’: Permission denied
find: ‘/run/user/11009’: Permission denied
find: ‘/run/user/11008’: Permission denied
find: ‘/run/user/11011’: Permission denied
find: ‘/run/user/11010’: Permission denied
find: ‘/run/user/11015’: Permission denied
find: ‘/run/user/11021’: Permission denied
find: ‘/run/user/11025’: Permission denied
find: ‘/run/user/11019’: Permission denied
find: ‘/run/user/11018’: Permission denied
find: ‘/run/user/8003’: Permission denied
find: ‘/run/user/11030’: Permission denied
find: ‘/run/user/11023’: Permission denied
find: ‘/run/user/8002’: Permission denied
find: ‘/run/chrony’: Permission denied
find: ‘/run/udisks2’: Permission denied
```

- Ta có thể dùng cách tối ưu hơn bằng cách lọc qua grep :
```bash 
find / -type f -size 33c -user bandit7 -group bandit6 2>&1 | grep -v "Permission denied"
```
- Tới đây output đã đơn giản hơn rất nhiều, ta dễ dàng lấy được target :
```bash 
bandit6@bandit:~$ find / -type f -size 33c -user bandit7 -group bandit6 2>&1 | grep -v "Permission denied"
find: ‘/proc/1305166/task/1305166/fdinfo/6’: No such file or directory
find: ‘/proc/1305166/fdinfo/5’: No such file or directory
/var/lib/dpkg/info/bandit7.password
bandit6@bandit:~$ cat ./var/lib/dpkg/info/bandit7.password
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
bandit6@bandit:/$
```
- Flag :
```
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```
