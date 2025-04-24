### IP address

```
S1# configure terminal
S1(config)# interface vlan 99
S1(config-if)# ip address 172.17.99.1 255.255.255.0
S1(config-if)# ipv6 address 2001:db8:acad:99::11/64
S1(config-if)# no shutdown
S1(config-if)# end
S1# copy running-config startup-config
```

### Default gateway

```
S1# configure terminal
S1(config)# ip default-gateway 172.17.99.1
S1(config)# end
S1# copy running-config startup-config
```

### Link local IPv6

```
S1(config)# interface vlan99
S1(config-if)# ipv6 address FE80::2 link-local
```

### Verify config

```
S1# show ip interface brief
S1# show ipv6 interface brief
```

### DNS

ip name-server 10.199.64.66

### Domain

ip domain name data.labnet.local

NTP

ip ntp 10.199.64.66