# NAT Configuration Example

**NAT (Network Address Translation) allows devices on a private network to communicate over the internet by translating private IP addresses to public IP addresses. NAT also enables the use of multiple public IPs, providing flexibility and conserving address space.**

Below are example configurations for NAT (Network Address Translation) and PAT (Port Address Translation), along with explanations for each command.

---

## Interface Configuration

```
interface GigabitEthernet0/0
 ip address 192.168.1.1 255.255.255.0
 ip nat inside

interface GigabitEthernet0/1
 ip address 203.0.113.2 255.255.255.0
 ip nat outside
```
**Explanation:**
- `interface GigabitEthernet0/0` and `interface GigabitEthernet0/1`: Select the interfaces to configure.
- `ip address ...`: Assigns IP addresses to the interfaces.
- `ip nat inside`: Marks the interface as the "inside" NAT interface (typically the LAN).
- `ip nat outside`: Marks the interface as the "outside" NAT interface (typically the WAN/Internet).

---

## NAT Pool Configuration

```
ip nat pool MYPOOL 203.0.113.10 203.0.113.20 netmask 255.255.255.0
ip nat inside source list 1 pool MYPOOL
```
**Explanation:**
- `ip nat pool MYPOOL ...`: Defines a pool of public IP addresses (203.0.113.10 to 203.0.113.20) for NAT.
- `ip nat inside source list 1 pool MYPOOL`: Translates source addresses from access list 1 to addresses in the pool.

---

# PAT (Port Address Translation)

**PAT (Port Address Translation), also known as NAT overload, allows multiple devices on a local network to be mapped to a single public IP address but with a different port number for each session. This enables many devices to share one public IP for internet access, conserving public IP addresses.**

```
access-list 1 permit 192.168.1.0 0.0.0.255
ip nat inside source list 1 interface GigabitEthernet0/1 overload
```
**Explanation:**
- `access-list 1 permit 192.168.1.0 0.0.0.255`: Permits traffic from the 192.168.1.0/24 network.
- `ip nat inside source list 1 interface GigabitEthernet0/1 overload`: Enables PAT (NAT overload), allowing multiple internal hosts to share a single public IP using different ports.

---

# CHECK

```
show ip nat translations
show ip nat statistics
show running-config | include nat
```
**Explanation:**
- `show ip nat translations`: Displays current NAT translations.
- `show ip nat statistics`: Shows NAT operation statistics.
- `show running-config | include nat`: Shows NAT-related configuration lines.