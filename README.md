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
  - [First Floor](#first-floor)
  - [Second Floor](#second-floor)
  - [Third to Eighth Floors](#third-to-eighth-floors)
  - [2.4GHz Channel Layout](#24ghz-channel-layout)

# College Apartment Network Design Project
This project was developed for my CIS 2347 Infrastructure and Networking course. The scenario involves designing a secure and scalable network for a luxury residence hall at the University of Houston, intended for student housing.

## Description
- An 8-story building contains 162 two-bedroom, one-bathroom apartments spread across six residential floors.
- The **1st floor** includes a lobby, an office space, and a centralized server room.
- The **2nd floor** is dedicated to conference rooms.
- A surrounding parking garage on floors 1 and 2 results in reduced floor dimensions compared to the residential levels.

## Objectives
- Design a **secure, efficient, and cost-effective** network infrastructure.
- **Isolate high-value data and critical infrastructure** through segmentation.
- Create a layout that supports future **expansion and scalability**.
- Provide **visual diagrams** of floor plans with labeled network components.

## Programs and Applications Used
- **Microsoft Visio** – for network topology and floor plan diagrams.
- **Packet Tracer** – for simulation and logical design of the network.

## Features
- **Secure Network Segmentation**
  - Utilizes VLANs to separate traffic based on user roles (infrastructure, employees, residents, and guests).

- **Robust Hardware Configuration**
  - Deploys access switches, core switches, wireless access points (WAPs), and servers supporting Active Directory and DHCP, with RAID support.

- **Scalable Infrastructure Design**  
  - Implements modular server racks with sufficient ports and physical space to accommodate future growth.

- **Power Protection & Disaster Recovery**
  - Each rack includes an Uninterruptible Power Supply (UPS), which is connected to RAID-enabled servers with off-site backup on AWS.

- **Comprehensive Cost Breakdown**  
  - Total estimated project cost: **$120,000+**, with detailed line items for each network component.

# Walk-through
This project required a significant amount of time and effort to draft the initial network layout and gain a broader understanding of the building’s structure and network flow (e.g., using tools like Packet Tracer). Throughout the process, I encountered several challenges—such as determining the correct layout scale, estimating the WAP coverage areas, and ensuring efficient device placement.

For context, this was my largest project to date and was the final assignment for my CIS 2347: Network Design and Infrastructure course. The assignment required specific deliverables such as a cost estimate, IP configuration plan, and network layout. Out of passion and ambition, I went well beyond the core requirements by diving deeply into areas like:
- Detailed rack configurations.
- Service planning for disaster recovery.
- Custom DHCP setup and server configuration.

## The Initial Design
At the start of the project, I wanted to have a clear logical overview of the network, which led me to begin drafting in Cisco Packet Tracer. I hadn't touched the program in a while, so I spent the first few days going through tutorials and building small networks to get familiar with the interface. After some time, I felt ready and created my first design.

This captured the general direction I envisioned, however, became overly inefficient and tedious to configure. I made the decision to start over entirely and rebuild a cleaner, more scalable design from scratch.

<div align="center">
  <img src="/Diagrams/PT_Initial_Layout.png" alt="Packet Tracer Layout Draft" height="700">
  <br>
  <em>Captured the general direction I envisioned, however, became overly inefficient and tedious to configure and so was scrapped.</em>
</div>

## Final Draft

<div align="center">
  <img src="/Diagrams/PTLayout.png" alt="Final Packet Tracer Layout">
  <br>
  <em>This newer scaled down version led to way less headaches needing to track and configure every switches.</em>
</div>

## Secure Network Segmentation
With a solid foundation in place, I began configuring VLANs and DHCP services to work together across the network. Before starting, I analyzed the layout of the network and conceptualized organizing it into 4 distinct VLAN groups.
- VLAN 30
- VLAN 20
- VLAN 10

However, configuring the DHCP server to properly support multiple VLANs and setting up the switches accordingly proved to be a complex and frustrating challenge. Despite the frustration, I persisted and succeeded in getting the configuration to work. Ultimately, I gained hands-on experience with trunk and access ports during this process.

### DHCP and VLAN Configuration
<div align="center">
  <img src="/Diagrams/DHCP-Configuration.png" alt="DHCP Configuration" height="600">
  <br>
  <em>Configuring this page took many hours understanding how default gateways work in a VLAN level and even more configuring the switches to work with it.</em>
</div>

## Robust Hardware Configuration
**Cisco Catalyst 1200** access switches with 48 ports 
- Support both Power over Ethernet (PoE) and SFP+ uplinks
- Delivers up to 1 Gbps per port while powering connected WAPs and reducing setup complexity.

**Cisco Catalyst 1300-24XS** core switches 
- Optimized for high-speed backbone interconnects using SFP+ transceivers and Cat6A cabling
- Ensures fast data delivery and redundancy between floors.

All switches are rack-mountable and housed in StarTech.com 18U server racks per floor. Core equipment—including servers, routers, and patch panels—are centralized in a Tripp Lite 24U server enclosure located in the main distribution frame (MDF). Network devices are organized using blank keystone patch panels, Cat5e/Cat6 cables, and RJ45 connectors, enabling clean, scalable cabling layouts.

To serve authentication and addressing needs, two Dell PowerEdge R240 servers run Active Directory and DHCP, allowing for centralized identity management, dynamic IP allocation, and VLAN-based traffic segmentation. These servers are backed with RAID support and can be expanded as needed.


## Scalable Infrastructure Design
Each floor's server rack contains 7U of available space after fitting switches, patch panels, and UPS.
- Allows for the addition of switches, monitoring equipment, or storage arrays.

The network topology uses a hybrid routed and switched backbone architecture, balancing performance with flexibility. 
- Each access switch is connected to two core switches for redundancy and load balancing.
- Modular components like patch panels, keystone jacks, and transceivers allow for quick replacement and addition without rewiring the entire system.

The use of bulk Cat5e and Cat6A spools, along with modular cabling infrastructure, ensures new Ethernet drops and endpoints can be added without major overhauls. 802.1Q VLAN tagging and dynamic VLAN assignment via RADIUS and Active Directory further improve logical scalability, enabling seamless segmentation of new users and devices.

<div align="center">
  <img src="/Diagrams/Network-Closet-Switch-Configuration.png" height="700">
  <br>
  <em>General idea of how the cables are to be configured on the switches. Green is the ethernet drops in resident's room. Red is the floor's WAPs</em>
</div>

## Power Protection & Disaster Recovery
Every rack is equipped with a **CyberPower Smart App Intelligent LCD OR2200LCDRT2U UPS** 
- Delivers **2000VA** of backup power and **surge protection**
- Can sustain operation for **several minutes** during a power outage
- Enough time for **safe shutdowns** or **auto-failover** to backup systems.

To enhance data resilience, a dual-layered backup approach is suggested:
- Local backups are hosted on the **main servers** for **fast file restoration** in case of minor failures.
- Off-site **cloud backups via AWS** ensure continuity during **catastrophic events** like natural disasters.

## Comprehensive Cost Breakdown
This network design balances **performance, scalability, and cost**. With an estimated total of **$120,017.30**, each component was chosen not just for compatibility, but also for long-term value and reliability. The budget covers:
- Wireless Access Points
- Server Racks
- Switches
- Cables
- Connectors
- Software License

| Equipment                       | Product Name                                                                    | Quantity | Cost per Item | Total Cost   |
|--------------------------------|----------------------------------------------------------------------------------|----------|---------------|--------------|
| Server Rack                    | StarTech.com 4-Post 18U Open Frame Server Rack                                  | 6        | $277.99       | $1,667.94    |
| Server Rack                    | StarTech.com 4-Post 24U Server Rack Cabinet                                     | 1        | $839.00       | $839.00      |
| Uninterruptible Power Supply   | CyberPower Smart App Intelligent LCD OR2200LCDRT2U                              | 7        | $604.95       | $4,234.65    |
| Server                         | Dell PowerEdge R240                                                             | 2        | $1,037.00     | $2,074.00    |
| Router                         | Cisco Catalyst 8200-1N-4T                                                       | 1        | $1,739.99     | $1,739.99    |
| Switch                         | Cisco Catalyst 1200-48P-4X                                                      | 20       | $1,189.99     | $23,799.80   |
| Switch                         | Cisco Catalyst 1300-24XS                                                        | 2        | $2,243.99     | $4,487.98    |
| Transceiver                    | Tripp Lite SFP+ Transceiver RJ45 Cat6a 98ft                                     | 84       | $174.99       | $14,699.16   |
| Wireless Access Points         | Cisco Business 140AC                                                            | 58       | $88.99        | $5,161.42    |
| Wall Plate                     | C2G Two Port Cat5E RJ45                                                         | 344      | $9.12         | $3,137.28    |
| RJ45 Connectors                | Belkin network connector (100 pack)                                             | 15       | $19.99        | $299.85      |
| Cable                          | Black Box GigaBase 350 CAT5e 1000ft Spool                                       | 120      | $259.99       | $31,198.80   |
| Cable                          | Monoprice Cat6 500ft Spool                                                      | 4        | $89.99        | $359.96      |
| Patch Cable                    | Monoprice Cat5e 6in Black Patch Cable                                           | 744      | $0.89         | $662.16      |
| Patch Cable (switches)         | Monoprice Cat6A 6in Blue Patch Cable                                            | 36       | $0.99         | $35.64       |
| Blank Patch Panels             | Tripp Lite 24-Port 1U Rack-Mount Shielded Blank Keystone/Multimedia Patch Panel | 36       | $39.99        | $1,439.64    |
| Network Access Control Software| Cisco Identity Services Engine Device Admin - license                           | 1        | $8,629.99     | $8,629.99    |
| DHCP Software                  | Cisco Prime Network Registrar DHCP                                              | 1        | $16,250.00    | $16,250.00   |
|                                |                                                                                  |          | **Total**     | **$120,017.30** |


# Floor Plans
The wireless access point (WAP) coverage areas were estimated based on the building’s dimensions, using informed assumptions. Floors 1 and 2 are smaller—approximately 100 by 70 feet—due to the surrounding parking garage, while the residential floors (3–8) are significantly larger at 240 by 150 feet. The coverage visualization includes both 2.4GHz and 5GHz bands, represented by yellow and red circles, respectively.

All circuits that form the access layer will utilize Cat5e cables, as they provide sufficient bandwidth to support speeds up to 1 Gbps for daily work and network traffic. For the backbone—which interconnects with other switches and buildings on campus—Cat6A cables will be used, as they support speeds up to 10 Gbps, making them ideal for handling increased traffic and higher throughput demands at the core.

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
