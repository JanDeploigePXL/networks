# OSPFv2
## Example
~~~
! ---------- R1 ----------
router ospf 10
 router-id 1.1.1.1
 network 192.168.10.0 0.0.0.255 area 0
 network 10.1.1.0 0.0.0.3 area 0
 network 10.1.1.4 0.0.0.3 area 0
 passive-interface g0/0/0

! ---------- R2 ----------
router ospf 10
 router-id 2.2.2.2
 network 192.168.20.1 0.0.0.0 area 0
 network 10.1.1.2    0.0.0.0 area 0
 network 10.1.1.9    0.0.0.0 area 0
 passive-interface g0/0/0

! ---------- R3 ----------
interface g0/0/0
 ip ospf 10 area 0
interface s0/1/0
 ip ospf 10 area 0
interface s0/1/1
 ip ospf 10 area 0
router ospf 10
 router-id 3.3.3.3
 passive-interface g0/0/0
~~~


