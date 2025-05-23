# VLAN Configuration Example

**VLANs (Virtual Local Area Networks) logically segment a network into different broadcast domains. Below are examples for creating VLANs, assigning ports, and configuring trunks, with explanations.**

---

### VLAN NAME

```
S1(config)# vlan 20
S1(config-vlan)# name management
S1(config-vlan)# end
```
**Explanation:**
- `vlan 20`: Creates VLAN 20.
- `name management`: Names the VLAN "management".

---

### VLAN PORTS

```
S1(config)# interface (range) 1/0/1(-10)
S1(config-if)# switchport mode access
S1(config-if)# switchport access vlan 20
S1(config-if)# end
```
**Explanation:**
- `switchport mode access`: Sets the port as an access port.
- `switchport access vlan 20`: Assigns the port to VLAN 20.

---

### VLAN TRUNK

```
S1(config)# interface 1/0/1
S1(config-if)# switchport mode trunk
S1(config-if)# switchport trunk allowed vlan 10,20,30,40
S1(config-if)# switchport trunk native vlan 99
S1(config-if)# end
```
**Explanation:**
- `switchport mode trunk`: Sets the port as a trunk.
- `switchport trunk allowed vlan ...`: Specifies which VLANs are allowed on the trunk.
- `switchport trunk native vlan 99`: Sets VLAN 99 as the native VLAN.

---

### Assigning ports

```
S1(config)# interface range gigabitEthernet 1/0/1-24
S1(config-if-range)# switchport access vlan 99
S1(config-if-range)# switchport port-security (mac-addres)
```
**Explanation:**
- `switchport access vlan 99`: Assigns the ports to VLAN 99.
- `switchport port-security ...`: Enables port security (optionally with a specific MAC address).

---

switchport mode trunk --> voor trunk naar andere switch  
switchport mode access --> voor clients (computer)

**Explanation:**  
- Use trunk mode for uplinks between switches.  
- Use access mode for end devices.

---

### Verify VLANs and Ports

```
S1# show vlan brief
S1# show interfaces status
S1# show interfaces trunk
S1# show running-config interface [interface]
S1# show port-security interface [interface]
```
**Explanation:**
- `show vlan brief`: Lists all VLANs and assigned ports.
- `show interfaces status`: Displays status of all switch interfaces.
- `show interfaces trunk`: Shows trunk ports and allowed VLANs.
- `show running-config interface [interface]`: Shows configuration for a specific interface.
- `show port-security interface [interface]`: Displays port security status for an interface.
