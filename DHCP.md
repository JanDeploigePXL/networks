# DHCP Relay Example

**DHCP relay allows routers to forward DHCP requests from clients on one subnet to a DHCP server on another subnet. This is useful when the DHCP server is not on the same local network as the clients. The `ip helper-address` command is used to specify the address of the DHCP server to which requests should be forwarded.**

Below is an example configuration for DHCP relay, with explanations for each command.

---

```
int gig 0/0/0.77
ip helper-address 10.199.64.66
```
**Explanation:**
- `int gig 0/0/0.77`: Enters interface configuration mode for interface GigabitEthernet 0/0/0.77.
- `ip helper-address 10.199.64.66`: Configures the router to forward UDP broadcasts (such as DHCP requests) received on this interface to the DHCP server at 10.199.64.66.

---

### Verify DHCP Relay

```
R1# show running-config interface gigabitEthernet 0/0/0.77
R1# show ip interface gigabitEthernet 0/0/0.77
R1# debug ip dhcp server packet
```
**Explanation:**
- `show running-config interface ...`: Shows the configuration for the interface.
- `show ip interface ...`: Displays interface status and helper addresses.
- `debug ip dhcp server packet`: (Optional) Debugs DHCP packets for troubleshooting.

---

**Note:**  
Yes, you need to configure `ip helper-address` on every interface (subnet) where you want DHCP clients to reach a remote DHCP server. Each subnet interface should have the appropriate `ip helper-address` command pointing to the DHCP server.