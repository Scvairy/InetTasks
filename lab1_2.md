### Router 1
	enable
	conf t
	hostname Router1

	interface FastEthernet0/0
	 ip address 192.168.10.1 255.255.255.252
	 no sh

	interface FastEthernet0/1
	 ip address 10.30.1.1 255.255.255.0
	 no sh

	interface FastEthernet1/0
	 ip address 192.168.1.1 255.255.255.0
	 no sh

	router rip
	 network 10.0.0.0
	 network 192.168.1.0
	 network 192.168.10.0

	exit
	write

#### Router1#sh ip route
	Codes: C - connected, S - static, I - IGRP, R - RIP, M - mobile, B - BGP
	       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
	       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
	       E1 - OSPF external type 1, E2 - OSPF external type 2, E - EGP
	       i - IS-IS, L1 - IS-IS level-1, L2 - IS-IS level-2, ia - IS-IS inter area
	       * - candidate default, U - per-user static route, o - ODR
	       P - periodic downloaded static route

	Gateway of last resort is not set

	     10.0.0.0/24 is subnetted, 1 subnets
	C       10.30.1.0 is directly connected, FastEthernet0/1
	C    192.168.1.0/24 is directly connected, FastEthernet1/0
	R    192.168.2.0/24 [120/1] via 192.168.10.2, 00:00:17, FastEthernet0/0
	R    192.168.3.0/24 [120/2] via 192.168.10.2, 00:00:17, FastEthernet0/0
	     192.168.10.0/30 is subnetted, 2 subnets
	C       192.168.10.0 is directly connected, FastEthernet0/0
	R       192.168.10.4 [120/1] via 192.168.10.2, 00:00:17, FastEthernet0/0


#### Router1#sh ip int brief
	Interface              IP-Address      OK? Method Status                Protocol 
	FastEthernet0/0        192.168.10.1    YES manual up                    up 
	FastEthernet0/1        10.30.1.1       YES manual up                    up 
	FastEthernet1/0        192.168.1.1     YES manual up                    up 
	FastEthernet1/1        unassigned      YES unset  administratively down down 
	Vlan1                  unassigned      YES unset  administratively down down

### Router 2
	enable
	conf t
	hostname Router2

	interface FastEthernet0/0
	 ip address 192.168.10.2 255.255.255.252 
	 no sh

	interface FastEthernet0/1
	 ip address 192.168.10.5 255.255.255.252
	 no sh

	interface FastEthernet1/0
	 ip address 192.168.2.1 255.255.255.0
	 no sh

	router rip
	 network 192.168.2.0
	 network 192.168.10.0

	exit
	write

#### Router2#sh ip route
	Codes: C - connected, S - static, I - IGRP, R - RIP, M - mobile, B - BGP
	       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
	       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
	       E1 - OSPF external type 1, E2 - OSPF external type 2, E - EGP
	       i - IS-IS, L1 - IS-IS level-1, L2 - IS-IS level-2, ia - IS-IS inter area
	       * - candidate default, U - per-user static route, o - ODR
	       P - periodic downloaded static route

	Gateway of last resort is not set

	R    10.0.0.0/8 [120/1] via 192.168.10.1, 00:00:25, FastEthernet0/0
	R    192.168.1.0/24 [120/1] via 192.168.10.1, 00:00:25, FastEthernet0/0
	C    192.168.2.0/24 is directly connected, FastEthernet1/0
	R    192.168.3.0/24 [120/1] via 192.168.10.6, 00:00:06, FastEthernet0/1
	     192.168.10.0/30 is subnetted, 2 subnets
	C       192.168.10.0 is directly connected, FastEthernet0/0
	C       192.168.10.4 is directly connected, FastEthernet0/1


#### Router2#sh ip int brief
	Interface              IP-Address      OK? Method Status                Protocol 
	FastEthernet0/0        192.168.10.2    YES manual up                    up 
	FastEthernet0/1        192.168.10.5    YES manual up                    up 
	FastEthernet1/0        192.168.2.1     YES manual up                    up 
	FastEthernet1/1        unassigned      YES unset  administratively down down 
	Vlan1                  unassigned      YES unset  administratively down down

### Router 3
	enable
	conf t
	hostname Router3

	interface FastEthernet0/0
	 ip address 10.30.1.2 255.255.255.0
	 no sh

	interface FastEthernet0/1
	 ip address 192.168.10.6 255.255.255.252
	 no sh

	interface FastEthernet1/0
	 ip address 192.168.3.1 255.255.255.0
	 no sh

	router rip
	 network 192.168.3.0
	 network 192.168.10.0

	exit
	write

#### Router3#sh ip route
	Codes: C - connected, S - static, I - IGRP, R - RIP, M - mobile, B - BGP
	       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
	       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
	       E1 - OSPF external type 1, E2 - OSPF external type 2, E - EGP
	       i - IS-IS, L1 - IS-IS level-1, L2 - IS-IS level-2, ia - IS-IS inter area
	       * - candidate default, U - per-user static route, o - ODR
	       P - periodic downloaded static route

	Gateway of last resort is not set

	     10.0.0.0/24 is subnetted, 1 subnets
	C       10.30.1.0 is directly connected, FastEthernet0/0
	R    192.168.1.0/24 [120/2] via 192.168.10.5, 00:00:01, FastEthernet0/1
	R    192.168.2.0/24 [120/1] via 192.168.10.5, 00:00:01, FastEthernet0/1
	C    192.168.3.0/24 is directly connected, FastEthernet1/0
	     192.168.10.0/30 is subnetted, 2 subnets
	R       192.168.10.0 [120/1] via 192.168.10.5, 00:00:01, FastEthernet0/1
	C       192.168.10.4 is directly connected, FastEthernet0/1


#### Router3#sh ip int brief
	Interface              IP-Address      OK? Method Status                Protocol 
	FastEthernet0/0        10.30.1.2       YES manual up                    up 
	FastEthernet0/1        192.168.10.6    YES manual up                    up 
	FastEthernet1/0        192.168.3.1     YES manual up                    up 
	FastEthernet1/1        unassigned      YES unset  administratively down down 
	Vlan1                  unassigned      YES unset  administratively down down

