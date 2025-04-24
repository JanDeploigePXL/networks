```
Router1> enable
Router1# configure terminal
Router1(config)# interface gigabitEthernet 0/1
Router1(config-if)# standby 1 ip <virtual_ip_address>
Router1(config-if)# standby 1 priority <priority_value>
Router1(config-if)# standby 1 preempt
Router1(config-if)# end
Router1# write memory
```