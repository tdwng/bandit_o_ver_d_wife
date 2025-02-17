# BANDIT 15

## INTRO 

- The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL/TLS encryption.

## SOLVE 

- Vì cổng yêu cầu mã hóa ssl nên sẽ dùng openssl thay cho nc.

```bash
bandit15@bandit:~$ echo "8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo" | openssl s_client -co
nnect localhost:30001
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
    Session-ID: E07C67EEB02DA5859C244B1FC42A5B6D59D7C904751CC8152FC8ADD031D98733
    Session-ID-ctx:
    Resumption PSK: A67D19B32300E2A1B0473E54CDE6AE998D48EC0CD09F741F7498044046310332344052932C5DFC367BE3CB673F3EE963
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 300 (seconds)
    TLS session ticket:
    0000 - 06 00 f1 4c 59 f3 0b 62-c1 8d 69 b3 9e 46 18 da   ...LY..b..i..F..
    0010 - 60 58 61 98 a9 38 5c 7a-3d eb 16 c9 af 00 22 c5   `Xa..8\z=.....".
    0020 - e5 54 71 8a 03 b1 0d e4-6e c7 ed ed 15 e8 cb bf   .Tq.....n.......
    0030 - a7 4e 18 d2 81 ae 11 1e-dc cf a5 aa 1b 94 49 79   .N............Iy
    0040 - c3 9c 68 57 b3 c8 e9 78-05 b7 0f a2 85 79 cb dd   ..hW...x.....y..
    0050 - 7a 6a 31 5b a7 2b 44 7d-1e 79 74 9d 4a 54 5d 0e   zj1[.+D}.yt.JT].
    0060 - 11 17 da de 38 07 c0 a2-80 83 7b 7f 09 b3 5d 44   ....8.....{...]D
    0070 - de 90 1a d0 dc 08 05 4d-38 5d 32 2b 77 e3 70 60   .......M8]2+w.p`
    0080 - a5 4b df 1a c6 48 54 6d-56 65 04 a4 ba 19 8e 29   .K...HTmVe.....)
    0090 - 4e 6c aa 04 df 0d 2f 11-b0 48 15 b0 74 33 6c ee   Nl..../..H..t3l.
    00a0 - ea b9 16 d8 f3 d3 d8 f3-1c 05 3b 4e a0 76 df 79   ..........;N.v.y
    00b0 - d8 ed 7b 3e 97 c1 f6 8b-bb 3d da 03 b5 e7 13 42   ..{>.....=.....B
    00c0 - 4e c4 db d6 b9 21 f9 b7-89 4d d2 e1 0c ce a4 03   N....!...M......
    00d0 - c8 5e c5 35 7f 49 03 09-c6 bd 9c 95 05 9d dd 6d   .^.5.I.........m

    Start Time: 1739798624
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
    Session-ID: 7BCDA34B0FD05527805C5CE1510068310DFD223FBC8661E061B560C849B95ECB
    Session-ID-ctx:
    Resumption PSK: 5F0C6567F4FE993F39CB3FE8A6DF867AB8E09F417F21D1FA7401E82044033AF0507D165D1A82857ED64347ECBEE9663E
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 300 (seconds)
    TLS session ticket:
    0000 - 06 00 f1 4c 59 f3 0b 62-c1 8d 69 b3 9e 46 18 da   ...LY..b..i..F..
    0010 - 9b 7f a8 72 70 35 42 84-72 12 7f b4 88 37 c9 b0   ...rp5B.r....7..
    0020 - f3 65 4a aa 0f 77 e4 bd-a7 af af 49 cf c9 5a ff   .eJ..w.....I..Z.
    0030 - 29 47 90 43 5a 26 b7 ee-8b dc b8 ab 9a c0 da 91   )G.CZ&..........
    0040 - b9 9e 03 4a c5 ee 00 77-42 9f f9 4a b7 2c e2 8a   ...J...wB..J.,..
    0050 - 39 d5 57 9a c7 e0 6c 5d-49 02 e8 ff 9e 01 9d 29   9.W...l]I......)
    0060 - 7e 9a 3f 5b 7f 89 4f 4b-0c 38 5d ea 90 c1 03 10   ~.?[..OK.8].....
    0070 - 58 01 5e af 71 05 45 fb-71 3d f5 11 89 9e 9d 68   X.^.q.E.q=.....h
    0080 - 30 71 54 c8 2c 42 37 a6-ad 34 e2 5e 38 6f 56 2e   0qT.,B7..4.^8oV.
    0090 - 0b b7 6c eb 10 cb 3a 3a-29 00 ea 3d e6 7e f4 5d   ..l...::)..=.~.]
    00a0 - 86 9a a6 b6 f9 b7 5c 02-0c 3c 60 34 29 9c 91 b0   ......\..<`4)...
    00b0 - e7 cd 77 75 50 9e 1e 39-61 aa a7 27 10 c3 72 5b   ..wuP..9a..'..r[
    00c0 - a2 21 3a e6 e7 a4 bd c3-3e 80 4a 7d 21 ea 63 50   .!:.....>.J}!.cP
    00d0 - bc 70 04 fb d9 77 0a 0c-79 ae d8 66 b8 27 4d 85   .p...w..y..f.'M.

    Start Time: 1739798624
    Timeout   : 7200 (sec)
    Verify return code: 18 (self-signed certificate)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
DONE
bandit15@bandit:~$ echo "8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo" | openssl s_client -connect localhost:30001 -quiet
Can't use SSL_get_servername
depth=0 CN = SnakeOil
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN = SnakeOil
verify return:1
Correct!
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx

bandit15@bandit:~$
```
- Exp : nên thêm option -quiet để lọc bớt thông tin không cần thiết.
 
- Flag :
```
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
```