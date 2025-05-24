# Basic Switch Configuration Example

**This file covers basic switch setup, including console and VTY access, passwords, disabling DNS lookup, and more.**

---

```
S1: enable
S1# configure terminal
S1(config)# line console 0
S1(config)# password a_password
S1(config)# login
S1(config)# end
```
**Explanation:**
- `line console 0`: Enters console line configuration.
- `password ...`: Sets the console password.
- `login`: Enables password checking at login.

---

```
S1(config)# line vty 0 15
S1(config-if)# password a_password
S1(config-if)# login
S1(config-if)# end
```
**Explanation:**
- `line vty 0 15`: Enters VTY (remote access) line configuration.
- `password ...`: Sets the VTY password.
- `login`: Enables password checking at login.

---

### Prevent console messaging interruptions

```
S1(config)# line con 0
S1(config-line)# logging synchronous
```
**Explanation:**
- `logging synchronous`: Prevents console messages from interrupting command entry.

---

### Enable telnet

```
S1(config)# line vty 0 15
S1(config-if)# transport input telnet
S1(config-if)# password a_password
S1(config-if)# login
```
**Explanation:**
- `transport input telnet`: Enables Telnet access on VTY lines.

---

### Password for privileged access

```
S1(config)# enable password cisco # plain-text
S1(config)# enable secret cisco # encrypted
```
**Explanation:**
- `enable password ...`: Sets a plain-text enable password.
- `enable secret ...`: Sets an encrypted enable password.

---

### No IP domain lookup

```
S1(config)# no ip domain-lookup
```
**Explanation:**
- `no ip domain-lookup`: Disables DNS lookup for mistyped commands.

---

### Verify Switch Configuration

```
S1# show running-config
S1# show line
S1# show users
S1# show version
```
**Explanation:**
- `show running-config`: Displays the current configuration.
- `show line`: Shows line (console/VTY) status.
- `show users`: Lists users currently connected.
- `show version`: Displays switch software and hardware information.
