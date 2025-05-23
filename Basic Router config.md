# Basic Router Configuration Example

**This file covers basic router setup, including hostname, passwords, interfaces, loopbacks, router-on-a-stick, HSRP, and more.**

---

### Hostname, password-encryption, banner

```
Router# configure terminal
Router(config)# hostname R1
R1(config)# service password-encryption
R1(config)# enable secret class
R1(config)# banner motd # A message #
```
**Explanation:**
- `hostname ...`: Sets the router's hostname.
- `service password-encryption`: Encrypts passwords in the configuration.
- `enable secret ...`: Sets the encrypted enable password.
- `banner motd ...`: Sets the Message of the Day banner.

---

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
**Explanation:**
- `interface ...`: Enters interface configuration mode.
- `ip address ...`: Assigns IPv4 address.
- `ipv6 address ...`: Assigns IPv6 address.
- `description ...`: Adds a description to the interface.
- `no shutdown`: Enables the interface.

---

### Loopback interface

```
R1(config)# interface loopback number 
R1(config-if)# ip address ip-address subnet-mask 
```
**Explanation:**
- `interface loopback ...`: Creates a loopback interface.
- `ip address ...`: Assigns an IP address to the loopback.

Example:
```
R1(config)# interface loopback 0
R1(config-if)# ip address 10.1.1.1 255.255.255.255
```
**Explanation:**
- `interface loopback 0`: Creates a virtual loopback interface (numbered 0).
- `ip address 10.1.1.1 255.255.255.255`: Assigns an IP address to the loopback interface. Loopbacks are always up and are often used for router IDs, management, or testing.

---

### Router on a stick

```
Router(config)# interface gigabitEthernet 0/0/0.75
Router(config-subif)# encapsulation dot1Q 75
```
**Explanation:**
- `interface ... .75`: Creates a subinterface for VLAN 75.
- `encapsulation dot1Q 75`: Enables 802.1Q encapsulation for VLAN 75.

**Note:**  
For router-on-a-stick, you must create a separate subinterface for every VLAN you want to route between. Each subinterface should use a unique VLAN ID and have its own IP address in the corresponding VLAN's subnet.

Example for multiple VLANs:
```
Router(config)# interface gigabitEthernet 0/0/0.10
Router(config-subif)# encapsulation dot1Q 10
Router(config-subif)# ip address 192.168.10.1 255.255.255.0

Router(config)# interface gigabitEthernet 0/0/0.20
Router(config-subif)# encapsulation dot1Q 20
Router(config-subif)# ip address 192.168.20.1 255.255.255.0
```

---

### Fysical ip adres for router

```
Router(config-subif)# ip address 172.17.7.66 255.255.255.240
```
**Explanation:**
- `ip address ...`: Assigns an IP address to the subinterface.

---

### HSRP

```
Router(config-subif)# standby version 2
Router(config-subif)# standby 75 ip 172.17.1.1
```
**Explanation:**
- `standby version 2`: Uses HSRP version 2.
- `standby 75 ip ...`: Sets the HSRP group and virtual IP.

---

### Priority

```
Router(config-subif)# standby 75 priority 250
Router(config-subif)# standby 75 preempt
Router(config-subif)# end
```
**Explanation:**
- `standby 75 priority ...`: Sets HSRP priority.
- `standby 75 preempt`: Allows router to take over if higher priority.
- `end`: Exits configuration mode.

---

### NATIVE VLAN

```
Router(config)# interface gigabitEthernet 0/0/0.99
Router(config-subif)# encapsulation dot1Q 99 native
```
**Explanation:**
- `encapsulation dot1Q 99 native`: Sets VLAN 99 as the native VLAN on the subinterface.

---

### BRING UP THE PORT

```
int gigabitEthernet 0/0/0
no shutdown
```
**Explanation:**
- `no shutdown`: Enables the physical interface.

---

### SET IP OF ROUTER

```
conf t
int gig 0/0/1
ip address 10.199.65.220 255.255.255.225
no shut
exit
```
**Explanation:**
- `ip address ...`: Assigns an IP address.
- `no shut`: Enables the interface.

---

### Verify Router Configuration

```
R1# show running-config
R1# show interfaces
R1# show ip interface brief
R1# show ipv6 interface brief
R1# show interfaces description
R1# show interfaces loopback 0
R1# show standby brief
```
**Explanation:**
- `show running-config`: Displays the current configuration.
- `show interfaces`: Shows detailed interface status.
- `show ip interface brief`: Lists IPv4 interfaces and status.
- `show ipv6 interface brief`: Lists IPv6 interfaces and status.
- `show interfaces description`: Shows interface descriptions.
- `show interfaces loopback 0`: Shows loopback interface details.
- `show standby brief`: Displays HSRP status.


