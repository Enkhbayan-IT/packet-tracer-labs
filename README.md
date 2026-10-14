# Cisco Packet Tracer | Network Infrastructure Labs

**Hands-on Networking • Cisco IOS • Routing & Switching • Enterprise Services • Troubleshooting**

This repository documents my practical networking projects developed using Cisco Packet Tracer as part of my IT Infrastructure and Cloud Administration learning journey.

The labs progress from basic router configuration to VLAN segmentation, inter-VLAN routing, access control, and enterprise network services.

Each main project focuses on network configuration, verification, and technical documentation.

## Featured Projects

| Lab | Project | Technologies and Skills |
|---|---|---|
| 01 | [Basic Router Configuration](01-basic-router-config/) | Cisco IOS CLI, interface configuration, device management |
| 02 | [DCE/DTE & Static Routing](02-dce-dte-static-routing/) | Serial WAN, DCE/DTE, static routes, ICMP, traceroute |
| 03 | [VLAN, Router-on-a-Stick & ACL](03-vlan-router-on-stick-acl/) | VLAN 10/20, 802.1Q trunking, inter-VLAN routing, extended ACL |
| 04 | [Enterprise Network Services](Lab%2004%20%E2%80%93%20Enterprise%20Network%20Services/) | DHCP Relay, DNS, HTTP, FTP, Email, wireless networking |

## Technical Skills Demonstrated

**Routing & Switching**
- Cisco IOS command-line configuration
- IPv4 addressing and subnetting
- Static routing
- VLAN segmentation
- 802.1Q trunking
- Router-on-a-Stick
- Inter-VLAN routing
- Serial WAN connectivity and DCE/DTE

**Network Security**
- Extended Access Control Lists (ACLs)
- Traffic filtering between VLANs
- ICMP access restrictions
- Verification of inbound ACL policies

**Enterprise Network Services**
- DHCP server configuration
- DHCP relay using `ip helper-address`
- DNS configuration and name resolution
- HTTP web services
- FTP file transfer services
- Email services
- Wired and wireless client connectivity

**Verification & Troubleshooting**
- `ping` and `tracert`
- `ipconfig` and `nslookup`
- `show ip interface brief`
- `show ip route`
- `show running-config`
- `show vlan brief`
- `show interfaces trunk`
- `show access-lists`

## Project Highlights

### Lab 01 – Basic Router Configuration

Introduction to Cisco IOS, router configuration modes, device settings, and network interface configuration.

[View Lab 01](01-basic-router-config/)

### Lab 02 – DCE/DTE & Static Routing

Two Cisco routers connected through a serial WAN link, with separate LAN networks.

**Key implementation:**
- Configured serial interfaces and DCE/DTE connectivity.
- Configured static routes between LAN subnets.
- Verified end-to-end communication using ping and traceroute.

[View Lab 02](02-dce-dte-static-routing/)

### Lab 03 – VLAN Segmentation, Router-on-a-Stick & Extended ACL

A small enterprise network divided into HR and IT departments.

**Network design:**
- VLAN 10 – HR: `192.168.10.0/24`
- VLAN 20 – IT: `192.168.20.0/24`

**Key implementation:**
- Configured switch access ports and VLAN membership.
- Configured an 802.1Q trunk.
- Implemented Router-on-a-Stick for inter-VLAN routing.
- Applied an extended ACL to restrict ICMP traffic from HR to IT.
- Verified routing and ACL behavior using Cisco IOS commands and connectivity tests.

[View Lab 03](03-vlan-router-on-stick-acl/)

### Lab 04 – Enterprise Network Services

A small enterprise network using separate server and client subnets.

**Network design:**
- Server LAN: `192.168.1.0/28`
- Client LAN: `192.168.1.16/28`
- DHCP Server: `192.168.1.6`
- DNS Server: `192.168.1.5`
- Router Client Gateway: `192.168.1.17`

**Key implementation:**
- Configured two routed IPv4 networks.
- Implemented DHCP relay between subnets.
- Verified automatic DHCP address assignment.
- Configured server infrastructure for DNS, HTTP, FTP, and Email.
- Included wireless connectivity and service verification documentation.

[View Lab 04](Lab%2004%20%E2%80%93%20Enterprise%20Network%20Services/)

## Additional Packet Tracer Exercises

The repository also includes introductory exercises covering:

1. Learning the Packet Tracer environment
2. Network topology prototyping
3. Packet flow observation
4. Web server connectivity
5. DHCP configuration
6. IP configuration commands
7. Wireless troubleshooting

These exercises provide foundational knowledge supporting the main infrastructure projects.

## Repository Organization

```text
packet-tracer-labs/
│
├── 01-basic-router-config/
├── 02-dce-dte-static-routing/
├── 03-vlan-router-on-stick-acl/
├── Lab 04 – Enterprise Network Services/
│
├── docs/
├── labs/
└── README.md
```

Individual lab directories contain available Packet Tracer project files, configuration exports, screenshots, and technical documentation.

## Learning Roadmap

Planned projects:

- [ ] Lab 05 – Network Troubleshooting: Five Fault Scenarios
- [ ] Lab 06 – OSPF, NAT/PAT and ACL
- [ ] Lab 07 – STP, EtherChannel and Network Redundancy
- [ ] Azure Networking – VNet, Subnets, NSG and Route Tables

These projects are planned and have not yet been marked as completed.

## Career Focus

I am developing practical skills for roles including:

- Junior IT Infrastructure Technician
- Network Technician
- IT Operations Technician
- Windows Server Administrator
- Azure / Cloud Operations Engineer

My learning combines Cisco networking fundamentals with Windows Server administration, PowerShell automation, and Microsoft Azure.

## Tools & Technologies

Cisco Packet Tracer | Cisco IOS | IPv4 | VLAN | Static Routing | ACL | DHCP | DNS | TCP/IP | ICMP | GitHub

---

**Author:** Enkhbayan-IT

[GitHub Profile](https://github.com/Enkhbayan-IT) | [Windows Server & System Administration Labs](https://github.com/Enkhbayan-IT/sysadmin-lab)

*All projects are educational simulations developed in Cisco Packet Tracer, not production deployments.*
