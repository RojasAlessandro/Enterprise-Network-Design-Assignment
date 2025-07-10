# INF1006: Enterprise Network Design Project  
**AY 2024/2025 – Assignment 1**  
**Singapore Institute of Technology (SIT)**  

## Group 6 Members
- Ang Ke Ying   
- Rojas Alessandro Rafael Doronila 
- Tay Yu Xuan Jolene  
- Choh Kaifeng  
- Raffael Davin Harjanto

**Submission Date:** 25 June 2025

---

## Project Overview

This project involves the **design and simulation of an enterprise computer network** for an institution, spanning two separate buildings (E2 and E6). We used the allocated IP address space `103.30.215.0/24` and implemented **Variable Length Subnet Masking (VLSM)**, VLAN segmentation, and other essential network technologies to ensure optimal **security, scalability, and redundancy**.

---

## VLSM Subnet Design

| **Zone**         | **VLAN ID** | **Devices**                           | **Subnet Mask** | **Network Address**     | **Usable IP Range** | **Notes**                          |
|------------------|------------|----------------------------------------|------------------|--------------------------|----------------------|------------------------------------|
| Network Lab      | VLAN 10    | 2 PCs, 2 laptops, switch, AP           | /26              | 103.30.215.0/26          | .1 – .62             | Room for 41+ devices and growth    |
| Security Lab     | VLAN 20    | 3 PCs, 2 laptops, switch, AP           | /26              | 103.30.215.64/26         | .65 – .126           | Same as Network Lab                |
| Admin Office     | VLAN 30    | 2 PCs, 1 printer, switch               | /29              | 103.30.215.192/29        | .193 – .198          | Compact office setup               |
| Lab 1            | VLAN 40    | 3 PCs, 2 laptops, switch, AP           | /27              | 103.30.215.128/27        | .129 – .158          | 25+ devices supported              |
| Lab 2            | VLAN 50    | 3 PCs, 2 laptops, switch, AP           | /27              | 103.30.215.160/27        | .161 – .190          | Future expansion ready             |
| E6 Servers       | —          | DNS, Web, ISP servers                  | /29              | 103.30.215.200/29        | .201 – .206          | Core services                      |
| WLAN Link        | —          | Router-to-router connection (E2 ↔ E6)  | /30              | 103.30.215.208/30        | .209 – .210          | Point-to-point IP routing          |

---

## Network Topology

- **Buildings:** E2 and E6  
- **Zones:** Labs, Admin Office, Server Room  
- **Routing:** Router-on-a-Stick setup  
- **Switching:** VLAN trunking via central Admin Office switch  
- **Connectivity:** Wired and wireless devices using access points  

---

## Routing Configuration

- **Router-on-a-Stick:** Sub-interfaces created for each VLAN  
- **Static Routing:** Simpler control and visibility  
- **Gateway Assignment:** Based on subnet allocations  

---

## 🔧 Features Implemented

### 1. Dynamic Host Configuration Protocol (DHCP)
- Auto-assigns IPs to clients  
- Separate DHCP pools for each VLAN:  
  - **E2 Router:** VLAN10_POOL, VLAN20_POOL, VLAN30_POOL  
  - **E6 Router:** VLAN40_POOL, VLAN50_POOL  

### 2. Access Control Lists (ACLs)
- Restrict access to the **admin printer**  
- **ACL 100** (E2 Router) and **ACL 110** (E6 Router)  
- Students and lecturers blocked; admins allowed  

### 3. 🔗 EtherChannel Link Aggregation
- Combines multiple switch links  
- Benefits:
  - Higher bandwidth  
  - Fault tolerance  
  - Load balancing  

### 4. Wireless Access Points
- WPA2-PSK security enabled  
- Static IP for wireless infrastructure  
- Student and lecturer personal device support  

### 5. VLAN Segmentation
- Isolates departments and controls broadcast domains  
- Improves security, performance, and manageability  

### 6. Redundancy Implementation
- **Device Redundancy** (backup devices)  
- **Link Redundancy** (multiple uplinks)  
- **Path Redundancy** (alternate routes)  
- **Service Redundancy** (failover servers)

---

## Conclusion

This enterprise network design delivers a **secure, scalable, and high-performing infrastructure** tailored to institutional needs. It leverages advanced features like VLANs, VLSM, DHCP, ACLs, and redundancy techniques to ensure **reliability, future expansion**, and **ease of management** in a simulated Cisco Packet Tracer environment.

