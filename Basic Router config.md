### Hostname, password-encryption, banner

```
Router# configure terminal
Router(config)# hostname R1
R1(config)# service password-encryption
R1(config)# enable secret class
R1(config)# banner motd # A message #
```

### Router interfaces

```
R1(config)# interface gigabiteEthernet 0/0/0
R1(config-if)# ip address 192.168.1.1 255.255.255.0
R1(config-if)# ipv6 address 2001:db8:acad:1::1/64
R1(config-if)# description Link to LAN 1
R1(config-if)# no shutdown
R1(config-if)# exit
R1(config)# interface gigabiteEthernet 0/0/1
R1(config-if)# ip address 192.168.2.1 255.255.255.0
R1(config-if)# ipv6 address 2001:db8:acad:2::1/64
R1(config-if)# description Link to LAN 2
R1(config-if)# no shutdown
R1(config-if)# exit
R1(config)# interface serial 0/0/0
R1(config-if)# ip address 209.165.200.225 255.255.255.252
R1(config-if)# ipv6 address 2001:db8:acad:3::225/64
R1(config-if)# description Link to R2
R1(config-if)# no shutdown
R1(config-if)# exit
```

### Loopback interface

```
R1(config)# interface loopback number 
R1(config-if)# ip address ip-address subnet-mask 
```

### Router on a stick

```
Router(config)# interface gigabitEthernet 0/0/0.75
Router(config-subif)# encapsulation dot1Q 75
```

### Fysical ip adres for router

```
Router(config-subif)# ip address 172.17.7.66 255.255.255.240
```

### HSRP

```
Router(config-subif)# standby version 2
Router(config-subif)# standby 75 ip 172.17.1.1
```

### Priority

```
Router(config-subif)# standby 75 priority 250
Router(config-subif)# standby 75 preempt
Router(config-subif)# end
```

### NATIVE VLAN

```
Router(config)# interface gigabitEthernet 0/0/0.99
Router(config-subif)# encapsulation dot1Q 99 native
```
### BRING UP THE PORT

```
int gigabitEthernet 0/0/0
no shutdown
```
### SET IP OF ROUTER

```
conf t
int gig 0/0/1
ip address 10.199.65.220 255.255.255.225
no shut
exit
```


