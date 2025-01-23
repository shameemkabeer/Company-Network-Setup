# Network Setup for Software Development Company

## Overview

This project demonstrates a comprehensive network setup for a software development company. The network is built using multiple topologies (Bus, Mesh, Star, and Ring) with the use of VLANs for efficient communication. The configuration includes DNS services, web server setup, and Cisco router configuration.

## Step 1: Define Network Structure

The network consists of the following topologies:

- **Bus Topology**: 4 PCs connected to a single backbone via 4 switches.
- **Mesh Topology**: 4 PCs with 4 switches, all interconnected.
- **Star Topology**: 6 PCs connected to a central switch.
- **Ring Topology**: 4 PCs connected to 4 switches in a circular layout.

## Step 2: Hardware Requirements

- **Router**: Cisco 2811 with HWIC-4ESW module installed.
- **Switches**: 13 total (4 for bus, 4 for mesh, 1 for star, 4 for ring).
- **PCs**: 18 total (4 for bus, 4 for mesh, 6 for star, 4 for ring).
- **Server**: 1 server for DNS and web services.

## Step 3: IP Addressing Scheme

**Device**: Server  
- **IP Address**: 192.168.1.100  
- **Subnet Mask**: 255.255.255.0  
- **Default Gateway**: 192.168.1.1  

**Device**: Bus Topology PCs  
- **IP Address**: 192.168.2.2-192.168.2.5  
- **Subnet Mask**: 255.255.255.0  
- **Default Gateway**: 192.168.2.1  

**Device**: Mesh Topology PCs  
- **IP Address**: 192.168.3.2-192.168.3.5  
- **Subnet Mask**: 255.255.255.0  
- **Default Gateway**: 192.168.3.1  

**Device**: Star Topology PCs  
- **IP Address**: 192.168.4.2-192.168.4.7  
- **Subnet Mask**: 255.255.255.0  
- **Default Gateway**: 192.168.4.1  

**Device**: Ring Topology PCs  
- **IP Address**: 192.168.5.2-192.168.5.5  
- **Subnet Mask**: 255.255.255.0  
- **Default Gateway**: 192.168.5.1  

## Step 4: Server Configuration

### DNS Configuration

1. Enable DNS Service on the server.
2. Add entries for domains:
   - [www.nexgen.com](http://www.nexgen.com) → 192.168.1.100
   - [www.nexgen.com/operations.html](http://www.nexgen.com/operations.html) → 192.168.1.100
   - [www.nexgen.com/dev.html](http://www.nexgen.com/dev.html) → 192.168.1.100
   - [www.nexgen.com/sales.html](http://www.nexgen.com/sales.html) → 192.168.1.100
   - [www.nexgen.com/qateam.html](http://www.nexgen.com/qateam.html) → 192.168.1.100

### Web Server Configuration

1. Enable HTTP/HTTPS Services on the server.
2. Create pages for:
   - [www.nexgen.com](http://www.nexgen.com) → General information.
   - [www.nexgen.com/operations.html](http://www.nexgen.com/operations.html) → Operations department.
   - [www.nexgen.com/dev.html](http://www.nexgen.com/dev.html) → Development department.
   - [www.nexgen.com/sales.html](http://www.nexgen.com/sales.html) → Sales department.
   - [www.nexgen.com/qateam.html](http://www.nexgen.com/qateam.html) → Quality Assurance Team department.

## Step 5: Router Configuration (Cisco 2811)

### Physical Setup:

- **Interface**: FastEthernet0/0  
  - **Role**: Server Gateway  
  - **IP Address**: 192.168.1.1  
  - **Subnet Mask**: 255.255.255.0  

- **Interface**: FastEthernet0/1  
  - **Role**: Bus Topology GW  
  - **IP Address**: 192.168.2.1  
  - **Subnet Mask**: 255.255.255.0  

- **Interface**: FastEthernet0/3/0  
  - **Role**: Mesh Topology GW  
  - **IP Address**: 192.168.3.1  
  - **Subnet Mask**: 255.255.255.0  

- **Interface**: FastEthernet0/3/1  
  - **Role**: Star Topology GW  
  - **IP Address**: 192.168.4.1  
  - **Subnet Mask**: 255.255.255.0  

- **Interface**: FastEthernet0/3/2  
  - **Role**: Ring Topology GW  
  - **IP Address**: 192.168.5.1  
  - **Subnet Mask**: 255.255.255.0  

### CLI Commands for VLAN Setup

### 1. Create VLANs and Assign IPs:

```bash
vlan database
 vlan 2 name VLAN_2
 vlan 3 name VLAN_3
 vlan 4 name VLAN_4
exit

interface vlan 2
 ip address 192.168.3.1 255.255.255.0
 no shutdown

interface vlan 3
 ip address 192.168.4.1 255.255.255.0
 no shutdown

interface vlan 4
 ip address 192.168.5.1 255.255.255.0
 no shutdown
```
### 2.Assign VLANs to HWIC Ports:
```
interface FastEthernet0/3/0
 switchport mode access
 switchport access vlan 2
 no shutdown

interface FastEthernet0/3/1
 switchport mode access
 switchport access vlan 3
 no shutdown

interface FastEthernet0/3/2
 switchport mode access
 switchport access vlan 4
 no shutdown
```
## Step 6: Test the Network
Ping Tests:

From each PC, ping its default gateway.
Example: ping 192.168.1.1 (Server Gateway).
DNS Resolution:

Test by pinging domain names from PCs.
Example: ping www.nexgen.com.
Website Access:

Open web browsers on PCs and access department-specific sites.

## Step 7: Save and Document
Save the Packet Tracer file.
Export configurations for reference.

## Step 8: Cost Efficiency Recommendations
Use fewer routers by leveraging VLANs and a single router for inter-department connectivity.
Optimize topologies to minimize cabling and hardware costs.

## 🖼️ Screenshot

![NexGen](https://github.com/user-attachments/assets/8abce5de-9caf-40a9-84a1-39f6b926f402)


### 📚 Check out my article about the project: [Linkedin](https://www.linkedin.com/pulse/network-design-nexgen-software-company-mohamed-shameem-pa-moi5c/?trackingId=j%2BuJ6ei8R%2BaVTyt540QY%2Fw%3D%3D)

## 🤝 Contributing
Feel free to contribute by creating pull requests or submitting issues. All contributions are welcome!

## 🧑‍💻 **Author**  
**SHAMEEM KABEER**  
A passionate cybersecurity enthusiast who enjoys developing simple, effective tools to identify vulnerabilities.



