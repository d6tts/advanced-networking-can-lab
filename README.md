# Advanced Networking – Campus Area Network Design

## Project Overview

This project is a simulated Campus Area Network (CAN) designed for a college campus with three academic buildings and an outdoor common area. The network supports students, faculty, staff, administration, and IT services.

The network was designed and configured using Cisco Packet Tracer for IST 4210 – Advanced Networking & Security.

## Campus Layout

- **Building A:** Central Administration and Technology
- **Building B:** Science and Engineering
- **Building C:** Humanities and Communication
- **Server Room:** Located in Building A
- **Outdoor Area:** Campus-wide wireless coverage

## Campus Endpoint Deployment

The completed campus network supports 158 total endpoints across three buildings.

| Building | Lab Computers | Classroom Computers | Office Workstations | Printers | Total |
|---|---:|---:|---:|---:|---:|
| Building A | 30 | 10 | 18 | 18 | 76 |
| Building B | 15 | 9 | 14 | 14 | 52 |
| Building C | 0 | 8 | 11 | 11 | 30 |
| **Total** | **45** | **27** | **43** | **43** | **158** |

Each building has two floors with dedicated access switching. Department devices are assigned to their respective VLANs.

## Network Features

- Redundant Layer 3 core switches using HSRP.
- VLAN segmentation for departments and network services.
- Inter-VLAN routing using switched virtual interfaces (SVIs).
- DHCP services for wired and wireless clients.
- Internal DNS server.
- Public-facing web server in a separate DMZ VLAN.
- Cisco ASA firewall with NAT/PAT.
- Wireless access using the shared `College-Campus` SSID and WPA2 security.
- Access control lists (ACLs) to restrict unauthorized network traffic.
- Distribution and access switches connecting the three buildings.

## Routing and Network Design

The final Packet Tracer configuration uses:

- Layer 3 core switches for inter-VLAN routing.
- HSRP to provide redundant default gateways.
- Static default routes from the core switches toward the ASA firewall.
- A simulated ISP connection through an external router.

OSPF was considered during the initial design, but it was not configured in the final Packet Tracer version.

## VLAN and IP Addressing

The assigned private address block is `10.50.0.0/16`.

| VLAN | Department or Purpose | Network |
|---|---|---|
| 10 | Computer Science | 10.50.0.0/24 |
| 20 | Business | 10.50.1.0/24 |
| 30 | Engineering | 10.50.2.0/24 |
| 40 | Mathematics and Science | 10.50.3.0/24 |
| 50 | Humanities | 10.50.4.0/24 |
| 60 | Arts and Communication | 10.50.5.0/24 |
| 70 | Administration | 10.50.6.0/24 |
| 80 | IT Sandbox | 10.50.7.0/24 |
| 90 | Internal Servers | 10.50.8.0/26 |
| 99 | Network Management | 10.50.9.0/26 |
| 100 | Wireless Clients | 10.50.16.0/22 |
| 110 | DMZ Servers | 10.50.20.0/28 |

The HSRP virtual gateway address is `.1` for the VLANs listed above.

## Servers and Services

The internal server network includes:

- APP-SRV1 – DHCP and DNS services
- APP-SRV2 – Application server
- FILE-SRV1 – Primary file server
- FILE-SRV2 – Backup file server
- PRINT-SRV – Print services
- NAS – Network storage

The DMZ contains a public web server at `10.50.20.2`. The internal DNS server resolves `www.college.local` to this address.

## Network Security

VLANs and ACLs are used to separate departments and restrict communication between network segments.

Security measures include:

- Department VLAN isolation.
- Additional restrictions for the IT Sandbox network.
- Wireless client access restrictions.
- Network management traffic restrictions.
- DMZ separation for the public web server.
- ASA firewall and NAT/PAT configuration.

## Testing and Verification

The network was tested in Packet Tracer for:

- DHCP address assignment.
- DNS name resolution.
- Internal website access.
- Inter-VLAN routing.
- Wireless connectivity.
- Department-to-department traffic restrictions.
- IT Sandbox access restrictions.
- Simulated ISP connectivity.

The results of these tests are documented in `verification.md`.

## Project Files

- `Advanced-Campus-Network.pkt` – Cisco Packet Tracer network project.
- `README.md` – Project overview and network design.
- `ip-addressing.md` – VLAN and IP addressing plan.
- `copilot-design-log.md` – Documentation of AI-assisted design decisions.
- `verification.md` – Network testing and verification results.

## Limitations

The ISP connection is simulated in Packet Tracer and does not provide a live connection to the public Internet. The DMZ web server was tested for internal campus access, but external inbound access was not verified.

Some planned campus infrastructure and security equipment are not fully modeled in the final Packet Tracer simulation.

## Course Information

**IST 4210 (80) – Advanced Networking & Security**

**Project:** AI-Assisted Campus Area Network Design
