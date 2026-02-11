# SMALL OFFICE / HOME OFFICE (SOHO) NETWORK DESIGN — Greenland Resources
Project Goal: Design and implement a small branch network (separate from HQ) using one router and one switch in Cisco Packet Tracer. The network will support three departments (Admin, Finance, Reception), each on its own VLAN and each with its own wireless network. All hosts and departments must be able to communicate (inter-VLAN routing).

**Table of Contents**
1. Problem Summary
2. Equipment & Files
3. Topology (what to draw in Packet Tracer)
4. IP addressing & VLAN plan
5. Step-by-step implementation -Design Topology -Configure VLANs -Configure Wireless Networks -Configure Wireless Networks -Configure Access & Trunk on Switch -Configure Inter-VLAN routing (router-on-a-stick) -Configure DHCP on router -Change all device interfaces to DHCP -Test for connectivity.
6. Verification commands & expected outputs
7. Troubleshooting tips


**Problem Summary**

Greenland Resources needs a small independent branch network that contains 3 departments (Admin, Finance, Reception). Each department must be on its own VLAN and must also provide wireless connectivity to its users. The ISP provides a single /24 network: 192.168.1.0/24.

Goals:
Single router + single switch architecture
3 VLANs with inter-VLAN routing
Wireless for each department (each department has its own SSID)
DHCP allocation per VLAN
All hosts must be able to communicate

