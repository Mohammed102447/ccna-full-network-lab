# CCNA Enterprise Mega Lab

This repository contains a complete enterprise-level CCNA Mega Lab designed to simulate a professional multi-office network.  
The topology covers Core, Distribution, and Access switching layers, dynamic routing, redundancy, network services, security, IPv6, and wireless infrastructure.

This lab is intended for CCNA students, junior network engineers, and anyone aiming to build real-world enterprise networking skills.

---

## 🖼️ Topology Overview

A dual-office enterprise network including:

- 2 Offices: Office A & Office B  
- Core Layer: 2 Core Switches (CSW1, CSW2)  
- Distribution Layer: 4 Distribution Switches (A1, A2, B1, B2)  
- Access Layer: 6 Access Switches  
- Edge Router (R1): connected to the Internet  
- Server (SRV1): DHCP, DNS, FTP, Syslog, NTP  
- Wireless Controller (WLC1)  
- 2 Lightweight Access Points  
- Full VLAN segmentation for PCs, VoIP, Wi-Fi, Management, and Servers  

Topology file:
<img width="1446" height="861" alt="A2" src="https://github.com/user-attachments/assets/366f28f0-9ee3-4207-a5b4-cceea05944f0" />



 🛠️ Part 1 — Basic Device Setup

- Device hostnames  
- Secured enable secret (Type 5 or Type 9)  
- Local user accounts for admins  
- Console + VTY password protection  
- SSHv2 configuration  
- Disable unused services (CDP, HTTP where needed)  
- Banner for legal notice  


 🧩 Part 2 — VLANs & Layer-2 EtherChannel

- VLANs for:
  - PC users  
  - IP Phones  
  - Wi-Fi  
  - Management  
  - Servers  
- Trunks configured with a dedicated native VLAN  
- DTP disabled on all trunk links  
- L2 EtherChannel:
  - Distribution layer aggregation  
  - Core redundant pathways  


 🌐 Part 3 — IP Addressing, Layer-3 EtherChannel & HSRP

- IPv4 addressing across SVI interfaces  
- Layer-3 EtherChannel on the Core layer  
- HSRPv2 for every major VLAN:
  - User PCs  
  - Phones  
  - Management  
  - Wi-Fi  
  - Servers  
- Active/standby distribution aligned with STP root roles  


 🔁 Part 4 — Spanning Tree Configuration

- Rapid PVST+ enabled on all switches  
- Core/Distribution role-based root bridging  
- Root primary/secondary hierarchy  
- PortFast on all access ports  
- BPDU Guard enabled  
- Loop guard on uplinks  


🏃 Part 5 — Routing (OSPF & Static)

- OSPFv2 enabled across R1, core, and distribution devices  
- Loopback interfaces used as Router-IDs  
- Passive interfaces for all SVIs  
- Default routes on R1:
  - Primary ISP  
  - Backup ISP (floating static)  
- Inter-office routing optimized via OSPF area 0  


 💼 Part 6 — Network Services (DHCP, DNS, NTP, FTP…)

R1 Services:
- DHCP server with multiple IP pools  
- NAT:
  - Static NAT for SRV1  
  - PAT overload using pool  
- DNS forwarding  
- Syslog client synced with SRV1  
- NTP authentication configured  

 Server (SRV1):
- DNS zone  
- NTP master  
- Syslog receiver  
- FTP server for IOS upgrades and file transfer  


 🔒 Part 7 — Network Security

- Extended ACL between Office A → Office B  
- Management ACL permitting SSH only from Admin VLAN  
- DHCP Snooping  
- Dynamic ARP Inspection  
- IP Source Guard  
- Port Security on all Access ports  
- LLDP enabled (CDP disabled)  
- Login blocking and password complexity  


 🧬 Part 8 — IPv6 Implementation

- Dual-stack deployment  
- IPv6 addressing on R1, CSW1, CSW2  
- IPv6 default route (primary + floating)  
- EUI-64 on access VLANs  
- IPv6 OSPF (OSPFv3) optional  


 📶 Part 9 — Wireless

- WLC1 full setup:
  - Management interface  
  - Dynamic interface mapped to VLAN 40  
  - SSID (WPA2-PSK)  
  - Mobility settings  
- LAPs automatically join via CAPWAP  
- Wireless clients receive DHCP from R1  
