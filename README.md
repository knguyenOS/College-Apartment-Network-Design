![banner](https://informationage-production.s3.amazonaws.com/uploads/2022/10/AdobeStock_144479354-1568x1039.jpeg)

# Table of contents
- [College Apartment Network Design Project](#college-apartment-network-design-project)
- [Walk-Through](#walk-through)

# College Apartment Network Design Project
This project was developed for my CIS 2347 Infrastructure and Networking course. The scenario involves designing a secure and scalable network for a luxury residence hall at the University of Houston, intended for student housing.

## Description
-  An 8-story building contains 162 two-bedroom, one-bathroom apartments spread across six residential floors.
-  The **1st floor** includes a lobby, an office space, and a centralized server room.
-  The **2nd floor** is dedicated to conference rooms
-  A surrounding parking garage on floors 1 and 2 results in reduced floor dimensions compared to the residential levels.

## Objectives
- Design a **secure, efficient, and cost-effective** network infrastructure.
- **Isolate high-value data and critical infrastructure** through segmentation.
- Create a layout that supports future **expansion and scalability**.
- Provide **visual diagrams** of floor plans with labeled network components.

## Programs and Applications Used
- Microsoft Visio - for network topology and floor plan diagrams.
- Packet Tracer - for simulation and logical design of the network.

## Features
- **Secure Network Segmentation**
  - Utilizes VLANs to separate traffic based on user roles (infrastructure, employees, residents, and guests)

- **Robust Hardware Configuration**
  - Deploys access switches, core switches, wireless access points (WAPs) and servers supporting Active Directory and DHCP, with with RAID support

- **Scalable Infrastructure Design**  
  - Implements modular server racks sufficient ports and physical space to accomodate future growth

- **Power Protection & Disaster Recovery**
  - Each rack includes an Uninterruptible Power Supply (UPS) and are connected to RAID-enabled servers, with off-site backup on AWS

- **Comprehensive Cost Breakdown**  
  - Total estimated project cost: **$120,000+**, with detailed line items for each network component  

# Walk-through
This project an extreme amount of time on my end drafting the initial layout to get a bigger picture of the layout (i.e., using Wireshark). I've also faced many issues such as determining the scale of the layout, the approximate coverage of the WAPs and various other.
For context, this was the final project for CIS 2347 network design and infrastructure. I needed to fill specific criterias such asp providing the cost estimation, IPs configuration, and layout. However, I went far above what was asked of me such as going incredibly
in-depth regarding rack configurations, services required for disaster recovery, and configuring DHCP which I would provide.

## Visualizing and testing the layout
When I initially started the project, I wanted to be able to logically see the design of the network and so started graphing up in packet tracer. For the first design, I had a good idea of the direction of where I wanted to go, however, had to completely startover from
scratch due to how needlessly over-complicated I made it.

<div align="center">
  <img src="/Diagrams/PT_Initial_Layout.png" alt="Packet Tracer Layout Draft" height="800">
</div>

### Packet Tracer - Final Draft
<div align="center">
  <img src="/Diagrams/PTLayout.png">
</div>

# Diagrams

### First Floor:
<div align="center">
  <img src="/Diagrams/Floor1.png" alt="First Floor Diagram" height="500">
</div>

### Second Floor:
<div align="center">
  <img src="/Diagrams/Floor2.png" alt="Second Floor Diagram" height="500">
</div>

### Third to Eighth Floors:
<div align="center">
  <img src="/Diagrams/Floor3-8.png" alt="Third to Eighth Floor Diagram" height="500">
</div>

### 2.4GHz Channel Layout:
<div align="center">
  <img src="/Diagrams/2.4GHz-Channel-Configuration.png" alt="2.4GHz Channel Diagram" height="500">
</div>


