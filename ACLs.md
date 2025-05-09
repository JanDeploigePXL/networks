```
R1(config) # ip access-list extended FTP-FILTER
R1(config-ext-nacl) # permit tcp 192.168.10.0 0.0.0.255 any eq ftp
R1(config-ext-nacl) # permit tcp 192.168.10.0 0.0.0.255 any eq ftp-data
```

```
ip access-group {access-list-number | access-list-name} {in | out}
access-list 10 remark ACE permits ONLY host 192.168.10.10 to the internet
access-list 10 permit host 192.168.10.10
do show access-lists
```

```
interface Serial 0/1/0
ip access-group 10 out
end
```

```
show access-lists

conf t
ip access-list standard 1
no 10
10 deny host 192.168.10.10
end
```

