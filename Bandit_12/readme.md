# BANDIT 12

## INTRO 

- The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!)

## SOLVE 

- Cứ giải nén cho đến khi có pwd :)))
```bash
bandit12@bandit:~$ cd /tmp
bandit12@bandit:/tmp$ ls
ls: cannot open directory '.': Permission denied
bandit12@bandit:/tmp$ mktemp -d
/tmp/tmp.2eaAidyDDy
bandit12@bandit:/tmp$ cd /tmp/tmp.2eaAidyDDy
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ ls
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ cd ../..
bandit12@bandit:/$ ls
bin                dev      formulaone  lib    lib.usr-is-merged  media  proc  sbin                srv  usr
bin.usr-is-merged  drifter  home        lib32  libx32             mnt    root  sbin.usr-is-merged  sys  var
boot               etc      krypton     lib64  lost+found         opt    run   snap                tmp
bandit12@bandit:/$ cd ~
bandit12@bandit:~$ ls
data.txt
bandit12@bandit:~$ cd /tmp/tmp.2eaAidyDDy
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ cp ~/data.txt
cp: missing destination file operand after '/home/bandit12/data.txt'
Try 'cp --help' for more information.
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ cp ~/data.txt .
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ ls
data.txt
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ xxd -r data.txt > data.bin
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ ls
data.bin  data.txt
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ file data.bin
data.bin: gzip compressed data, was "data2.bin", last modified: Thu Sep 19 07:08:15 2024, max compression, from Unix, original size modulo 2^32 574
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ mv data.bin data.gz
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ ls
data.gz  data.txt
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ gunzip data.gz
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ cat data.bin
cat: data.bin: No such file or directory
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ ls
data  data.txt
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ cat data
BZh91AY&SYʃ�����������������ݿ~[���߾��o������;V4�i���CF�CA���␦i��hѠ�3Q���QFF�4� �&MF���␦��d4���O���4шC�
␦d�F�␦hɦ�0�hh�2*�`Q��S/�&F��@�@4i��h�
                       ���]�N��')!L��L�5��O�Z
�=g!Wb^
�d     �����#�{B��9�v�/tJ���<N�7o�#E�_#
  54�)A����
           tOJQ��#�̜�匔a���JB�a�}6�"�YⵟQ���*��0h���}�����|�␦!   &��n�"��{�
                                                                          �Go7
                                                                              6a�ީ�/�F��8��S6��Gα�S7�H1R�A��&�l(�$��e�\�l�ن�"G�ՋX�Vz�
                                                    ���\c�%     a,Sd�}$���`�Ǿ
␦�G�Cp���C�ˈ*J�K���g��g����#mAj(��`��.R)}��N0��&F�]0b&(�N�KgT8�BJ���.Ƀ���]��BC*�bandit12@bandit:/tmp/tmp.2eaAidyDDy$ mv data data.bz2
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ ls
data.bz2  data.txt
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ bzip2 -d data
bzip2: Can't open input file data: No such file or directory.
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ bzip2 -d data.bz2
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ ls
data  data.txt
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ cat data
���fdata4.bin��=H[q���赚�� ���Nzor?pb�*��H��U$!J*�A����Z$��֡
AP\���
��JP�1�VEt�H75:Z�I��{��8g{#�xH� ��7G�34�"�.�G;�U�0=f~xM����0���[0<�dY��W�]w��"����ڿ�x��?��:��{�Nmhs����-
_��A<����2�z�,v��T�W��ә��;�د�[����T@l:�:jO��ME��5w�d���~��ៅ�����`�:�u�n9��UTPbandit12@bandit:/tmp/tmp.2eaAidyDDy$ file data
data: gzip compressed data, was "data4.bin", last modified: Thu Sep 19 07:08:15 2024, max compression, from Unix, original size modulo 2^32 20480
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ mv data data.gz
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ gunzip data.gz
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ ls
data  data.txt
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ file data
data: POSIX tar archive (GNU)
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ tar -xf data
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ ls -l
total 36
-rw-rw-r-- 1 bandit12 bandit12 20480 Feb 17 12:47 data
-rw-r--r-- 1 bandit12 bandit12 10240 Sep 19 07:08 data5.bin
-rw-r----- 1 bandit12 bandit12  2583 Feb 17 12:41 data.txt
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ file data
data: POSIX tar archive (GNU)
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ rm data.txt
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ ls -l
total 32
-rw-rw-r-- 1 bandit12 bandit12 20480 Feb 17 12:47 data
-rw-r--r-- 1 bandit12 bandit12 10240 Sep 19 07:08 data5.bin
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ file data*
data:      POSIX tar archive (GNU)
data5.bin: POSIX tar archive (GNU)
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ tar -xf data
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ ls -l
total 32
-rw-rw-r-- 1 bandit12 bandit12 20480 Feb 17 12:47 data
-rw-r--r-- 1 bandit12 bandit12 10240 Sep 19 07:08 data5.bin
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ file data
data: POSIX tar archive (GNU)
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ tar -xf data5.bin
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ ls
data  data5.bin  data6.bin
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ file data6.bin
data6.bin: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ bzip2 -d data6.bin
bzip2: Can't guess original name for data6.bin -- using data6.bin.out
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ ls
data  data5.bin  data6.bin.out
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ file data.bin.out
data.bin.out: cannot open `data.bin.out' (No such file or directory)
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ ls -l
total 44
-rw-rw-r-- 1 bandit12 bandit12 20480 Feb 17 12:47 data
-rw-r--r-- 1 bandit12 bandit12 10240 Sep 19 07:08 data5.bin
-rw-r--r-- 1 bandit12 bandit12 10240 Sep 19 07:08 data6.bin.out
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ file data6.bin.out
data6.bin.out: POSIX tar archive (GNU)
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ tar -xf data6.bin.out
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ ls
data  data5.bin  data6.bin.out  data8.bin
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ file data8.bin
data8.bin: gzip compressed data, was "data9.bin", last modified: Thu Sep 19 07:08:15 2024, max compression, from Unix, original size modulo 2^32 49
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ mv data8.bin data8.gz
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ gunzip data8.gz
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ ls
data  data5.bin  data6.bin.out  data8
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ file data8
data8: ASCII text
bandit12@bandit:/tmp/tmp.2eaAidyDDy$ cat data8
The password is FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
bandit12@bandit:/tmp/tmp.2eaAidyDDy$
```
- Flag :
```
FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
```
