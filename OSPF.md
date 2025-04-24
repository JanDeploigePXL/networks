```
show ip ospf neighbor
show ip ospf database
show ip route
```

```
R1(config)# router ospf 10
interface loopback 1
ip address 1.1.1.1 255.255.255.255
end
show ip protocols | include Router ID
```

```
router ospf 10
router-id 1.1.1.1
end
```

```
show ip protocols | include Router ID
```

```
clear ip ospf process
network network-address wildcard-mask area area-id
```

```
1. Router OSPF 10
2. Router ID
3. Interfaces voor OSPF
   - Network statement
   - Interface niveau
```

Wildcard mask --> Omgekeerde van een subnetmask | 255.255.255.252 --> 0.0.0.3

Passive interface --> Interface waarop ospf niet gebruikt wordt.

```
router ospf 10
passive-interface loopback 0
```

```
show ip protocols
```

```
router ospf 10
network 10.10.1.0 0.0.0.255 area 0
network 10.1.1.4 0.0.0.3 area 0
network 10.1.1.12 0.0.0.3 area 0
```

```
interface Gig 0/0/1
ip ospf 10 area 0
```

```
interface Gig 0/0/2
ip ospf 10 area 0
```

```
interface loopback 0
ip ospf 10 area 0
```

```
show ip ospf interface Gig 0/0/0
```

```
interface Gig 0/0/1
ip ospf network point-to-point
ip ospf priority 0-255 <-- higher is more priority
```

```
auto-cost reference-bandwidth 10000000000
ip ospf cost 10
ip ospf dead-interval <seconds>
ip ospf hello-interval <seconds>
```

```
show ip interface brief
show ip route
show ip ospf neighbor
show ip protocol
show ip protocols
show ip ospf
show ip ospf interface
```