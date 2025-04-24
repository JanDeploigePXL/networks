```
S1# show ip ssh
S1(config)# ip domain-name freedombox.be
S1(config)# crypto key generate rsa
S1(config)# username admin secret pxl
S1(config)# line vty 0 15
S1(config-line)# transport input ssh
S1(config-line)# login local
S1(config-line)# exit
S1(config)# ip ssh version 2
```