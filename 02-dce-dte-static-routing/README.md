# Lab 02 — DCE/DTE Serial Connection and Static Routing

## Overview

This Cisco Packet Tracer lab connects two separate LANs through a point-to-point serial WAN link between two routers. Static routes allow hosts on either LAN to communicate across the WAN.

## Objectives

- Configure router LAN and serial interfaces.
- Identify the DCE and DTE ends of a serial connection.
- Configure the clock rate on the DCE interface.
- Implement bidirectional IPv4 static routing.
- Verify routing using `show ip route`, `ping`, and `tracert`.

## Topology

```text
PC1 --- SW1 --- R1 ===== Serial WAN ===== R2 --- SW2 --- PC2
                DCE                    DTE
```

- LAN 1: `192.168.1.0/24`
- Serial WAN: `192.168.2.0/24`
- LAN 2: `192.168.3.0/24`

> The `/24` WAN subnet reflects the configuration used in this lab. A `/30` is more address-efficient for a traditional point-to-point IPv4 link.

## IP Addressing

| Device | Interface | IPv4 address | Subnet mask | Default gateway |
|---|---|---|---|---|
| R1 | FastEthernet0/0 | 192.168.1.1 | 255.255.255.0 | — |
| R1 | Serial0/1/0 (DCE) | 192.168.2.1 | 255.255.255.0 | — |
| R2 | Serial0/1/0 (DTE) | 192.168.2.2 | 255.255.255.0 | — |
| R2 | FastEthernet0/0 | 192.168.3.1 | 255.255.255.0 | — |
| PC1 | FastEthernet | 192.168.1.10 | 255.255.255.0 | 192.168.1.1 |
| PC2 | FastEthernet | 192.168.3.10 | 255.255.255.0 | 192.168.3.1 |

## Configuration

### R1

```cisco
configure terminal
interface FastEthernet0/0
 ip address 192.168.1.1 255.255.255.0
 no shutdown
exit
interface Serial0/1/0
 ip address 192.168.2.1 255.255.255.0
 clock rate 2000000
 no shutdown
exit
ip route 192.168.3.0 255.255.255.0 192.168.2.2
end
copy running-config startup-config
```

### R2

```cisco
configure terminal
interface FastEthernet0/0
 ip address 192.168.3.1 255.255.255.0
 no shutdown
exit
interface Serial0/1/0
 ip address 192.168.2.2 255.255.255.0
 no shutdown
exit
ip route 192.168.1.0 255.255.255.0 192.168.2.1
end
copy running-config startup-config
```

The serial link uses the Cisco default HDLC encapsulation; no explicit encapsulation change was needed.

## Verification

### Interface and routing checks

Run these commands on each router:

```cisco
show ip interface brief
show ip route
```

The serial interfaces were verified as `up/up`. The routing tables showed these static routes:

- R1: `S 192.168.3.0/24 [1/0] via 192.168.2.2`
- R2: `S 192.168.1.0/24 [1/0] via 192.168.2.1`

### Connectivity tests

- R2 to R1 serial interface (`192.168.2.1`): **5/5 replies (100%)**.
- R1 to R2 LAN gateway (`192.168.3.1`): **5/5 replies (100%)**.
- PC1 to PC2 (`192.168.3.10`): **3/4 replies (75%) on the captured initial test**; subsequent replies confirmed connectivity.
- Traceroute from PC1 to PC2 completed across the expected path:

```text
192.168.1.1  (R1)
192.168.2.2  (R2)
192.168.3.10 (PC2)
```

From PC1's Command Prompt:

```text
ping 192.168.3.10
tracert 192.168.3.10
```

## Troubleshooting Notes

**Initial ping failure to `192.168.3.1`:** R1 initially had only connected routes, with no route to `192.168.3.0/24`. Adding a static route via `192.168.2.2`, and ensuring R2's LAN interface was configured and active, resolved reachability.

**First PC-to-PC ping lost one packet:** The captured initial test returned 3 out of 4 replies. ARP resolution is one possible cause in Packet Tracer, but the exact cause was not independently confirmed. Traceroute subsequently reached PC2.

## Files

```text
02-dce-dte-static-routing/
├── README.md
├── 02-dce-dte-static-routing.pkt
├── topology.png
├── configs/
│   ├── R1.txt
│   └── R2.txt
└── screenshots/
    ├── interface-status.png
    ├── routing-table.png
    └── ping-traceroute.png
```

> File names above describe the recommended repository structure. Add the corresponding Packet Tracer file and screenshots before publishing.

## Key Takeaways

- The DCE end provides clocking for the serial link.
- Each router requires a route to the remote LAN, including the return path.
- `show ip interface brief` validates interface state; `show ip route` validates route installation.
- Successful router-to-router pings do not replace end-to-end host testing.

## Tools

Cisco Packet Tracer · Cisco IOS CLI · IPv4 · Static Routing · Serial DCE/DTE
