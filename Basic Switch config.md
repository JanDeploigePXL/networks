```
S1: enable
S1# configure terminal
S1(config)# line console 0
S1(config)# password a_password
S1(config)# login
S1(config)# end
```

```
S1(config)# line vty 0 15
S1(config-if)# password a_password
S1(config-if)# login
S1(config-if)# end
```

### Prevent console messaging interruptions

```
S1(config)# line con 0
S1(config-line)# logging synchronous
```

### Enable telnet

```
S1(config)# line vty 0 15
S1(config-if)# transport input telnet
S1(config-if)# password a_password
S1(config-if)# login
```

### Password for privileged access

```
S1(config)# enable password cisco # plain-text
S1(config)# enable secret cisco # encrypted
```

### No IP domain lookup

```
S1(config)# no ip domain-lookup
```
