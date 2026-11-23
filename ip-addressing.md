# IPv4 Addressing and VLAN Plan

Starting Network: 10.50.0.0/16

## VLAN and Subnet Table

## Additional VLAN Assignments

| VLAN ID | Network Purpose | Network Address | Prefix |
|---|---|---|---|
| 90 | Internal Servers | 10.50.8.0/26 | /26 |
| 99 | Network Management | 10.50.9.0/26 | /26 |
| 100 | Wireless Clients | 10.50.16.0/22 | /22 |
| 110 | DMZ Servers | 10.50.20.0/28 | /28 |

These VLAN IDs are proposed additions to the original eight department VLANs.

## Routing Notes

The /30 subnets are reserved for point-to-point routed connections between the core switches, distribution switches, and firewall if the selected equipment supports those connections.

If Layer 2 trunks are used instead, separate /30 networks will not be needed for those connections.

The campus will need a gateway redundancy method if both core switches are responsible for routing department VLANs. The final method will depend on the Cisco Packet Tracer devices selected.
## Subnet Calculations

To be completed.
