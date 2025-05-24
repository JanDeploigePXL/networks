## Standard **Named** IPv4 ACLs – Quick-Reference Cheatsheet


### 1  Why use a named ACL?

| Advantage    | What it means                                                                                                             |
| ------------ | ------------------------------------------------------------------------------------------------------------------------- |
| **Readable** | `BLOCK-WEBSERVER` is clearer than `access-list 1`.                                                                        |
| **Editable** | You can add, delete, or reorder individual lines without removing the whole list (`ip access-list standard <name>` mode). |
| **Scalable** | Up to 4 096 names vs. only 198 numbered ranges (1-99, 1300-1999).                                                         |

---

### 2  Configuration Workflow (Standard ACL)

```text
ip access-list standard <ACL-NAME>
 deny   <source> <wildcard>
 [sequence-number] permit <…>
 exit
interface <int>
 ip access-group <ACL-NAME> {in | out}
```
> *Sequence numbers (10, 20, 30 …) are optional; IOS auto-increments by 10 if you omit them.*
#### Example
~~~
R1(config)# ip access-list standard BLOCK-40-TO-SRV
R1(config-std-nacl)# 10 remark *** deny whole /24 except .50 ***
R1(config-std-nacl)# 20 permit host 192.168.40.50    ! exception
R1(config-std-nacl)# 30 deny   192.168.40.0 0.0.0.255 ! block rest
R1(config-std-nacl)# 40 permit any                    ! everything else
R1(config-std-nacl)# exit
~~~
~~~
R1(config)# interface g0/1
R1(config-if)# ip access-group BLOCK-40-TO-SRV out
R1(config-if)# end
~~~

### 3  Editing a Named ACL On-the-Fly

| Task                      | Command in ACL-config mode             |
| ------------------------- | -------------------------------------- |
| **Insert a new ACE**      | `15 deny host 192.168.11.99`           |
| **Remove an ACE**         | `no 20`                                |
| **Show sequence numbers** | `do show access-lists BLOCK-11-TO-WEB` |

Example: add a single host exception so PC 192.168.11.99 can still reach the WebServer:

```text
R2# conf t
R2(config)# ip access-list standard BLOCK-11-TO-WEB
R2(config-std-nacl)# 15 permit host 192.168.11.99
R2(config-std-nacl)# exit
```

ACE order now:

```
10 deny 192.168.11.0 0.0.0.255
15 permit host 192.168.11.99
20 permit any
```

---

### 5  Verification Commands

| Purpose                      | Command                    |                                            |
| ---------------------------- | -------------------------- | ------------------------------------------ |
| Display named ACL & counters | `show access-lists <name>` |                                            |
| See interface bindings       | \`show ip interface <int>  | include access\`                           |
| Confirm saved to NVRAM       | \`show run                 | section BLOCK-\` (filter on your ACL name) |

---

