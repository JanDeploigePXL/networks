# Spanning Tree Configuration Example

**Spanning Tree Protocol (STP) prevents loops in a switched network by blocking redundant paths. Rapid PVST+ is a Cisco enhancement for faster convergence.**

Below is an example configuration for STP, with explanations for each command.

---

```
spanning-tree vlan 2
spanning-tree mode rapid-pvst
spanning-tree vlan 2 root primary
```
**Explanation:**
- `spanning-tree vlan 2`: Enables STP for VLAN 2.
- `spanning-tree mode rapid-pvst`: Sets the spanning tree mode to Rapid PVST+.
- `spanning-tree vlan 2 root primary`: Makes this switch the primary root bridge for VLAN 2.
