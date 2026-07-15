# CCNA Multi-Site Enterprise Lab

This project demonstrates a multi-site enterprise network implemented in Cisco Packet Tracer. Two branch offices (Shiraz and Tehran) are connected through a WAN link while providing VLAN segmentation, inter-VLAN routing, and secure remote management.

---

## Technologies Used
- VLAN
- Router-on-a-Stick
- IEEE 802.1Q Trunking
- EtherChannel (LACP)
- Rapid Spanning Tree Protocol (RSTP)
- SSH Remote Management
- DHCP
- Static Routing
- PortFast
- BPDU Guard

---

## Branch Network Design

### Shiraz
| VLAN | Name | Network |
|------|------|---------------|
| 10 | IT | 192.168.10.0/24 |
| 20 | HR | 192.168.20.0/24 |
| 30 | Management | 192.168.30.0/24 |

### Tehran
| VLAN | Name | Network |
|------|------|---------------|
| 10 | IT | 172.16.10.0/24 |
| 20 | HR | 172.16.20.0/24 |
| 30 | Management | 172.16.30.0/24 |

---

## Network Design

- Two enterprise branches connected through a point-to-point WAN link.
- Router-on-a-Stick is used for inter-VLAN routing at both sites.
- SW01 acts as the distribution switch and STP Root Bridge.
- SW02 and SW03 act as access switches.
- EtherChannel is configured using LACP.
- DHCP services are provided by each site's router.
- Static routing enables communication between both sites.
- SSH is enabled on all routers and switches.
- PortFast and BPDU Guard are enabled on access ports.

---

## WAN Addressing

| Device | IP Address |
|---------|------------|
| R1-Shiraz | 10.10.10.1/30 |
| R1-Tehran | 10.10.10.2/30 |

---

## Management IPs

### Shiraz

| Device | Management IP |
|---------|---------------|
| SW01 | 192.168.30.1 |
| SW02 | 192.168.30.2 |
| SW03 | 192.168.30.3 |
| R1 | 192.168.30.254 |

### Tehran

| Device | Management IP |
|---------|---------------|
| SW01 | 172.16.30.1 |
| SW02 | 172.16.30.2 |
| SW03 | 172.16.30.3 |
| R1 | 172.16.30.254 |

---

## Files

- `Multi-Site-VLAN-Routing-Lab.pkt` → Cisco Packet Tracer project
- `Configs/Routers/` → Router configurations
- `Configs/Switches/` → Switch configurations

---

## Skills Demonstrated

- VLAN Segmentation
- Inter-VLAN Routing
- Router-on-a-Stick
- Layer 2 Redundancy
- EtherChannel (LACP)
- STP Root Bridge Configuration
- SSH Configuration
- DHCP Configuration
- Static Routing
- Multi-Site Enterprise Network Design
- Cisco IOS CLI