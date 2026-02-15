# SMALL OFFICE / HOME OFFICE (SOHO) NETWORK DESIGN — Greenland Resources


**PROBLEM SUMMARY**

Greenland Resources is a fast-growing company in Western Nigeria with more than 1 million customers globally. The company deals with buying and selling food items and they are operating from the headquarters in western Nigeria. 
The company is intending to open a branch near a local village, somewhere in the north, and they require IT personnel to design a network for the branch. The network is intended to operate separately from the headquarters. 
Being a small network, the company has the following requirements during implementation.
1.	A router and one switch to be used.
2.	Three (3) departments which is Admin, Finance and Reception.
3.	Each department is required to be running on different VLANS.
4.	Each department is required to have a wireless network for the users.
5.	Host devices in the network are required to communicate with each other.
6.	Devices in all the department are required to communicate with each other.
Assume the Internet Service Providers (ISP) gave out a base network of 192.168.1.0, design and implement a network considering the above requirements.



**DEVICE AND EQUIPMENT**

Router: 2911 (Core-Router)

Switch: 2960 (Core-Switch)

Access Points: Access Point (Admin-AP, Finance-AP, Reception-AP)

Portable Computer (Admin-PC, Finance-PC, Reception-PC)

Printers (Admin-Printer, Finance-Printer, Reception-Printer)

Laptops, Tablet and Phones for each department



**TOPOLOGY**

<img width="937" height="431" alt="image" src="https://github.com/user-attachments/assets/393aa2a2-b1de-4631-94a7-a8692dabaed1" />



**IP ADDRESSING & VLAN PLAN**
- We'll split 192.168.1.0/24 into four /26 subnets (62 hosts each) — three used for departments and one reserved:

VLAN 10 — Admin
VLAN ID: 10
Subnet: 192.168.1.0/26
Gateway (Router subinterface): 192.168.1.1

VLAN 20 — Finance
VLAN ID: 20
Subnet: 192.168.1.64/26
Gateway: 192.168.1.65

VLAN 30 — Reception
VLAN ID: 30
Subnet: 192.168.1.128/26
Gateway: 192.168.1.129



**IMPLEMENTATION**

Action 1 — Design Topology
- Create the physical layout in Cisco Packet Tracer by placing one router, one switch, three wireless access points (one per department), and the required end devices (PCs and Printers).
- Connect the router to the switch, then connect departmental devices and access points to the switch. Label devices clearly and save the project file.

Action 2 — Configure VLANs
- Create three VLANs on the switch: one for Admin, one for Finance, and one for Reception. Assign the appropriate switch ports to each VLAN based on the department the connected devices belong to.

Action 3 — Configure Wireless Networks
- Configure each access point with a unique SSID corresponding to its department (e.g., Admin_WIFI, Finance_WIFI, Reception_WIFI).
- Enable wireless security (such as WPA2) and set a password.
- Ensure each access point is connected to a switch port assigned to the correct VLAN so wireless users join the proper network segment.

Action 4 — Configure Access and Trunk on Switch
- Configure the switch port connected to the router as a trunk port to allow multiple VLANs to pass through it.
- Ensure all other ports connected to departmental devices and access points are configured as access ports assigned to their respective VLANs.

Action 5 — Configure Inter-VLAN Routing
- On the router, enable routing between VLANs using subinterfaces (router-on-a-stick method).
- Assign each VLAN a default gateway IP address so devices in different VLANs can communicate with each other.

Action 6 — Configure DHCP Server
- Configure the router to act as a DHCP server.
- Create a separate DHCP pool for each VLAN and define the appropriate subnet, default gateway, and DNS server so devices can automatically receive IP addresses.

Action 7 — Change All Devices to DHCP
- Configure all wired and wireless devices to obtain IP addresses automatically via DHCP.
- Ensure wireless clients connect to the correct SSID before requesting an IP address.

Action 8 — Test for Connectivity
- Verify connectivity by testing communication within the same VLAN and across different VLANs.
- Confirm that devices receive correct IP addresses and can reach their respective gateways and other departments.



**VERIFICATION COMMANDS AND EXPECTED OUTCOMES**

Switch (Main-Switch)
- show vlan brief (confirms VLANs and ports).
- show interfaces trunk (shows trunk status and allowed VLANs).

Router (Core-Router)
- show ip interface brief (see subinterfaces and IPs).
- show ip route (verify connected networks (you should see 192.168.1.0/26, 192.168.1.64/26, 192.168.1.128/26)).
- show running-config (full configuration).

Expected to
- ping across VLANs returns replies.
- DHCP clients receive addresses in the correct subnet (e.g., Admin client 192.168.1.11)



**TROUBLESHOOTING TIPS**

- If hosts don't get DHCP addresses: verify ip dhcp pool and ip dhcp excluded-address ranges, ensure no IP overlap.
- If inter-VLAN traffic fails: check trunk is up (show interfaces trunk) and router subinterfaces exist with correct encapsulation dot1Q IDs.
- If wireless clients can't reach network: Confirm AP is physically connected to the correct switch access port and that that port is in the correct VLAN.
- Use show arp on router to verify MAC-to-IP mappings.






