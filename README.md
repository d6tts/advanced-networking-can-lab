# Advanced Networking – Campus Area Network Design

## Project Overview

This project involves designing and implementing a Campus Area Network (CAN) for a college campus consisting of three academic buildings and an outdoor common area.

The network will provide connectivity for students, faculty, staff, and administrators across all three buildings.

## Campus Network Design

The campus network will include:

- Building A – Central Administration and Technology
- Building B – Science and Engineering
- Building C – Humanities and Communication
- Central server room located in Building A
- Campus-wide wireless network
- Internet connectivity
- Firewall and DMZ security
- Multiple VLANs for network separation

## Network Technologies

The project will use the following technologies:

- IPv4 addressing and CIDR/VLSM subnetting
- VLANs and trunking
- Inter-VLAN routing
- OSPF routing
- DHCP and DNS
- NAT/PAT
- Access Control Lists (ACLs)
- Wireless networking
- Firewall and DMZ configuration

## Network Addressing

The assigned private IPv4 address block is:

`10.50.0.0/16`

Individual subnets will be created for academic departments, administration, servers, wireless clients, and other network services.

## Software and Tools

- Cisco Packet Tracer
- GitHub
- GitHub Copilot

## Project Documentation

The repository will contain:

- `README.md` – Project overview
- `copilot-design-log.md` – Documentation of AI-assisted design
- `ip-addressing.md` – VLAN and subnetting plan
- `verification.md` – Network connectivity and testing results
- Cisco Packet Tracer project file (`.pkt`)

## Course

IST 4210 (80) - ADV. NETWORKING & SECURITY

Advanced Campus Area Network Design

Project Overview

This project is a simulated campus area network designed for a college with three buildings and an outdoor common area. The network supports students, faculty, administration, IT staff, and campus services.

The network was designed and configured using Cisco Packet Tracer.

Network Features

Three campus buildings connected through a central network.

Redundant Layer 3 core switches using HSRP.

VLAN segmentation for departments and network services.

Inter-VLAN routing.

DHCP for wired and wireless clients.

Internal DNS server.

Public-facing web server in a DMZ network.

ASA firewall with NAT/PAT.

Wireless access using the shared College-Campus SSID and WPA2-PSK.

Access control lists (ACLs) to restrict unauthorized network traffic.

VLAN and IP Addressing

VLAN

Department or Purpose

Network

10

Computer Science

10.50.0.0/24

20

Business

10.50.1.0/24

30

Engineering

10.50.2.0/24

40

Mathematics and Science

10.50.3.0/24

50

Humanities

10.50.4.0/24

60

Arts and Communication

10.50.5.0/24

70

Administration

10.50.6.0/24

80

IT Sandbox

10.50.7.0/24

90

Internal Servers

10.50.8.0/26

99

Network Management

10.50.9.0/26

100

Wireless Clients

10.50.16.0/22

110

DMZ Servers

10.50.20.0/28

Network Security

The network uses VLANs and ACLs to separate departments and protect important resources. Department devices can access approved services, while unauthorized communication between departments is restricted.

The IT Sandbox and wireless networks have additional access restrictions. The DMZ contains the public web server, separated from internal campus resources.

Project Files

Advanced-Campus-Network.pkt – Cisco Packet Tracer network project.

README.md – Project overview and network design.

ip-addressing.md – IP addressing and subnet information.

copilot-design-log.md – Documentation of AI assistance and design decisions.

verification.md – Network testing and verification results.

Verification

The network was tested for DHCP assignment, DNS resolution, website access, routing, wireless connectivity, and security restrictions. The tested connections behaved as expected.

Limitations

The ISP connection is simulated in Packet Tracer. The project demonstrates the network design and configuration but does not represent a live connection to the public Internet.
