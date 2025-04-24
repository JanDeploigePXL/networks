```
S1# configure terminal
S1(config)# interface GigabitEthernet 1/0/1
S1(config-if)# duplex full
S1(config-if)# speed 100
S1(config-if)# end
S1# copy running-config startup-config
```