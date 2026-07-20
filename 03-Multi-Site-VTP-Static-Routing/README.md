# CCNA 3-Site Network with VTP & Static Routing

## Overview
![Network Topology](Topology.png)
This project simulates a three-site enterprise network built in Cisco Packet Tracer. The enterprise consists of **Tehran (Headquarters)**, **Tabriz**, and **Shiraz**, connected through a **hub-and-spoke WAN topology**, with Tehran serving as the central hub.
The lab demonstrates the implementation of enterprise Layer 2 and Layer 3 technologies, including VLAN segmentation, VTP, EtherChannel, Router-on-a-Stick, DHCP, SSH, and static routing between multiple sites.

---

## Technologies Used

### Layer 2
- VLAN Segmentation
- IEEE 802.1Q Trunking
- VTP Version 2 (Server / Client)
- EtherChannel (LACP)
- Rapid Spanning Tree Protocol (RSTP)
- PortFast
- BPDU Guard

### Layer 3
- Router-on-a-Stick
- DHCP (Router-Based)
- Static Routing
- Route Summarization

### Management & Security
- SSH Remote Management
- Management VLAN

---

## IP Addressing Plan

### Tabriz
| VLAN | Name | Network |
|------|------|---------------|
|10|IT|172.17.10.0/24|
|20|Management|172.17.20.0/24|
> VLANs are configured manually. VTP is intentionally not deployed in this branch.

### Tehran (Headquarters)
| VLAN | Name | Network |
|------|------|---------------|
|10|IT|172.16.10.0/24|
|20|HR|172.16.20.0/24|
|30|PR|172.16.30.0/24|
|40|Management|172.16.40.0/24|

### Shiraz
| VLAN | Name | Network |
|------|------|---------------|
|10|IT|192.168.10.0/24|
|20|HR|192.168.20.0/24|
|30|Management|192.168.30.0/24|

---

## Network Design

### WAN Architecture
- Hub-and-Spoke topology
- Tehran acts as the central hub.
- Dedicated point-to-point WAN links connect Tehran to Tabriz and Shiraz.

### VLAN Management (VTP)
- Tehran and Shiraz use the **farkiantech.local** VTP domain.
- VTP Version 2 is deployed.
- The distribution switch (**SW01**) in each site operates as the VTP Server.
- All remaining switches operate as VTP Clients.
- Tabriz uses manual VLAN configuration to demonstrate a hybrid enterprise environment.

### Inter-VLAN Routing
Router-on-a-Stick is implemented on all branch routers using IEEE 802.1Q subinterfaces.

### Layer 2 Redundancy
- EtherChannel (LACP) bundles redundant uplinks.
- SW01 is configured as the Root Bridge for each site's spanning tree by setting the priority to **4096**.

### DHCP Services
Each router provides DHCP services for all local user VLANs.

### Routing Strategy
Branch Routers:
- Default Route (`0.0.0.0/0`) pointing toward Tehran.
Tehran Router: Summary Static Routes:
- `172.17.0.0/16` → Tabriz
- `192.168.0.0/16` → Shiraz
This reduces the routing table size while maintaining connectivity.

### Device Management
- SSH is enabled on all routers and switches.
- Management traffic uses dedicated Management VLANs.
- PortFast and BPDU Guard are enabled on all access ports.

---

## WAN Addressing

| Link | Tehran | Remote Site |
|------|---------|-------------|
|Tehran ↔ Tabriz|10.10.10.1/30|10.10.10.2/30|
|Tehran ↔ Shiraz|10.10.10.5/30|10.10.10.6/30|

---

## Management IP Addresses

### Tabriz
| Device | IP Address |
|---------|------------|
|SW01|172.17.20.1|
|R1|172.17.20.254|

### Tehran
| Device | IP Address |
|---------|------------|
|SW01|172.16.40.1|
|SW02|172.16.40.2|
|SW03|172.16.40.3|
|SW04|172.16.40.4|
|SW05|172.16.40.5|
|R1|172.16.40.254|

### Shiraz
| Device | IP Address |
|---------|------------|
|SW01|192.168.30.1|
|SW02|192.168.30.2|
|SW03|192.168.30.3|
|R1|192.168.30.254|

---

## Verification

The following tests were successfully completed:
- DHCP address assignment
- Inter-VLAN communication
- Inter-site connectivity
- VTP synchronization
- EtherChannel operation
- STP Root Bridge election
- SSH remote access

---

## Files

- `03-Multi-Site-VTP-Static-Routing.pkt` → Cisco Packet Tracer project
- `Configs/Shiraz/` → Shiraz Network configurations
- `Configs/Tabriz/` → Tabriz Network configurations
- `Configs/Tehran/` → Tehran Network configurations

---

## Skills Demonstrated

- Enterprise Multi-Site Network Design
- VLAN Segmentation & IEEE 802.1Q Trunking
- Router-on-a-Stick (Inter-VLAN Routing)
- VTP Server/Client Configuration
- EtherChannel (LACP)
- Rapid Spanning Tree Protocol (RSTP)
- Static Routing & Route Summarization
- Hub-and-Spoke WAN Design
- DHCP Configuration
- SSH Secure Management
- Cisco IOS CLI Configuration


This lab was built to practice enterprise networking concepts commonly covered in the CCNA curriculum, including centralized VLAN management with VTP, Layer 2 redundancy, secure device management, inter-site routing, and scalable enterprise network design.
