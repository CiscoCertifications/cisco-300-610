# Cisco 300-610 DCID Exam: Designing Cisco Data Center Infrastructure

[![Cisco Certified](https://img.shields.io/badge/Cisco_Certified-CCNP_Data_Center_|_DCID-049fd9?style=for-the-badge&logo=cisco&logoColor=white)](https://www.cisco.com/)
[![Track](https://img.shields.io/badge/Track-Data_Center_Design-049fd9?style=for-the-badge&logo=cisco)](https://www.cisco.com/)
[![Level](https://img.shields.io/badge/Level-Professional_Concentration-1BA0D7?style=for-the-badge)](https://www.cisco.com/)
[![Duration](https://img.shields.io/badge/Duration-90_Minutes-orange?style=for-the-badge)](https://www.cisco.com/)
[![Score](https://img.shields.io/badge/Passing_Score-~825%20%2F%201000-blue?style=for-the-badge)](https://www.cisco.com/)
[![Practice Partner](https://img.shields.io/badge/Practice_Partner-CertsClub_(20%25_Off_Code:_club20)-28a745?style=for-the-badge&logo=shield)](https://www.certsclub.com/cisco/)

---

## 1. Exam Overview & Candidate Profile

The **Cisco 300-610 DCID (Designing Cisco Data Center Infrastructure)** exam tests a candidate's architectural knowledge of designing scalable, resilient, and high-performance data center infrastructure solutions. The examination verifies design expertise across Cisco Nexus leaf-spine networks, VXLAN EVPN overlays, Data Center Interconnect (DCI), Cisco Unified Computing System (UCS B-Series, C-Series, and X-Series), hyperconverged systems (Cisco HyperFlex), Storage Area Networks (Fibre Channel, FCoE, NVMe-oF, Smart Zoning), and software-defined automation using Cisco ACI (Multi-Pod, Multi-Site, Nexus Dashboard).

Passing the 300-610 DCID exam earns the **Cisco Certified Specialist - Data Center Design** certification and satisfies the concentration requirement for the **CCNP Data Center** certification.

### Target Candidate Profile & Roles
* **Data Center Solutions Architect & Infrastructure Designer**
* **Principal Enterprise Cloud & Fabric Engineer**
* **Senior Pre-Sales / Post-Sales Technical Systems Architect**
* **Data Center Infrastructure Consulting Specialist**
* **Prerequisites:** In-depth knowledge of data center switching, storage protocols, virtualization, and server compute (CCNP DCCOR level).

---

## 2. Key Exam Specifications

| Parameter | Official Specification |
| :--- | :--- |
| **Exam Code** | 300-610 |
| **Exam Name** | Designing Cisco Data Center Infrastructure (DCID) |
| **Associated Credential** | Cisco Certified Specialist - Data Center Design / CCNP Data Center |
| **Duration** | 90 Minutes |
| **Passing Score** | ~825 / 1000 (Scaled dynamic calibration) |
| **Question Count** | 55–65 questions |
| **Question Formats** | Multiple Choice (single/multiple select), Drag-and-Drop, Architectural Scenarios |
| **Delivery Vendor** | Pearson VUE Authorized Test Centers & OnVUE Online Remote Proctored |
| **Practice Test Partner** | **[300-610 Practice Test](https://www.certsclub.com/cisco/)** (Coupon: `club20` for 20% off) |

---

## 3. Skills Measured & Blueprint Domain Weighting

| Domain Code | Domain Title | Exam Weight | Key Technical Objectives Covered |
| :--- | :--- | :---: | :--- |
| **1.0** | **Network Design** | **35%** | Leaf-and-spine Clos architecture; oversubscription ratios and ECMP; Routing protocols in data centers (eBGP underlay, OSPF, IS-IS); VXLAN BGP EVPN fabric design (distributed anycast gateway, L2/L3 VNI, vPC with VXLAN); Data Center Interconnect (DCI: VXLAN EVPN Multi-Site, OTV, MPLS); High availability (vPC Peer-Gateway, Peer-Switch). |
| **2.0** | **Compute Design** | **25%** | Cisco UCS architecture (Fabric Interconnects, I/O Modules, Chassis, X-Series); Fabric Interconnect End-Host Mode (EHM) vs. Switch Mode; Hyperconverged compute solutions (Cisco HyperFlex cluster sizing, edge vs. standard); Compute management (Cisco Intersight SaaS vs. UCS Manager). |
| **3.0** | **Storage Network Design** | **20%** | SAN architecture (Dual-fabric redundant SAN, VSAN design); Inter-VSAN Routing (IVR); Fibre Channel zoning (Smart Zoning, WWPN vs. Device Alias); Buffer-to-Buffer (B2B) credit calculation for extended distances; Storage protocols (FC, FCoE, iSCSI, NVMe over Fabrics). |
| **4.0** | **Automation Design** | **20%** | Cisco ACI fabric topologies: Multi-Pod vs. Multi-Site vs. Remote Leaf vs. ACI Virtual Edge; Orchestration via Cisco Nexus Dashboard Orchestrator (NDO); Telemetry and monitoring design (Nexus Dashboard Insights, streaming gRPC telemetry). |

---

## 4. Scenario-Based Technical Practice Questions

### Scenario 1: Spine-and-Leaf Fabric Design - Oversubscription Ratio Calculation
**Topology Background:**  
A data center architect designs a 2-tier leaf-and-spine network using Cisco Nexus 9300 switches. Each leaf switch has forty-eight 10Gbps server-facing downlink access ports and six 100Gbps uplink ports connected to spine switches. What is the calculated fabric oversubscription ratio, and does it meet standard enterprise recommendations ($\le 3:1$)?

* A. 4:1 oversubscription; does not meet standard
* B. 0.8:1 (non-blocking line rate); meets standard
* C. 1.2:1 oversubscription ($480\text{ Gbps down} : 600\text{ Gbps up}$); provides non-blocking capacity exceeding standards
* D. 8:1 oversubscription; requires redesign

**Correct Answer:** **C**

**Detailed Technical Explanation:**  
* Oversubscription ratio calculation:
  * **Downlink capacity (Servers):** $48 \times 10\text{ Gbps} = 480\text{ Gbps}$.
  * **Uplink capacity (Spines):** $6 \times 100\text{ Gbps} = 600\text{ Gbps}$.
  * Ratio: $\frac{480}{600} = 0.8 : 1$ (or $1 : 1.25$ overprovisioned uplink bandwidth).
* Because the uplink capacity ($600\text{ Gbps}$) exceeds the total possible downlink bandwidth ($480\text{ Gbps}$), this design is completely **non-blocking** at full wire speed and easily complies with the enterprise guideline ($\le 3:1$).
* Distractor analysis: Option A calculates 48/12. Option B misstates the exact ratio. Option D miscalculates 48/6.

---

### Scenario 2: Data Center Interconnect - VXLAN EVPN Multi-Site Architecture
**Topology Background:**  
An enterprise connects two geographically separated data centers over an unmanaged Layer 3 IP routed transport. The business requires seamless Layer 2 LAN extension and Layer 3 host mobility between sites without extending internal site IGP protocols or creating Spanning Tree dependencies across the WAN. Which DCI architecture should the architect recommend?

* A. Back-to-back vPC across dark fiber
* B. VXLAN EVPN Multi-Site utilizing Border Gateways (BGs)
* C. Traditional 802.1Q trunking over leased lines
* D. Static GRE tunnels between server hypervisors

**Correct Answer:** **B**

**Detailed Technical Explanation:**  
* **VXLAN EVPN Multi-Site (RFC 9014):**
  * Solves the scalability and fault-domain limitations of older DCI technologies (like OTV or stretched fabrics).
  * Dedicated leaf nodes act as **Border Gateways (BGs)** at each site.
  * Internal site BGP EVPN peering and underlay IGPs remain completely isolated within each site.
  * Border Gateways terminate local VXLAN tunnels, rewrite next-hops, and re-encapsulate traffic into inter-site VXLAN tunnels across the routed IP network.
  * Failure domains, BUM traffic suppression, and broadcast loops are contained locally, preventing site outages from cascading across the WAN.
* Distractor analysis: Option A is impossible over routed IP networks. Option C extends broadcast storms and STP loops across data centers. Option D introduces severe MTU and management overhead.

---

### Scenario 3: Cisco UCS Fabric Interconnect - End-Host Mode vs. Switch Mode
**Topology Background:**  
A network architect designs a Cisco UCS deployment connecting Fabric Interconnects (FIs) to upstream Cisco Nexus 9000 core aggregation switches. To adhere to Cisco best practices, the architect configures the Fabric Interconnects in the default **End-Host Mode (EHM)** rather than Switch Mode. What is the primary operational advantage of End-Host Mode?

* A. The Fabric Interconnects run full Spanning Tree Protocol (STP), forcing core switches to block uplink ports.
* B. The Fabric Interconnects appear to the upstream network as a collection of host servers (NICs) rather than switches; Spanning Tree Protocol (STP) is completely disabled on the FIs, preventing STP recalculations, eliminating loop risks, and allowing all uplinks to be fully utilized active/active.
* C. FIs automatically assign public IP addresses to all blades.
* D. It permits blades to route BGP directly into the SAN.

**Correct Answer:** **B**

**Detailed Technical Explanation:**  
* In **Cisco UCS End-Host Mode (EHM)**:
  * The Fabric Interconnects do **not** run Spanning Tree Protocol (STP). They do not transmit BPDUs upstream.
  * To the upstream Nexus switches, the entire UCS domain appears as a standard multi-homed server endpoint.
  * **Benefits:**
    1. Uplinks to upstream switches never block due to STP; traffic is pinned or bundled across all uplinks.
    2. Any topology changes or blade additions within UCS cause zero STP flaps in the upstream core network.
    3. Loop avoidance inside UCS is handled deterministically by internal fabric pinning and reverse path validation.
* Distractor analysis: Option A describes Switch Mode, which runs STP and introduces port blocking. Options C and D are false.

---

### Scenario 4: Storage Area Networking - Smart Zoning in Cisco MDS Switches
**Topology Background:**  
A storage architect designs a large Fibre Channel SAN fabric on Cisco MDS 9710 director switches connecting 500 initiators (servers) and 20 target storage ports in a single VSAN. Traditional Single-Initiator/Single-Target zoning requires 10,000 zone definitions, exhausting hardware TCAM entries. Which Cisco MDS SAN feature reduces TCAM exhaustion while maintaining zoning isolation?

* A. Hard Zoning
* B. Smart Zoning
* C. Port Security
* D. Inter-VSAN Routing (IVR)

**Correct Answer:** **B**

**Detailed Technical Explanation:**  
* **Smart Zoning (RFC 6138 / Cisco innovation):**
  * Allows administrators to place multiple initiators and multiple targets into a single zone definition, but requires members to be explicitly tagged as **`initiation`**, **`target`**, or **`both`**.
  * The switch hardware analyzes the tags and programs TCAM ACL entries **strictly for Initiator-to-Target pairs**, suppressing redundant and useless Initiator-to-Initiator and Target-to-Target rules.
  * This slashes hardware TCAM entry consumption by up to 90% while keeping zone administration clean and manageable.
* Distractor analysis: Option A (traditional hard zoning) exhausts TCAM. Option C is port access control. Option D routes between different VSANs.

---

### Scenario 5: Extended Distance SAN - Buffer-to-Buffer (B2B) Credit Calculation
**Topology Background:**  
An enterprise connects two data centers situated 100 kilometers apart using a 16 Gbps Fibre Channel dark fiber link between Cisco MDS switches. The average FC frame size is 2 KB. What resource must the SAN designer calculate and allocate to the inter-switch link (ISL) ports to prevent link starvation and maintain full 16 Gbps line-rate throughput over this distance?

* A. Jumbo MTU buffers
* B. Extended Buffer-to-Buffer (B2B) Credits
* C. Priority Flow Control (PFC) pause credits
* D. OSPF cost metrics

**Correct Answer:** **B**

**Detailed Technical Explanation:**  
* In Fibre Channel, flow control is managed credit-by-credit using **Buffer-to-Buffer (B2B) Credits**. A port cannot transmit a frame until it receives a receiver ready (`R_RDY`) credit acknowledgment from the distant receiver.
* Over long distances (e.g., $100\text{ km}$), propagation delay means thousands of frames are in flight simultaneously.
* Formula: $\text{B2B Credits} \approx \frac{\text{Distance (km)} \times \text{Link Speed (Gbps)}}{2 \times \text{Frame Size (KB)}} + \text{Internal processing headroom}$.
* If insufficient B2B credits are assigned, the transmitter exhausts credits and pauses transmission while waiting for `R_RDY` signals to travel back across the $100\text{ km}$ fiber, causing severe bandwidth throttling. Allocating **Extended B2B Credits** from switch buffer pools guarantees non-blocking line-rate performance.
* Distractor analysis: Option A is an Ethernet concept. Option C is Ethernet PFC. Option D is an IP routing metric.

---

### Scenario 6: Cisco ACI Architecture - Multi-Pod vs. Multi-Site
**Topology Background:**  
An enterprise operates two data center halls located across the street from each other connected via redundant low-latency ($< 5\text{ ms}$) dark fiber links. The engineering team wants a unified management fabric where a single APIC controller cluster manages both halls, creating a single availability and policy domain with an Inter-Pod Network (IPN). Which Cisco ACI architecture should the designer select?

* A. Cisco ACI Multi-Site
* B. Cisco ACI Multi-Pod
* C. Standalone NX-OS fabrics
* D. ACI Cloud APIC only

**Correct Answer:** **B**

**Detailed Technical Explanation:**  
* **Cisco ACI Multi-Pod:**
  * Uses a **single APIC controller cluster** to manage multiple pods interconnected via an **Inter-Pod Network (IPN)**.
  * Operates as a **single availability zone / single fabric domain**: policy, tenant, and contract changes are automatically global across all pods.
  * Requires low round-trip latency ($\le 50\text{ ms}$, ideally $< 5\text{ ms}$) and MTU $\ge 1550$ across the IPN.
* **Cisco ACI Multi-Site:**
  * Connects multiple **completely independent APIC fabrics** (separate management and availability domains) managed by a centralized Cisco Nexus Dashboard Orchestrator (NDO / MSO), designed for geographically dispersed data centers with higher latency and independent fault isolation.
* Distractor analysis: Option A is designed for separate independent fault domains. Option C abandons ACI policy. Option D is for public cloud instances (AWS/Azure).

---

### Scenario 7: Storage Network Design - Inter-VSAN Routing (IVR)
**Topology Background:**  
A healthcare organization maintains two separate Fibre Channel VSANs on Cisco MDS switches: `VSAN 10` (Radiology imaging) and `VSAN 20` (Cardiology records). A high-performance backup tape library resides in `VSAN 100`. The storage architect must allow servers in both `VSAN 10` and `VSAN 20` to access the tape library in `VSAN 100` without merging the VSANs or exposing them to fabric reconfigurations and zone disruption. Which technology accomplishes this?

* A. Fibre Channel Inter-VSAN Routing (IVR)
* B. VSAN Trunking
* C. FCoE VLAN Mapping
* D. Static IP Routing over FC

**Correct Answer:** **A**

**Detailed Technical Explanation:**  
* **Inter-VSAN Routing (IVR):**
  * Enables initiator devices in one VSAN to communicate with target devices in another VSAN without merging the VSANs.
  * Prevents fabric disruptions, domain ID conflicts, and zone churn from propagating across VSAN boundaries.
  * Can operate with or without IVR NAT to rewrite FC-IDs across the border switch.
* Distractor analysis: Option B (VSAN Trunking) transports multiple VSANs across an ISL, but does not route between them. Options C and D do not provide native FC inter-VSAN routing.

---

### Scenario 8: Nexus vPC Optimization - Peer-Gateway and Peer-Switch Features
**Topology Background:**  
An engineer designs a virtual PortChannel (vPC) domain on Cisco Nexus 7000 switches connecting dual-attached Network Attached Storage (NAS) appliances. Certain storage vendor controllers violate standard ARP behavior by sending packets with the source MAC address of one vPC peer switch directly to the other vPC peer switch over the vPC member link. To prevent packets from crossing and congesting the vPC peer-link, which command must be enabled on both vPC switches?

* A. `peer-gateway`
* B. `peer-switch`
* C. `ip arp gratuitous ignore`
* D. `system default switchport`

**Correct Answer:** **A**

**Detailed Technical Explanation:**  
* The **`peer-gateway`** feature:
  * Allows a vPC switch to act as the active gateway for packets addressed to the peer switch's router MAC address.
  * It intercepts and locally routes packets destined to the other peer switch's MAC address without traversing the vPC peer-link.
  * This avoids peer-link saturation and prevents dropped packets caused by non-compliant network devices and storage arrays (such as EMC/NetApp controllers) that optimize reply traffic by replying to the specific MAC from which they received traffic rather than performing ARP for their gateway.
* Distractor analysis: Option B (`peer-switch`) optimizes Spanning Tree by making both vPC switches appear as a single root bridge. Options C and D are unrelated.

---

### Scenario 9: Compute Management - Cisco Intersight SaaS vs. UCS Manager
**Topology Background:**  
An enterprise with 50 edge retail locations deploys two Cisco UCS C-Series rack servers per location. Managing each location individually via on-premises UCS Manager or CIMC web interfaces is operationally unmanageable. Which cloud-based architecture provides centralized, single-pane-of-glass policy orchestration, predictive analytics, and zero-touch server firmware compliance across all 50 sites?

* A. Cisco Intersight (SaaS)
* B. Cisco Prime Infrastructure
* C. Local UCS Manager on each server
* D. Nagios Core monitoring agent

**Correct Answer:** **A**

**Detailed Technical Explanation:**  
* **Cisco Intersight:**
  * A cloud-delivered (SaaS) systems management platform for Cisco UCS and HyperFlex infrastructure.
  * Connects securely outbound from edge devices to the Intersight cloud without requiring inbound firewall openings or on-premises management VMs.
  * Provides global server inventory, declarative server profile deployment, firmware compliance baseline enforcement, and AI-driven predictive hardware failure analytics (Connected TAC) across distributed edge and core data centers.
* Distractor analysis: Option B (Prime) is legacy network-centric management. Option C requires managing 50 disconnected GUIs. Option D is basic ping monitoring.

---

### Scenario 10: Data Center Interconnect (DCI) - Overlay Transport Virtualization (OTV)
**Topology Background:**  
A legacy enterprise data center connects to a secondary backup facility over an unmanaged carrier IP network using Cisco Overlay Transport Virtualization (OTV). How does OTV prevent Layer 2 bridging loops and eliminate broadcast storms across the core transport network without running Spanning Tree Protocol across the WAN?

* A. OTV runs standard 802.1D Spanning Tree across all WAN links.
* B. OTV terminates STP locally at each site edge, filters Spanning Tree BPDUs from crossing the overlay, and uses an Authoritative Edge Device (AED) election per VLAN along with IS-IS control-plane MAC address routing.
* C. OTV converts all Ethernet frames into ATM cells.
* D. OTV forces all traffic to route through a central cloud proxy.

**Correct Answer:** **B**

**Detailed Technical Explanation:**  
* **Overlay Transport Virtualization (OTV):**
  1. **STP Isolation:** OTV strictly terminates Spanning Tree at the internal interface of the edge device. BPDUs are blocked, ensuring an STP loop or flap in Data Center 1 never propagates across the WAN to impact Data Center 2.
  2. **Loop Prevention:** OTV edge devices elect an **Authoritative Edge Device (AED)** per VLAN (even/odd VLAN load balancing). Only the elected AED for a VLAN can forward Layer 2 frames between the site and the overlay.
  3. **Control Plane Learning:** OTV uses internal IS-IS in the background to advertise MAC address reachability via IP multicast/unicast, preventing unknown unicast flooding across the WAN.
* Distractor analysis: Option A is false; OTV never forwards BPDUs. Options C and D fabricate incorrect protocol behaviors.

---

## 5. Recommended Study Resources & Official Documentation

* [Cisco 300-610 DCID Official Exam Blueprint Topics](https://learningnetwork.cisco.com/s/dcid-exam-topics)
* [Cisco Press: Designing Cisco Data Center Infrastructure (DCID 300-610) Official Cert Guide](https://www.ciscopress.com/)
* [300-610 Practice Test - CertsClub](https://www.certsclub.com/cisco/) (Use coupon `club20` for 20% off)
* [Cisco Data Center Spine-and-Leaf Architecture Design Guide](https://www.cisco.com/c/en/us/solutions/data-center/data-center-networking/index.html)
* [Cisco ACI Multi-Pod and Multi-Site Architecture White Papers](https://www.cisco.com/c/en/us/solutions/data-center-virtualization/application-centric-infrastructure/white-paper-c11-739609.html)
* [Cisco MDS 9000 Series Fabric Configuration Guide (Smart Zoning & IVR)](https://www.cisco.com/c/en/us/support/storage-networking/mds-9000-series-multilayer-switches/products-installation-and-configuration-guides-list.html)

---

## 6. SEO Keywords & Search Index Topics

```
300-610, 300-610 exam, 300-610 practice test, 300-610 study guide, cisco 300-610,
dcid, cisco dcid, ccnp data center design, designing cisco data center infrastructure,
certsclub 300-610, spine and leaf oversubscription ratio 480 600 non blocking,
vxlan evpn multi-site border gateway dci, ucs fabric interconnect end-host mode stp,
cisco smart zoning tcam initiator target, buffer to buffer b2b credit extended distance,
aci multi-pod vs multi-site ndo apic cluster, inter-vsan routing ivr cisco mds,
nexus vpc peer-gateway nas arp fix, intersight saas edge ucs c-series management,
otv authoritative edge device aed stp isolation
```

---

## 7. Community Discussions & Contributions

* **Design Discussions & Topology Reviews:** Share leaf-spine designs, ACI Multi-Pod architectures, and SAN zoning strategies in [GitHub Discussions](../../discussions).
* **Issue Submissions:** To report errata or propose new technical questions, open a ticket in [GitHub Issues](../../issues).
* **Design Contributions:** Cisco Validated Design (CVD) adaptations and CML/UCS topology files are welcomed via Pull Requests.

---
*Maintained by the Cisco Certified Curriculum Community. Contributions and pull requests are welcomed.*
