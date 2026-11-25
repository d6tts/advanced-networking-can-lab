# GitHub Copilot Design Log

## Interaction 1 – Campus Endpoint Inventory

### Prompt

I am designing a college campus network with three two-story buildings.

Building A:
20 lab computers, 10 lab computers, 10 classroom computers, 18 office workstations, and 18 printers.

Building B:
15 lab computers, 9 classroom computers, 14 office workstations, and 14 printers.

Building C:
8 classroom computers, 11 office workstations, and 11 printers.

Calculate the total wired endpoints for each building and the entire campus. Recommend an appropriate number of access switches and explain your reasoning. Include room for future expansion.
### Copilot Recommendation

| Building | Wired endpoints |
|---|---:|
| A | 76 |
| B | 52 |
| C | 30 |
| **Campus total** | **158** |

A practical starting point is **six access switches**, with at least one in each floor’s wiring closet: **two 48-port switches in A, two 48-port switches in B, and two 24-port switches in C**. That provides 96 ports in A, 96 in B, and 48 in C—**82 spare ports total** for growth (20, 44, and 18 spare, respectively).

This assumes endpoint placement on each floor fits within that floor’s switch capacity. Confirm the floor-by-floor counts and cable distances before ordering; uneven distributions may require different port sizes or additional switches.
### My Evaluation

I accept Copilot's recommendation of six access switches. The endpoint calculations are correct, with 76 devices in Building A, 52 in Building B, and 30 in Building C. This gives the campus a total of 158 wired endpoints.

### Technical Reason

The six switches provide 240 total ports, leaving 82 spare ports for future expansion. This gives each building enough starting capacity for its current devices. However, I will need to check the number of devices on each floor to make sure the switches are placed correctly and that no floor runs out of ports.

## Interaction 2 – Campus Network Topology

### Prompt

I am designing a Campus Area Network (CAN) in Cisco Packet Tracer for a college with three two-story buildings.

The campus has Building A for administration and technology, Building B for science and engineering, and Building C for humanities and communication. There is also an outdoor common area.

I plan to use two core Layer 3 switches, three building distribution switches, and six floor access switches. The network also needs VLANs, OSPF, a server room, firewall, DMZ, IDS/IPS, wireless access points, and Internet connectivity.

Review my design, recommend appropriate devices, explain how everything should connect, identify improvements, and provide a simple topology diagram. Do not create IP addresses or device configurations yet.

### Copilot Recommendation

Copilot recommended a hierarchical network with two core switches connected to three building distribution switches. Each distribution switch connects to the access switches on both floors of its building.

It also recommended fiber connections between buildings, a firewall between the campus and the ISP, and a separate DMZ containing the public Web server and Proxy server. The internal servers would connect through a dedicated server-room access switch. Wireless access points would connect to the campus switches.

Copilot also recommended using OSPF for internal campus routing and using a default or external route toward the ISP.

### My Evaluation

I accept Copilot's proposed topology with a few improvements. The design separates the core, distribution, and access layers and includes the required connections between all three buildings. I also agree with using two core switches for redundancy and keeping the public servers in a separate DMZ.

### Technical Reason

This design makes the campus network easier to manage and expand. Having two core switches provides another connection if one core switch fails. Fiber connections are a good choice for connecting the buildings. Keeping the DMZ separate from the internal network also helps protect campus computers and servers from outside traffic. I will make sure the firewall controls access between the Internet, DMZ, and internal network.

## Interaction 3 – IP Addressing and VLAN Planning

### Prompt

I asked GitHub Copilot to create an IP addressing plan using the campus network block 10.50.0.0/16. I requested separate subnets for the eight departments, internal servers, network management, wireless clients, the DMZ, and routed connections.

### Copilot Recommendation

Copilot recommended using /24 subnets for the eight department VLANs, /26 subnets for internal servers and network management, a /22 subnet for wireless clients, a /28 subnet for the DMZ, and /30 subnets for point-to-point connections.

### My Evaluation

I accept most of Copilot's IP addressing plan. The subnet calculations are correct, and none of the listed networks overlap. I will make a few changes by assigning VLAN IDs to the additional networks and confirming which connections will use routed links instead of Layer 2 trunks.

### Technical Reason

Using separate subnets for each department helps organize the network and keeps department traffic separated. The larger /24 and /22 networks leave room for future devices. The smaller /30 networks are useful for point-to-point connections because they only need two usable addresses. I also need to plan gateway redundancy so the network can continue working if a core switch fails.

## Interaction 4 – Network Security and Access Control

### Prompt

I asked GitHub Copilot to create a security plan for the campus network. I wanted recommendations for VLAN communication, firewall rules, DMZ protection, wireless security, server protection, and access control lists.

### Copilot Recommendation

Copilot recommended using a default-deny policy. Each department VLAN should only communicate with networks and services it needs. It also recommended isolating the IT Sandbox, protecting internal servers, restricting the management VLAN, and placing public-facing servers in a separate DMZ.

### My Evaluation

I accept Copilot's security recommendations. I will use ACLs to control communication between VLANs and the firewall to protect the campus from outside traffic. I will also keep the IT Sandbox isolated and limit management access to approved IT devices. Guest wireless access should be separated from regular campus wireless access.

### Technical Reason

These security rules help protect the campus network by limiting unnecessary access. Separating departments and servers makes it harder for unauthorized users to reach important information. The firewall and DMZ also allow the public to access the campus website without giving them access to internal computers and servers.

## Interaction 5 – Packet Tracer Configuration Planning

### Prompt

I asked GitHub Copilot to create a beginner-friendly configuration plan for my campus network in Cisco Packet Tracer. I requested example commands for VLANs, trunk ports, inter-VLAN routing, OSPF, DHCP, ACLs, NAT/PAT, and connectivity testing.

### Copilot Recommendation

Copilot recommended configuring the network in stages. It suggested starting with the switches and VLANs, then configuring routing, DHCP, security rules, the firewall, and finally testing connectivity. It also explained that the exact commands depend on the Packet Tracer device models.

### My Evaluation

I accept Copilot's staged configuration plan. Before entering commands, I need to confirm the switch and firewall models and decide where the VLAN gateways will be located. I also need to make sure the wireless VLAN can reach all three buildings.

### Technical Reason

Configuring the network one stage at a time makes it easier to find and fix problems. Different Cisco devices support different commands, so checking the models first will help prevent configuration errors. Testing each stage will also help make sure the network works before moving forward.

Interaction 6 – Network Security and Final Verification

Objective: Configure network security rules and verify that devices can access approved resources while blocking unauthorized traffic.

AI Assistance: ChatGPT helped create and apply extended access control lists (ACLs) on CORE1 and CORE2. The ACLs were configured for department VLANs, the IT Sandbox, wireless clients, and network management.

Work Completed:

Configured ACLs for department VLANs 10–70.

Restricted the IT Sandbox (VLAN 80) from accessing other internal campus networks.

Configured wireless security rules for VLAN 100.

Restricted access to the network management VLAN 99.

Allowed approved DNS and public website traffic.

Tested DHCP, DNS, website access, and department isolation.

Saved switch configurations and the Packet Tracer project.

Testing Results: The tested devices received correct DHCP addresses, accessed the public website, and were blocked from reaching restricted department networks and internal servers where required.

Human Verification: I entered the commands in Cisco Packet Tracer, reviewed the results, corrected configuration issues, and performed connectivity tests to confirm the network was working as expected.

Outcome: The main campus network configuration and security testing were completed.
