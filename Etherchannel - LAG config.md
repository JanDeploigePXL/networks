```
S1(config)# interface range GigabitEthernet 1/0/1-2
S1(config-if-range)# channel-group 1 mode active
S1(config-if-range)# exit
S1(config-if)# interface port-channel 1
S1(config-if)# switchport mode trunk
S1(config-if)# switchport trunk native vlan 99
S1(config-if)# switchport trunk allowed vlan 1,2,20
```
