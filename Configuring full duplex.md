# Configuring Full Duplex and Speed

**You can manually configure the duplex and speed settings on switch interfaces for optimal performance or to resolve compatibility issues.**

Below is an example configuration, with explanations for each command.

---

```
S1# configure terminal
S1(config)# interface GigabitEthernet 1/0/1
S1(config-if)# duplex full
S1(config-if)# speed 100
S1(config-if)# end
S1# copy running-config startup-config
```
**Explanation:**
- `interface GigabitEthernet 1/0/1`: Selects the interface to configure.
- `duplex full`: Sets the interface to full duplex mode.
- `speed 100`: Sets the interface speed to 100 Mbps.
- `copy running-config startup-config`: Saves the configuration.

### Verify Duplex and Speed

```
S1# show interfaces status
S1# show interfaces GigabitEthernet 1/0/1
```
**Explanation:**
- `show interfaces status`: Displays status, speed, and duplex for all interfaces.
- `show interfaces GigabitEthernet 1/0/1`: Shows detailed information for a specific interface, including duplex and speed.

**About Duplex:**
- **Duplex** refers to how data is transmitted and received on a network interface.
    - **Half duplex**: Data can be sent or received, but not both at the same time (like a walkie-talkie).
    - **Full duplex**: Data can be sent and received simultaneously (like a telephone conversation). This is preferred for modern networks as it doubles potential throughput and avoids collisions.