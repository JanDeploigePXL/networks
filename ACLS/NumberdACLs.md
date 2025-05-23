## NumberdACLS

### 1  Planning – 3-minute checklist

| Question                          | Decide                                                                                 | Notes                                                                             |
| --------------------------------- | -------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| **What traffic must be blocked?** | • 192.168.11.0/24 → 192.168.20.254 (WebServer) <br>• 192.168.10.0/24 → 192.168.30.0/24 | Everything else allowed                                                           |
| **Where to place the list?**      | *Standard* ACL → **closest to the destination**                                        | • On **R2 G0/0 out** (toward WebServer) <br>• On **R3 G0/0 out** (toward PC3 LAN) |
| **Number to use?**                | 1–99 (or 1300–1999). Lab uses **1** on each router                                     | Numbering is local to the router, duplicates OK                                   |

---

### 2  Build the ACL

```text
access-list <#> deny   <source> <wildcard>
access-list <#> permit <any | source wildcard>
```

---

### 3  Apply the ACL to an interface

```text
interface <int>
 ip access-group <#> {in | out}
```

---

### 4  Quick-Verify Commands

| Purpose                            | Command                  |                       |
| ---------------------------------- | ------------------------ | --------------------- |
| Show ACEs and counters             | `show access-lists`      |                       |
| Check which interface has the list | \`show ip interface g0/0 | include access\`      |
| Confirm saved config               | \`show run               | section access-list\` |

---
