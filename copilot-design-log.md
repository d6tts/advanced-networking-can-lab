# GitHub Copilot Design Log

## Interaction 1 – Network Design

Prompt:

Copilot Recommendation:

My Evaluation:

Technical Reason:

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
