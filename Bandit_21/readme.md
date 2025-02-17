# BANDIT 21

## INTRO

## SOLVE 

- Khá đơn giản :
```bash
bandit21@bandit:/etc/cron.d$ file *
cronjob_bandit22: ASCII text
cronjob_bandit23: ASCII text
cronjob_bandit24: ASCII text
e2scrub_all:      ASCII text
otw-tmp-dir:      regular file, no read permission
sysstat:          ASCII text
bandit21@bandit:/etc/cron.d$ cat ./cronjob*
@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
@reboot bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
* * * * * bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
@reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
bandit21@bandit:/etc/cron.d$ ls -l /usr/bin/cronjob_bandit22.sh
-rwxr-x--- 1 bandit22 bandit21 130 Sep 19 07:08 /usr/bin/cronjob_bandit22.sh
bandit21@bandit:/etc/cron.d$ ls -l /usr/bin/cronjob_bandit22.sh
-rwxr-x--- 1 bandit22 bandit21 130 Sep 19 07:08 /usr/bin/cronjob_bandit22.sh
bandit21@bandit:/etc/cron.d$ cat /usr/bin/cronjob_bandit22.sh
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
bandit21@bandit:/etc/cron.d$ cat ./tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat: ./tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv: No such file or directory
bandit21@bandit:/etc/cron.d$ cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q
bandit21@bandit:/etc/cron.d$
```
- Flag :
```
tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q
```
