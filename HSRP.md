# HSRP Configuration Example

**HSRP (Hot Standby Router Protocol) provides network redundancy for IP networks by ensuring that user traffic immediately and transparently recovers from first hop failures in a router or switch. HSRP allows two or more routers to work together to present the appearance of a single virtual router to the hosts on the LAN.**

Below is an example configuration for HSRP, with explanations for each command.

---

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
**Explanation:**
- `enable`: Enters privileged EXEC mode.
- `configure terminal`: Enters global configuration mode.
- `interface gigabitEthernet 0/1`: Selects the interface to configure HSRP.
- `standby 1 ip <virtual_ip_address>`: Sets the HSRP group (1) and assigns the virtual IP address shared by the routers.
- `standby 1 priority <priority_value>`: Sets the HSRP priority for this router (higher value = higher priority to become active).
- `standby 1 preempt`: Allows the router to take over as active if its priority becomes higher than the current active router.
- `end`: Exits configuration mode.
- `write memory`: Saves the configuration to NVRAM.

---

## Example: HSRP Configuration for R1 and R2

Suppose you have two routers, R1 and R2, connected to the same LAN segment. The LAN network is 192.168.10.0/24. The routers' physical IPs are 192.168.10.2 (R1) and 192.168.10.3 (R2). The shared virtual IP for HSRP is 192.168.10.1.

**R1 Configuration (Active Router):**
```
interface gigabitEthernet 0/1
 ip address 192.168.10.2 255.255.255.0
 standby 1 ip 192.168.10.1
 standby 1 priority 110
 standby 1 preempt
```

**R2 Configuration (Standby Router):**
```
interface gigabitEthernet 0/1
 ip address 192.168.10.3 255.255.255.0
 standby 1 ip 192.168.10.1
 standby 1 priority 100
 standby 1 preempt
```

**Explanation:**
- Both routers use the same HSRP group (1) and virtual IP (192.168.10.1).
- R1 has a higher priority (110) and will be the active router.
- R2 has a lower priority (100) and will be the standby router.
- Both use `preempt` to allow a higher-priority router to take over if it comes online.

---

### Verify HSRP

```
R1# show standby
R1# show standby brief
R1# show running-config | include standby
```
**Explanation:**
- `show standby`: Displays detailed HSRP status.
- `show standby brief`: Shows a summary of HSRP groups and states.
- `show running-config | include standby`: Shows HSRP configuration lines.