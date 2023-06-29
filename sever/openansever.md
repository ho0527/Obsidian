# 本地端架站步驟(open sever in local computer)

## step
1. go to cmd
2. type command
```cmd
> ipconfig
```
3. found Default Gateway in Wireless LAN adapter Wi-Fi:
```cmd
Wireless LAN adapter Wi-Fi:

   Connection-specific DNS Suffix  . : home
   Link-local IPv6 Address . . . . . : fe80::1410:3851:bdf2:49ac%9
   IPv4 Address. . . . . . . . . . . : 192.168.0.43
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.0.1 // this one
```
4. go to web sever and type Default Gateway ip
5. login
6. go to basic > port forwarding
7. add rule
8. type IPv4 Address in 192.168.0.*\[here\]*
9. type the port you want to open to public
10. Control -> both
11. click add
12. now you can use it and anyone can go in your website:)

## 註解及參見
[openSSL](ssl.md)


小賀chris:) 2023/06/28 v1.0.0