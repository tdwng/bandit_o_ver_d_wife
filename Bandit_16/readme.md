# BANDIT 16

## INTRO < TRANSLATED >

- Có thể lấy thông tin xác thực cho cấp độ tiếp theo bằng cách gửi mật khẩu của cấp độ hiện tại đến một cổng trên máy chủ cục bộ trong phạm vi từ 31000 đến 32000. Trước tiên, hãy tìm xem cổng nào trong số các cổng này có máy chủ đang lắng nghe. Sau đó, hãy tìm xem cổng nào trong số các cổng đó sử dụng SSL/TLS và cổng nào không. Chỉ có 1 máy chủ sẽ cung cấp thông tin xác thực tiếp theo, các máy chủ khác sẽ chỉ gửi lại cho bạn bất cứ thông tin nào bạn gửi đến máy chủ đó. 

## SOLVE

- Dùng nmap để quét cổng, sau đó thử từng cái một :
```bash
bandit16@bandit:~$ nmap -p 31000-32000 localhost
Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-02-17 13:29 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00032s latency).
Not shown: 996 closed tcp ports (conn-refused)
PORT      STATE SERVICE
31046/tcp open  unknown
31518/tcp open  unknown
31691/tcp open  unknown
31790/tcp open  unknown
31960/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 0.07 seconds
bandit16@bandit:~$ openssl s_client -connect localhost:31046
CONNECTED(00000003)
4087F0F7FF7F0000:error:0A0000F4:SSL routines:ossl_statem_client_read_transition:unexpected message:../ssl/statem/statem_clnt.c:398:
---
no peer certificate available
---
No client certificate CA names sent
---
SSL handshake has read 293 bytes and written 300 bytes
Verification: OK
---
New, (NONE), Cipher is (NONE)
Secure Renegotiation IS NOT supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
Early data was not sent
Verify return code: 0 (ok)
---
bandit16@bandit:~$ echo "kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx" | openssl s_client -co
nnect localhost:31046 -quiet
4087F0F7FF7F0000:error:0A0000F4:SSL routines:ossl_statem_client_read_transition:unexpected message:../ssl/statem/statem_clnt.c:398:
bandit16@bandit:~$ openssl s_client -connect localhost:31518
CONNECTED(00000003)
Can't use SSL_get_servername
depth=0 CN = SnakeOil
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN = SnakeOil
verify return:1
---
Certificate chain
 0 s:CN = SnakeOil
   i:CN = SnakeOil
   a:PKEY: rsaEncryption, 4096 (bit); sigalg: RSA-SHA256
   v:NotBefore: Jun 10 03:59:50 2024 GMT; NotAfter: Jun  8 03:59:50 2034 GMT
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIFBzCCAu+gAwIBAgIUBLz7DBxA0IfojaL/WaJzE6Sbz7cwDQYJKoZIhvcNAQEL
BQAwEzERMA8GA1UEAwwIU25ha2VPaWwwHhcNMjQwNjEwMDM1OTUwWhcNMzQwNjA4
MDM1OTUwWjATMREwDwYDVQQDDAhTbmFrZU9pbDCCAiIwDQYJKoZIhvcNAQEBBQAD
ggIPADCCAgoCggIBANI+P5QXm9Bj21FIPsQqbqZRb5XmSZZJYaam7EIJ16Fxedf+
jXAv4d/FVqiEM4BuSNsNMeBMx2Gq0lAfN33h+RMTjRoMb8yBsZsC063MLfXCk4p+
09gtGP7BS6Iy5XdmfY/fPHvA3JDEScdlDDmd6Lsbdwhv93Q8M6POVO9sv4HuS4t/
jEjr+NhE+Bjr/wDbyg7GL71BP1WPZpQnRE4OzoSrt5+bZVLvODWUFwinB0fLaGRk
GmI0r5EUOUd7HpYyoIQbiNlePGfPpHRKnmdXTTEZEoxeWWAaM1VhPGqfrB/Pnca+
vAJX7iBOb3kHinmfVOScsG/YAUR94wSELeY+UlEWJaELVUntrJ5HeRDiTChiVQ++
wnnjNbepaW6shopybUF3XXfhIb4NvwLWpvoKFXVtcVjlOujF0snVvpE+MRT0wacy
tHtjZs7Ao7GYxDz6H8AdBLKJW67uQon37a4MI260ADFMS+2vEAbNSFP+f6ii5mrB
18cY64ZaF6oU8bjGK7BArDx56bRc3WFyuBIGWAFHEuB948BcshXY7baf5jjzPmgz
mq1zdRthQB31MOM2ii6vuTkheAvKfFf+llH4M9SnES4NSF2hj9NnHga9V08wfhYc
x0W6qu+S8HUdVF+V23yTvUNgz4Q+UoGs4sHSDEsIBFqNvInnpUmtNgcR2L5PAgMB
AAGjUzBRMB0GA1UdDgQWBBTPo8kfze4P9EgxNuyk7+xDGFtAYzAfBgNVHSMEGDAW
gBTPo8kfze4P9EgxNuyk7+xDGFtAYzAPBgNVHRMBAf8EBTADAQH/MA0GCSqGSIb3
DQEBCwUAA4ICAQAKHomtmcGqyiLnhziLe97Mq2+Sul5QgYVwfx/KYOXxv2T8ZmcR
Ae9XFhZT4jsAOUDK1OXx9aZgDGJHJLNEVTe9zWv1ONFfNxEBxQgP7hhmDBWdtj6d
taqEW/Jp06X+08BtnYK9NZsvDg2YRcvOHConeMjwvEL7tQK0m+GVyQfLYg6jnrhx
egH+abucTKxabFcWSE+Vk0uJYMqcbXvB4WNKz9vj4V5Hn7/DN4xIjFko+nREw6Oa
/AUFjNnO/FPjap+d68H1LdzMH3PSs+yjGid+6Zx9FCnt9qZydW13Miqg3nDnODXw
+Z682mQFjVlGPCA5ZOQbyMKY4tNazG2n8qy2famQT3+jF8Lb6a4NGbnpeWnLMkIu
jWLWIkA9MlbdNXuajiPNVyYIK9gdoBzbfaKwoOfSsLxEqlf8rio1GGcEV5Hlz5S2
txwI0xdW9MWeGWoiLbZSbRJH4TIBFFtoBG0LoEJi0C+UPwS8CDngJB4TyrZqEld3
rH87W+Et1t/Nepoc/Eoaux9PFp5VPXP+qwQGmhir/hv7OsgBhrkYuhkjxZ8+1uk7
tUWC/XM0mpLoxsq6vVl3AJaJe1ivdA9xLytsuG4iv02Juc593HXYR8yOpow0Eq2T
U5EyeuFg5RXYwAPi7ykw1PW7zAPL4MlonEVz+QXOSx6eyhimp1VZC11SCg==
-----END CERTIFICATE-----
subject=CN = SnakeOil
issuer=CN = SnakeOil
---
No client certificate CA names sent
Peer signing digest: SHA256
Peer signature type: RSA-PSS
Server Temp Key: X25519, 253 bits
---
SSL handshake has read 2103 bytes and written 373 bytes
Verification error: self-signed certificate
---
New, TLSv1.3, Cipher is TLS_AES_256_GCM_SHA384
Server public key is 4096 bit
Secure Renegotiation IS NOT supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
Early data was not sent
Verify return code: 18 (self-signed certificate)
---
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: 785EB96452C140B725D719F1D54BBD978E36FC56F27659121FA51C06A6B6BEA0
    Session-ID-ctx:
    Resumption PSK: 188DB16E9A729BDCD221A8A4238E0636001E87AE70D6F0663EA96DFD9D0D1EE33125CA5FDFA53E6D9AD846B8C322354C
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 300 (seconds)
    TLS session ticket:
    0000 - 3b a9 e4 b2 98 5f 9b 38-cd 5a 22 f4 db e9 af 67   ;...._.8.Z"....g
    0010 - f1 c3 42 f5 d5 ff c4 1b-53 b1 31 2a e5 50 01 e5   ..B.....S.1*.P..
    0020 - d8 e3 89 f1 4f c2 42 7f-ca 53 e1 17 89 b8 34 9c   ....O.B..S....4.
    0030 - 2e 96 f0 76 5b c3 04 4e-93 c1 72 a4 d8 86 26 b2   ...v[..N..r...&.
    0040 - 86 e8 e0 15 49 7f cd 05-11 be 5c 80 d7 d0 d0 22   ....I.....\...."
    0050 - 38 3d b5 db 98 eb 18 65-20 9f b2 3e 63 91 4e 11   8=.....e ..>c.N.
    0060 - 5e 80 3d 4a 2b 69 37 d0-22 96 e3 75 51 31 46 3d   ^.=J+i7."..uQ1F=
    0070 - be 1a 7c 26 92 f4 ec b8-41 df ec 7f c0 8c a2 75   ..|&....A......u
    0080 - 8e 0f 0d 2c 6e 6e 2b b7-06 b1 85 90 30 26 5b 91   ...,nn+.....0&[.
    0090 - e4 18 01 4a fe 62 17 51-7d 73 65 1f 2e f1 3b c3   ...J.b.Q}se...;.
    00a0 - 19 d1 51 76 60 e2 3c a4-b4 00 c2 d6 e6 1a b2 e3   ..Qv`.<.........
    00b0 - 5a c5 02 ed c9 35 28 20-99 15 9d e7 3c 5e a7 b7   Z....5( ....<^..
    00c0 - fc d6 86 29 ab 20 ca 8f-5a f7 01 e8 05 aa 52 c9   ...). ..Z.....R.
    00d0 - 89 55 58 21 7d 86 46 d9-f7 29 96 80 62 3d c4 2c   .UX!}.F..)..b=.,

    Start Time: 1739799156
    Timeout   : 7200 (sec)
    Verify return code: 18 (self-signed certificate)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: D83E80980A620A90ACEFB75F7625E795106691D83174FB2B26752CC2B6A9662D
    Session-ID-ctx:
    Resumption PSK: A0EF888FA89D7CD39290284C130B0641869C199A74F4F8F2DD326CD616479A156F927B96EAE88743337A07FBAB944136
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 300 (seconds)
    TLS session ticket:
    0000 - 3b a9 e4 b2 98 5f 9b 38-cd 5a 22 f4 db e9 af 67   ;...._.8.Z"....g
    0010 - 9b 40 52 f9 89 48 78 c0-2b 4c a0 0f 65 36 6a 61   .@R..Hx.+L..e6ja
    0020 - 9d 02 71 80 9c 76 10 35-f3 84 6d c2 55 06 f3 f2   ..q..v.5..m.U...
    0030 - 09 fc a8 a7 94 6e aa 6e-85 19 bf 4d 5f 9b f3 c9   .....n.n...M_...
    0040 - 47 2d 6f a4 c0 44 3a a2-eb 14 3e dc 8c eb 57 df   G-o..D:...>...W.
    0050 - b5 66 e8 f4 bd b3 15 d3-3d c1 52 c2 3a 9a 5a d8   .f......=.R.:.Z.
    0060 - 14 46 b7 0d 7e 54 bb 22-f4 e0 bf 91 f8 9e f0 b1   .F..~T."........
    0070 - bd 29 b0 45 42 1d 75 6f-6f 60 19 84 e4 80 7c 33   .).EB.uoo`....|3
    0080 - fb fe 9f 29 c3 73 68 13-67 b1 f7 db cf 37 09 ec   ...).sh.g....7..
    0090 - 32 fc 3c af d1 ba b5 da-ae ac 8e f0 d7 26 e9 a9   2.<..........&..
    00a0 - 3a c0 2e 1e 6e 8d 7b fe-df 41 88 20 fd c5 a2 f9   :...n.{..A. ....
    00b0 - f8 94 3d e1 e4 0f 99 30-f3 6a 29 00 6d f4 be 2c   ..=....0.j).m..,
    00c0 - a9 bb 77 d8 87 22 2f 05-70 f7 29 ed be 17 6d 62   ..w.."/.p.)...mb
    00d0 - c1 85 80 56 d6 e1 08 b2-d0 74 60 70 3b 6d e5 c5   ...V.....t`p;m..

    Start Time: 1739799156
    Timeout   : 7200 (sec)
    Verify return code: 18 (self-signed certificate)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
closed
bandit16@bandit:~$ echo "kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx" | openssl s_client -connect localhost:31518 -quiet
Can't use SSL_get_servername
depth=0 CN = SnakeOil
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN = SnakeOil
verify return:1
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx

bandit16@bandit:~$
```
- Flag :
```
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
```
