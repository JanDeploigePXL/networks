# Static route

**A default static route forwards all traffic destined for unknown networks to a specified next-hop IP address. This is commonly used to direct traffic towards the internet or a central router.**

- `0.0.0.0` (Destination network): This represents any destination IP address (the default route).
- `0.0.0.0` (Subnet mask): This means "match all networks."
- `10.199.65.100` (Next-hop IP): This is the IP address of the next-hop router where traffic should be sent if there is no more specific route in the routing table.

```
R1(config)# ip route 0.0.0.0 0.0.0.0 10.199.65.100
```
**Explanation:**
- `ip route 0.0.0.0 0.0.0.0 10.199.65.100`: Configures a default static route to forward all unknown traffic to 10.199.65.100.

### Verify Static Route

```
R1# show ip route
R1# show running-config | include ip route
```
**Explanation:**
- `show ip route`: Displays the routing table, including static and default routes.
- `show running-config | include ip route`: Shows all static route commands in the configuration.