![banner](https://informationage-production.s3.amazonaws.com/uploads/2022/10/AdobeStock_144479354-1568x1039.jpeg)

# College Apartment Network Design Documentation
_A detailed technical overview of my final project for CIS 2347: Infrastructure and Networking._

# Table of Contents
- [Project Overview](#college-apartment-network-design-project)
  - [Description](#description)
  - [Objectives](#objectives)
  - [Tools Used](#programs-and-applications-used)
  - [Key Features](#features)
- [Project Walkthrough](#walk-through)
  - [Initial Design](#the-initial-design)
  - [Final Draft](#final-draft)
  - [DHCP & VLAN](#dhcp-and-vlan-configuration)
- [Hardware & Infrastructure](#robust-hardware-configuration)
  - [Power & Disaster Recovery](#power-protection--disaster-recovery)
  - [Scalability](#scalable-infrastructure-design)
- [Budget & Equipment](#comprehensive-cost-breakdown)
- [Floor Plans & Channel Layout](#floor-plans)
- [Conclusion](#conclusion)
  - [Lessons Learned](#lessons-learned)
  - [Final Thoughts](#final-thoughts)

# College Apartment Network Design Project
This project was developed for my CIS 2347 Infrastructure and Networking course. The scenario involves designing a secure and scalable network for a luxury residence hall at the University of Houston, intended for student housing.

## Description
- An 8-story building contains **162 two-bedroom, one-bathroom apartments** spread across **six residential floors**.
- The **1st floor** includes a lobby, an office space, and a centralized server room.
- The **2nd floor** is dedicated to conference rooms.
- [Click here for floor plans](#floor-plans)

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
  - Utilizes VLANs (Virtual Local Area Network) to separate traffic based on user roles (infrastructure, employees, residents, and guests).

- **Robust Hardware Configuration**
  - Deploys access switches, core switches, wireless access points (WAPs), and servers supporting Active Directory (AD) and Dynamic Host Configuration Protocol (DHCP), with RAID (Redundant Array of Independent Disks) support.

- **Scalable Infrastructure Design**  
  - Implements modular server racks with sufficient ports and physical space to accommodate future growth.

- **Power Protection & Disaster Recovery**
  - Each rack includes an Uninterruptible Power Supply (UPS), which is connected to RAID-enabled servers with off-site backup on AWS.

- **Comprehensive Cost Breakdown**  
  - Total estimated project cost: **$120,000+**, with detailed line items for each network component.

# Walk-through
This project required a significant amount of time and effort to not only draft the initial layout but also to structure the entire network to work cohesively. It pushed me to think more about scaling the design, estimating WAP coverage, and ensuring efficient device placement. Throughout the process, I encountered several challenges that led to frustration and restless nights, but those same moments helped me grow and learn far more about practical network design.

> For reference, this is my **largest and most comprehensive project** to date, involving hands-on work with **desigining, configuring, and setting up server rack configuration**.

## The Initial Design
<p align="center">
  <img src="/Diagrams/PT_Initial_Layout.png" alt="Initial logical network draft" height="700"><br>
  <em>This version reflected my initial vision but quickly became overly inefficient and tedious to manage.</em>
</p>

## Final Draft
<p align="center">
  <img src="/Diagrams/PTLayout.png" alt="Final logical network"><br>
  <em>This scaled-down version significantly reduced the complexity of managing and configuring multiple devices.</em>
</p>

## DHCP and VLAN Configuration
<p align="center">
  <img src="/Diagrams/DHCP-Configuration.png" alt="DHCP Configuration" height="600"><br>
  <em>Configuring VLANs on the DHCP server and switches took many hours of errors and troubleshooting</em>
</p>

# Robust Hardware Configuration
**Cisco Catalyst 1200** access switches with 48 ports  
- Support both Power over Ethernet (PoE) and SFP+ uplinks  
- Deliver up to 1 Gbps per port while powering connected WAPs and reducing setup complexity  

**Cisco Catalyst 1300-24XS** core switches  
- Optimized for high-speed backbone interconnects using SFP+ transceivers and Cat6A cabling  
- Ensure fast data delivery and redundancy between floors  

All switches are **rack-mountable** and housed in **server racks** per floor.  
- Each floor contains an intermediate distribution frame (IDF) room for housing the server rack  
- Core equipments such as servers, switches, and routers are centralized in a 24U server rack in the main distribution frame (MDF)

To serve authentication and addressing needs:  
- Two **Dell PowerEdge R240** servers run AD and DHCP for identity management and VLAN-based traffic segmentation  
- These servers are backed with RAID support and can be expanded as needed  

# Scalable Infrastructure Design
Each floor's server rack contains 7U of available space after fitting switches, patch panels, and UPS.  
- Allows for the addition of switches, monitoring equipment, or storage arrays  

The network topology uses a hybrid routed and switched backbone architecture, balancing performance with flexibility.  
- Each access switch is connected to two core switches for redundancy and load balancing  
- Modular components like patch panels, keystone jacks, and transceivers allow for quick replacement and expansion without rewiring the entire system  

The use of bulk Cat5e and Cat6A spools, along with modular cabling infrastructure, ensures new Ethernet drops and endpoints can be added without major overhauls. **802.1Q VLAN tagging** and **dynamic VLAN assignment via RADIUS and Active Directory** further improve logical scalability.

<p align="center">
  <img src="/Diagrams/Network-Closet-Switch-Configuration.png" alt="Cable configuration of switches on server rack" height="700"><br>
  <em>General layout of how cables are configured on access switches. Green indicates Ethernet drops to resident rooms. Red indicates WAPs.</em>
</p>

# Power Protection & Disaster Recovery
Every rack is equipped with a **CyberPower Smart App Intelligent LCD OR2200LCDRT2U UPS**  
- Delivers **2000VA** of backup power and **surge protection**  
- Can sustain operation for several minutes during a power outage  
- Enough time for **safe shutdowns** or **auto-failover** to backup systems  

To enhance data resilience, a dual-layered backup approach is suggested:  
- Local backups are hosted on the **main servers** for fast file restoration in case of minor failures  
- Off-site **cloud backups via AWS** ensure continuity during **catastrophic events** like natural disasters  

# Comprehensive Cost Breakdown
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
**Floors 1-2**
- Approximately **100 by 70 feet**, due to the surrounding parking garage.

**Floors 3–8**
- Approximately **240 by 150 feet**.

**Ethernet Drops**
- Visualized by a blue rectangle in each room
- #'s of drops represented by the nodes/arms

**WAP coverage visualization**
- **2.4GHz** represented by **yellow** circles
- **5GHz** represented by **red** circles

All circuits that form the **access layer** utilize **Cat5e cables** (highlighted in **green**), while **backbone cables** use **Cat6A** (highlighted in **orange**).

## First Floor: [⬆️ Back to top](#college-apartment-network-design-project)
<p align="center">
  <img src="/Diagrams/Floor1.png" alt="First Floor Diagram" height="500">
</p>

## Second Floor: [⬆️ Back to top](#college-apartment-network-design-project)
<p align="center">
  <img src="/Diagrams/Floor2.png" alt="Second Floor Diagram" height="500">
</p>

## Third to Eighth Floors: [⬆️ Back to top](#college-apartment-network-design-project)
<p align="center">
  <img src="/Diagrams/Floor3-8.png" alt="Third to Eighth Floor Diagram" height="500">
</p>

## 2.4GHz Channel Layout: [⬆️ Back to top](#college-apartment-network-design-project)

<p align="center">
  <img src="/Diagrams/2.4GHz-Channel-Configuration.png" alt="2.4GHz Channel Diagram" height="500">
</p>

# Conclusion

## Lessons Learned
Though this documentation doesn't cover every step and moment of frustration, this project taught me a lot about the real-world complexities involved in designing scalable networks. From planning for scalability to implementing failover strategies, I gained confidence in configuring VLANs, simulating networks in Packet Tracer, and researching components and features more intuitively.

Looking back, here are some notable things I would do differently if I had the chance to start over:
- Start prototyping sooner
- Rely less on trial-and-error
- Focus on one step at a time
- Recognize when I'm taking on too much

## Final Thoughts
This project was an incredibly fun and valuable learning experience, despite the many restless nights and frustrating challenges along the way. In hindsight, the most rewarding part was realizing how ambitious I can be when I’m truly passionate about a goal or project.
