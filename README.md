# Multi-Site-Enterprise-Network
Simulated multi site enterprise network in GNS3

## IP Addressing
|Location |VLAN|Subnet|
|:---|:---|:---|
|HQ|10|192.168.10.0/24|
|HQ|20|192.168.20.0/24|
|HQ|30|192.168.30.0/24|
|Branch 1|10|192.168.11.0/24|

## Device Inventory
|Device|Platform|
|:---|:---|
|Routers|IOSv|
|Switches|IOSvL2|
|PCs|GNS3 VPCs|

## Network Topology
![Network Topology](Network%20Topology.png)

## Network Architecture
The design of the HQ network separates the infrastructure into edge, distribution and access layers.

At HQ, two Layer 3 distribution switches provide inter-VLAN routing and redundant default gateways using HSRP. Etherchannel is used to aggregate physical connections between the two distribution switches and OSPF provides dynamic routing between the internal devices.

The enterprise network connects to a simulated ISP using edge routers, with BGP providing external routing. GRE tunnels are used to provide connectivity between HQ and the branch network and OSPF is used to advertise routes between the sites.

A centralised DHCP service is also situated in the HQ network which provides the IP configuration for all client devices. DHCP relay is used for each VLAN to discover the server.
