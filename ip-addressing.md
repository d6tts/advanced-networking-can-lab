IP Addressing Plan

1. Network Overview

The campus network uses the private address block 10.50.0.0/16.

Each department and network service has its own VLAN and subnet. The default gateway for each VLAN is the HSRP virtual IP address ending in .1.

2. VLAN Addressing

VLAN

Name

Network

Subnet Mask

Gateway

10

Computer Science

10.50.0.0/24

255.255.255.0

10.50.0.1

20

Business

10.50.1.0/24

255.255.255.0

10.50.1.1

30

Engineering

10.50.2.0/24

255.255.255.0

10.50.2.1

40

Mathematics and Science

10.50.3.0/24

255.255.255.0

10.50.3.1

50

Humanities

10.50.4.0/24

255.255.255.0

10.50.4.1

60

Arts and Communication

10.50.5.0/24

255.255.255.0

10.50.5.1

70

Administration

10.50.6.0/24

255.255.255.0

10.50.6.1

80

IT Sandbox

10.50.7.0/24

255.255.255.0

10.50.7.1

90

Internal Servers

10.50.8.0/26

255.255.255.192

10.50.8.1

99

Network Management

10.50.9.0/26

255.255.255.192

10.50.9.1

100

Wireless Clients

10.50.16.0/22

255.255.252.0

10.50.16.1

110

DMZ Servers

10.50.20.0/28

255.255.255.240

10.50.20.1

3. Core Switch Addresses

CORE1 and CORE2 provide redundant routing using HSRP.

VLAN

CORE1 Address

CORE2 Address

HSRP Gateway

10

10.50.0.2

10.50.0.3

10.50.0.1

20

10.50.1.2

10.50.1.3

10.50.1.1

30

10.50.2.2

10.50.2.3

10.50.2.1

40

10.50.3.2

10.50.3.3

10.50.3.1

50

10.50.4.2

10.50.4.3

10.50.4.1

60

10.50.5.2

10.50.5.3

10.50.5.1

70

10.50.6.2

10.50.6.3

10.50.6.1

80

10.50.7.2

10.50.7.3

10.50.7.1

90

10.50.8.2

10.50.8.3

10.50.8.1

99

10.50.9.2

10.50.9.3

10.50.9.1

100

10.50.16.2

10.50.16.3

10.50.16.1

110

10.50.20.3

10.50.20.4

10.50.20.1

CORE1 is configured as the preferred active HSRP switch.

4. Server Addressing

Internal servers use static IP addresses in VLAN 90.

Device

IP Address

Gateway

APP-SRV1 (DHCP/DNS)

10.50.8.10

10.50.8.1

APP-SRV2

10.50.8.11

10.50.8.1

FILE-SRV1

10.50.8.12

10.50.8.1

FILE-SRV2

10.50.8.13

10.50.8.1

PRINT-SRV

10.50.8.14

10.50.8.1

NAS

10.50.8.15

10.50.8.1

The public web server is located in VLAN 110:

Device

IP Address

Gateway

PUBLIC-WEB

10.50.20.2

10.50.20.1

The DNS record www.college.local points to 10.50.20.2.

5. DHCP Configuration

APP-SRV1 provides DHCP services for the department and wireless VLANs.

VLAN

DHCP Starting Address

10

10.50.0.10

20

10.50.1.10

30

10.50.2.10

40

10.50.3.10

50

10.50.4.10

60

10.50.5.10

70

10.50.6.10

80

10.50.7.10

100

10.50.16.10

The DHCP server uses 10.50.8.10 for DNS. Both core switches use DHCP relay through ip helper-address 10.50.8.10.

6. Firewall and ISP Addressing

Device or Interface

IP Address

CAMPUS-FW inside (VLAN 1)

192.168.1.1/24

CORE1 VLAN 1

192.168.1.2/24

CORE2 VLAN 1

192.168.1.3/24

CAMPUS-FW outside (VLAN 2)

203.0.113.2/30

ISP-RTR Gi0/0

203.0.113.1/30

The ASA firewall performs NAT/PAT for the campus network and uses the ISP router as its default route.

7. Addressing and Routing Notes

Department devices receive addresses through DHCP.

Servers and infrastructure devices use static addresses.

HSRP provides redundant default gateways.

The core switches provide inter-VLAN routing.

Distribution and access switches use VLAN trunks to carry campus traffic.

The ASA firewall handles outbound NAT/PAT.

The DMZ contains the public web server.

ACLs restrict unauthorized communication between VLANs.
