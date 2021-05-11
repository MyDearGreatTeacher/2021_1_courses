#
```
安裝 DC

成功安裝的各種驗證


建置底下使用者與全組

業務部 
  部長 ==> 你自己
  你的好朋友

行政部  

人資部
   
```

#
```
PS C:\Users\Administrator> nslookup
Default Server:  DESKTOP-S08HONO
Address:  ::1

> set type = srv
Unrecognized command: set type = srv
> set type=srv
> _ldap._tcp.dc,_msdcs.syaksu.local
Unrecognized command: _ldap._tcp.dc,_msdcs.syaksu.local
> _ldap._tcp.dc._msdcs.syaksu.local
Server:  DESKTOP-S08HONO
Address:  ::1

*** DESKTOP-S08HONO can't find _ldap._tcp.dc._msdcs.syaksu.local: Non-existent domain
> _ldap._tcp.dc._msdcs.sayksu.local
Server:  DESKTOP-S08HONO
Address:  ::1

_ldap._tcp.dc._msdcs.sayksu.local       SRV service location:
          priority       = 0
          weight         = 100
          port           = 389
          svr hostname   = KSU-Server-Windows2019.sayksu.local
KSU-Server-Windows2019.sayksu.local     internet address = 172.27.206.251
>

```
