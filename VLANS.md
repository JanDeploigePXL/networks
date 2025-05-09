### VLAN NAME

```
S1(config)# vlan 20
S1(config-vlan)# name management
S1(config-vlan)# end
```

### VLAN PORTS

```
S1(config)# interface (range) 1/0/1(-10)
S1(config-if)# switchport mode access
S1(config-if)# switchport access vlan 20
S1(config-if)# end
```

### VLAN TRUNK

```
S1(config)# interface 1/0/1
S1(config-if)# switchport mode trunk
S1(config-if)# switchport trunk allowed vlan 10,20,30,40
S1(config-if)# switchport trunk native vlan 99
S1(config-if)# end
```

### Assigning ports

```
S1(config)# interface range gigabitEthernet 1/0/1-24
S1(config-if-range)# switchport access vlan 99
S1(config-if-range)# switchport port-security (mac-addres)
```

switchport mode trunk --> voor trunk naar andere switch
switchport mode access --> voor clients (computer)
