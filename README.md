# BGP-Routing-protocol-between-OSPF-and-RIP
Inter-AS routing lab in Cisco Packet Tracer: OSPF (AS 100) and RIPv2 (AS 200) connected using BGP.
# Inter-AS Routing Lab: OSPF, RIPv2 and BGP using Cisco Packet Tracer

## Overview
This project connects two separate networks that run different routing protocols, using **BGP** as the link between them. It shows how routes are exchanged between different Autonomous Systems (AS) and how end devices in one network can reach devices in the other.

## Topology
![Network Topology](screenshots/topology.png)

## Network Design

| Area | Colour | AS Number | Routing Protocol |
|------|--------|-----------|------------------|
| Network 1 | Pink | AS 100 | OSPF (single area, Area 0) |
| Network 2 | Yellow | AS 200 | RIP version 2 |
| Inter-AS link | Green | AS 100 ↔ AS 200 | BGP (eBGP) |

- **AS 100 (OSPF):** Three routers connected by point-to-point links, each with its own LAN.
- **AS 200 (RIPv2):** Three routers connected by point-to-point links, each with its own LAN.
- **BGP link:** The edge router of each AS peers over the `100.0.0.0/24` network. Routes from both AS are exchanged and redistributed so the two networks can communicate.

## IP Addressing

**AS 100 (Pink)**

| Network | Purpose |
|---------|---------|
| 10.0.0.0/24, 20.0.0.0/24, 30.0.0.0/24 | Router-to-router links |
| 192.168.10.0/24 | LAN 1 |
| 192.168.20.0/24 | LAN 2 |
| 192.168.30.0/24 | LAN 3 |

**AS 200 (Yellow)**

| Network | Purpose |
|---------|---------|
| 40.0.0.0/24, 50.0.0.0/24, 60.0.0.0/24 | Router-to-router links |
| 192.168.40.0/24 | LAN 4 |
| 192.168.50.0/24 | LAN 5 |
| 192.168.60.0/24 | LAN 6 |

**Inter-AS link:** 100.0.0.0/24

## Technologies Used
- OSPF (single area)
- RIP version 2
- eBGP between autonomous systems
- Route redistribution between protocols
- Static IP addressing and subnetting
- Cisco 2811 routers and 2960 switches

## Objectives
- Configure OSPF in AS 100 and RIPv2 in AS 200
- Establish an eBGP neighbour relationship between the two AS
- Redistribute BGP routes into OSPF and RIP, and the reverse
- Verify end-to-end connectivity between PCs in both networks

## Verification
- `show ip route` to check learned OSPF, RIP and BGP routes
- `show ip bgp summary` to confirm the BGP neighbour is established
- `show ip ospf neighbor` to confirm OSPF adjacencies
- Ping from a PC in AS 100 (e.g. 192.168.10.1) to a PC in AS 200 (e.g. 192.168.60.1)


## How to Open
1. Download `Batch-116-BGP.pkt` (or the zipped version)
2. Open it in **Cisco Packet Tracer**

## Result
PCs in the OSPF network can successfully ping PCs in the RIPv2 network and the reverse, which confirms that BGP and route redistribution are working.
