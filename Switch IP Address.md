# Switch IP Address and Related Configuration

**This file covers how to configure IP addresses, default gateway, IPv6, DNS, domain name, and NTP on a switch. These settings are essential for switch management and network connectivity.**

---

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
**Explanation:**
- `interface vlan 99`: Enters interface configuration for VLAN 99 (SVI).
- `ip address ...`: Assigns an IPv4 address to the SVI.
- `ipv6 address ...`: Assigns an IPv6 address to the SVI.
- `no shutdown`: Enables the interface.
- `copy running-config startup-config`: Saves the configuration.

---

### Default gateway

```
S1# configure terminal
S1(config)# ip default-gateway 172.17.99.1
S1(config)# end
S1# copy running-config startup-config
```
**Explanation:**
- `ip default-gateway ...`: Sets the default gateway for the switch.

---

### Link local IPv6

```
S1(config)# interface vlan99
S1(config-if)# ipv6 address FE80::2 link-local
```
**Explanation:**
- `ipv6 address ... link-local`: Assigns a link-local IPv6 address to the interface.

---

### Verify config

```
S1# show ip interface brief
S1# show ipv6 interface brief
S1# show running-config interface vlan 99
S1# show running-config | include ip default-gateway
S1# show hosts
S1# show ntp status
```
**Explanation:**
- `show ip interface brief`: Displays summary of IPv4 interfaces.
- `show ipv6 interface brief`: Displays summary of IPv6 interfaces.
- `show running-config interface vlan 99`: Shows the configuration for VLAN 99 interface.
- `show running-config | include ip default-gateway`: Shows the configured default gateway.
- `show hosts`: Displays DNS server configuration.
- `show ntp status`: Shows NTP synchronization status.

---

### DNS

ip name-server 10.199.64.66

**Explanation:**  
- `ip name-server ...`: Configures the DNS server IP address.

---

### Domain

ip domain name data.labnet.local

**Explanation:**  
- `ip domain name ...`: Sets the domain name for the switch.

---

### NTP

ip ntp 10.199.64.66

**Explanation:**  
- `ip ntp ...`: Configures the NTP server for time synchronization.