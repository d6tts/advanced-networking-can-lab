# Network Verification and Testing

## 1. DHCP Testing

DHCP was tested on wired and wireless devices. The devices received IP addresses from the correct VLAN subnets.

| Device | VLAN | Assigned IP |
|---|---:|---|
| PC-A1 | 10 | 10.50.0.x |
| PC-B1 | 20 | 10.50.1.11 |
| PC-B2 | 30 | 10.50.2.11 |
| PC-B3 | 40 | 10.50.3.11 |
| PC-C1 | 50 | 10.50.4.11 |
| PC-C2 | 60 | 10.50.5.11 |
| PC-C3 | 70 | 10.50.6.11 |
| PC-A3 | 80 | 10.50.7.11 |
| LAPTOP-A | 100 | 10.50.16.11 |

**Result:** DHCP successfully assigned addresses, subnet masks, and default gateways.

## 2. DNS and Web Server Testing

- Internal DNS server at `10.50.8.10` was reachable from approved department devices.
- The hostname `www.college.local` successfully resolved to `10.50.20.2`.
- The public web server loaded using `http://www.college.local`.
- Website access was tested from wired and wireless devices, including the IT Sandbox.

**Result:** DNS resolution and HTTP access worked.

## 3. Routing and NAT Testing

- Department devices successfully reached their default gateways.
- Inter-VLAN routing was configured on CORE1 and CORE2.
- PC-A1 successfully pinged the simulated ISP router at `203.0.113.1`.
- NAT/PAT was configured on the ASA firewall.

**Result:** Internal routing and outbound connectivity to the simulated ISP were verified.

## 4. Network Security Testing

| Test | Expected Result | Actual Result |
|---|---|---|
| PC-A1 to DNS server | Allow | Passed |
| PC-A1 to Business PC | Block | Passed |
| PC-B1 to DNS server | Allow | Passed |
| PC-B1 to Computer Science PC | Block | Passed |
| PC-C3 to Computer Science PC | Block | Passed |
| PC-A3 to public website | Allow | Passed |
| PC-A3 to Business PC | Block | Passed |
| PC-A3 to internal DNS server using ping | Block | Passed |
| LAPTOP-A to public website | Allow | Passed |
| LAPTOP-A to Business PC | Block | Passed |
| PC-A1 to management gateway | Block | Passed |

**Result:** The tested ACL rules allowed approved traffic and blocked the tested unauthorized connections.

## 5. Wireless Testing

- Configured the common SSID `College-Campus`.
- Configured WPA2-PSK authentication.
- Connected LAPTOP-A to the wireless network.
- Verified that it received a DHCP address in VLAN 100.
- Confirmed access to the public website.
- Confirmed that access to the Business department was blocked.

**Result:** Wireless connectivity, DHCP, DNS, and security restrictions worked.

## 6. Final Notes

The campus network was configured with multiple VLANs, redundant core switches, DHCP, DNS, wireless access, an ASA firewall, NAT/PAT, and access control lists.

Testing confirmed that the main network functions worked and that the tested security restrictions behaved as expected.

The ISP connection in Packet Tracer represents a simulated external network, not a connection to the actual public Internet. Additional testing of external access to the DMZ web server would be needed to verify inbound public access.
