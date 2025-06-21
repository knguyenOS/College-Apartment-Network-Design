![banner](https://informationage-production.s3.amazonaws.com/uploads/2022/10/AdobeStock_144479354-1568x1039.jpeg)

# Table of Contents
- [College Apartment Network Design Project](#college-apartment-network-design-project)
  - [Description](#description)
  - [Objectives](#objectives)
  - [Programs and Applications Used](#programs-and-applications-used)
  - [Features](#features)
- [Walk-through](#walk-through)
  - [The Initial Design](#the-initial-design)
  - [Final Draft](#final-draft)
  - [DHCP and VLAN Configuration](#dhcp-and-vlan-configuration)
- [Floor Plans](#floor-plans)

# College Apartment Network Design Project
This project was developed for my CIS 2347 Infrastructure and Networking course. The scenario involves designing a secure and scalable network for a luxury residence hall at the University of Houston, intended for student housing.

## Description
- An 8-story building contains 162 two-bedroom, one-bathroom apartments spread across six residential floors.
- The **1st floor** includes a lobby, an office space, and a centralized server room.
- The **2nd floor** is dedicated to conference rooms
- A surrounding parking garage on floors 1 and 2 results in reduced floor dimensions compared to the residential levels.

## Objectives
- Design a **secure, efficient, and cost-effective** network infrastructure.
- **Isolate high-value data and critical infrastructure** through segmentation.
- Create a layout that supports future **expansion and scalability**.
- Provide **visual diagrams** of floor plans with labeled network components.

## Programs and Applications Used
- **Microsoft Visio** - for network topology and floor plan diagrams.
- **Packet Tracer** - for simulation and logical design of the network.

## Features
- **Secure Network Segmentation**
  - Utilizes VLANs to separate traffic based on user roles (infrastructure, employees, residents, and guests)

- **Robust Hardware Configuration**
  - Deploys access switches, core switches, wireless access points (WAPs) and servers supporting Active Directory and DHCP, with RAID support

- **Scalable Infrastructure Design**  
  - Implements modular server racks sufficient ports and physical space to accomodate future growth

- **Power Protection & Disaster Recovery**
  - Each rack includes an Uninterruptible Power Supply (UPS) and are connected to RAID-enabled servers, with off-site backup on AWS

- **Comprehensive Cost Breakdown**  
  - Total estimated project cost: **$120,000+**, with detailed line items for each network component  

# Walk-through
This project required a significant amount of time and effort to draft the initial network layout and gain a broader understanding of the building’s structure and network flow (e.g., using tools like Packet Tracer). Throughout the process, I encountered several challenges—such as determining the correct layout scale, estimating the WAPs coverage areas, and ensuring efficient device placement.

For context, this was my largest project to date and was the final assignment for my CIS 2347: Network Design and Infrastructure course. The assignment required specific deliverables such as a cost estimate, IP configuration plan, and network layout. Out of passion and ambition, I went well beyond the core requirements by diving deeply into areas like:
- Detailed rack configurations
- Service planning for disaster recovery
- Custom DHCP setup and server configuration

## The Initial Design
At the start of the project, I wanted to have a clear logical overview of the network, which led me to begin drafting in Cisco Packet Tracer. I haven't touched the program in a while so I spent first few days going through tutorials and building small networks to get familar again with the interface. After some time, I felt ready and I created my first design which captured the general direction I envisioned. The problem was that it became overly inefficient and tedious to configure. As a result, I made the decision to start over entirely and rebuild a cleaner, more scalable design from scratch.

<div align="center">
  <img src="/Diagrams/PT_Initial_Layout.png" alt="Packet Tracer Layout Draft" height="800">
</div>

## Final Draft
I felt much more confident working on this version of the design, as it was better scaled and no longer required me to meticulously configure each device manually. With a solid foundation in place, I began configuring VLANs and DHCP services to work together across the network. Before starting, I analyzed the layout of the network and conceptualized organizing the network into three distinct VLAN groups.

However, configuring the DHCP server to properly support multiple VLANs and setting up the switches accordingly proved to be a complex and frustrating challenge. Despite the frustration, I persisted, and succeeded in getting the configuration to work. Ultimately I learned trunk and access port during this process

<div align="center">
  <img src="/Diagrams/PTLayout.png">
</div>

### DHCP and VLAN Configuration
<div align="center">
  <img src="/Diagrams/DHCP-Configuration.png" alt="DHCP Configuration" height="500">
</div>

# Floor Plans
The wireless access point (WAP) coverage areas were estimated based on the building’s dimensions, using informed assumptions. Floors 1 and 2 are smaller—approximately 100 by 70 feet—due to the surrounding parking garage, while the residential floors (3–8) are significantly larger at 240 by 150 feet. The coverage visualization includes both 2.4GHz and 5GHz bands, represented by yellow and red circles, respectively.

All circuits that form the access layer will utilize Cat5e cables as they provide sufficient bandwidth, supporting speeds up to 1 Gbps for daily work and network traffic. For the backbone which interconnects with other switches and the various buildings on campus, Cat6A cables would be used as it supports speeds up to 10 Gbps, making it ideal to handle the increased traffic and higher throughput demands of the backbone and core

## First Floor:
<div align="center">
  <img src="/Diagrams/Floor1.png" alt="First Floor Diagram" height="500">
</div>

## Second Floor:
<div align="center">
  <img src="/Diagrams/Floor2.png" alt="Second Floor Diagram" height="500">
</div>

## Third to Eighth Floors:
<div align="center">
  <img src="/Diagrams/Floor3-8.png" alt="Third to Eighth Floor Diagram" height="500">
</div>

## 2.4GHz Channel Layout:
<div align="center">
  <img src="/Diagrams/2.4GHz-Channel-Configuration.png" alt="2.4GHz Channel Diagram" height="500">
</div>


