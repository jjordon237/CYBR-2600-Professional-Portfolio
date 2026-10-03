<p align="center">
  <img src="/projects/avmc-hospital-network-capstone/Week%2008/images/avmc-logo.png" alt="Appalachian Valley Medical Center (AVMC) logo" width="400">
</p>

# AVMC Packet Tracer Network Simulation

This folder contains the final Cisco Packet Tracer implementation of the **Appalachian Valley Medical Center (AVMC)** cybersecurity capstone.

AVMC is a fictional healthcare environment developed to demonstrate network architecture, segmentation, access control, clinical and operational technology integration, security testing, incident-response planning, and recovery design.

The final Packet Tracer environment represents the culmination of the AVMC network build and the security improvements implemented during Week 8.

---

## Final Packet Tracer File

**File:** `AVMC_Capstone_James_Jordon_v6.0_Week_8_Final.pkt`

**Version:** 6.0 – Week 8 Final

The final topology includes:

- Layer 3 core switching and inter-VLAN routing
- 802.1Q trunking
- DHCP and DHCP relay
- Internal DNS
- Internal AVMC EHR service
- Simulated public AVMC website
- Guest wireless access
- Medical IoT devices
- Facilities and Building Management Systems (BMS)
- Physical-security devices
- ACL-based segmentation
- IT management separation
- Edge routing
- Security logging infrastructure
- Isolated backup/recovery environment

---

## Network Segmentation

The AVMC environment separates systems according to operational purpose and trust level.

| VLAN | Name / Function | Network |
|---|---|---|
| 10 | Administration | `10.40.10.0/27` |
| 20 | Clinical Care | `10.40.20.0/26` |
| 30 | Imaging & Laboratory | `10.40.30.0/27` |
| 40 | Medical IoT | `10.40.40.0/27` |
| 50 | Server Infrastructure | `10.40.50.0/28` |
| 60 | IT Management | `10.40.60.0/28` |
| 70 | Guest Network | `10.40.70.0/26` |
| 80 | Facilities / BMS | `10.40.80.0/28` |
| 90 | Backup / Recovery | `10.40.90.0/28` |
| 999 | Native / Unused | Infrastructure use |

VLAN separation is supplemented by access control lists because VLAN membership alone does not prevent routed communication between trust zones.

---

## AVMC Internal EHR

The simulated internal clinical portal is hosted by:

**Server:** `EHR-SRV1`  
**Address:** `10.40.50.3`  
**Hostname:** `ehr.avmc.local`  
**Service:** HTTPS

The EHR service represents a protected internal clinical application.

Access is restricted according to network function. For example, authorized clinical systems can access the service, while Guest and Facilities/BMS networks are prevented from reaching protected clinical resources.

Medical IoT access is restricted at the service level rather than receiving unrestricted access to the server environment.

---

## Public AVMC Website

The simulation also contains a separate public-facing AVMC website:

**Hostname:** `www.avmc.org`

This resource represents services intended to be accessible outside the protected AVMC clinical environment.

Separating the public website from `ehr.avmc.local` demonstrates the distinction between public-facing resources and protected internal applications.

---

## Security Controls

The final Packet Tracer implementation uses multiple security controls, including:

- VLAN-based network segmentation
- Extended ACLs
- Guest-network isolation
- Medical IoT least-privilege restrictions
- Facilities/BMS isolation
- IT management separation
- PortFast on appropriate access ports
- BPDU Guard
- Disabled and isolated unused switch ports
- Dedicated native/unused VLAN 999
- Controlled inter-VLAN routing
- ACL hit-counter verification
- Positive and negative connectivity testing
- Separate recovery-network controls

Security controls were tested rather than assumed to function based solely on configuration.

---

## Guest Network

VLAN 70 represents patient and visitor wireless access.

The final Guest policy permits required network services and approved public access while denying access to protected AVMC internal resources.

Testing confirmed that guest devices could retain intended public connectivity without receiving unrestricted access to the hospital network.

---

## Medical IoT

VLAN 40 contains representative medical and clinical devices.

The Medical IoT environment is intentionally separated from ordinary clinical workstations and other AVMC networks.

ACLs restrict these systems to required services, including approved EHR communication, while preventing unnecessary internal and external connectivity.

This models the principle of **least privilege** for specialized healthcare devices.

---

## Facilities / BMS

VLAN 80 represents AVMC building-management and physical-security systems.

Representative devices include:

- HVAC/environmental controls
- security cameras
- secured doors
- building-management services
- Facilities workstation

Facilities/BMS systems retain access required for their operational functions while being restricted from protected clinical resources and unnecessary public-network access.

This separates operational technology and physical-security systems from the clinical environment.

---

## Backup and Recovery Environment

During the Week 8 ransomware tabletop exercise, the original architecture was found to lack an explicitly isolated cold-storage or immutable recovery tier.

The network design was therefore modified to add:

**VLAN:** 90 – `BACKUP_RECOVERY`  
**Network:** `10.40.90.0/28`  
**Gateway:** `10.40.90.1`  
**Recovery Server:** `COLD-BACKUP1`  
**Server Address:** `10.40.90.2`

The topology identifies this as the:

> **OFF-SITE RECOVERY ENVIRONMENT**

This represents an isolated cold/immutable backup tier for purposes of the simulation.

---

## Ransomware Tabletop Remediation

The recovery environment was not added merely for presentation purposes.

It was created as a direct corrective action resulting from the AVMC ransomware tabletop.

Initial testing after VLAN 90 was created demonstrated that `COLD-BACKUP1` could still communicate with production networks because the Layer 3 core routed traffic between VLANs.

This demonstrated an important security lesson:

> **VLAN separation alone does not guarantee security isolation.**

AVMC subsequently implemented bidirectional ACL controls around the recovery environment.

Testing then confirmed:

- `COLD-BACKUP1` retained access to its recovery gateway
- recovery-to-production traffic was denied
- production-to-recovery traffic was denied
- Clinical systems could not reach `COLD-BACKUP1`
- ACL match counters confirmed that the security rules were actively denying the test traffic

This created a complete remediation cycle:

**Tabletop Finding → Architecture Change → Security Control → Testing → Validation**

---

## Validation Approach

The AVMC environment was tested using both expected-success and expected-failure conditions.

Examples included:

- authorized EHR access
- unauthorized EHR access
- Guest-to-internal restrictions
- Guest-to-public access
- Medical IoT approved service access
- Medical IoT unauthorized access
- Facilities/BMS operational connectivity
- Facilities-to-clinical restrictions
- recovery-to-production restrictions
- production-to-recovery restrictions
- ACL hit-counter verification

A failed ping was not automatically considered proof of successful security enforcement.

Where applicable, ACL counters and known-good baseline connectivity were used to distinguish an intentional security denial from a routing, addressing, cabling, or device failure.

---

## Final Architecture

The final topology is documented with labels identifying the major AVMC security zones and services.

![Final AVMC Network Topology](/projects/avmc-hospital-network-capstone/Week%2008/images/final-avmc-topology-labeled.png)

Detailed architecture views are also available in the project `images` directory.

---

## Simulation Limitations

Cisco Packet Tracer is an educational network simulator and does not reproduce every technology required in a production healthcare environment.

Examples of controls that would require additional production technologies include:

- true immutable backup storage
- physically offline backup media
- enterprise next-generation firewalls
- endpoint detection and response
- SIEM/SOC monitoring
- production identity and access management
- multi-factor authentication
- enterprise vulnerability management
- full application-layer inspection
- high availability and redundant infrastructure
- production medical-device security controls
- comprehensive encryption and key management

`COLD-BACKUP1`, for example, represents the **security concept** of an isolated recovery tier. It should not be interpreted as a complete implementation of physically offline or immutable enterprise backup infrastructure.

---

## Skills Demonstrated

The final Packet Tracer environment demonstrates practical experience with:

- IPv4 subnetting
- VLAN design
- 802.1Q trunking
- Layer 3 switching
- SVIs
- inter-VLAN routing
- DHCP
- DHCP relay
- DNS
- HTTP/HTTPS services
- ACL design
- least-privilege network access
- network segmentation
- guest wireless design
- Medical IoT segmentation
- Facilities/OT segmentation
- switch-port hardening
- troubleshooting
- security testing
- ACL verification
- incident-response-driven remediation
- technical documentation

---

## Educational Use

This project represents a **fictional healthcare organization and training environment**.

It is not a production hospital network design and contains no real AVMC patient information, protected health information, or production credentials.

The environment was created for cybersecurity education, technical experimentation, and portfolio demonstration.

---

## AI Assistance and Attribution

OpenAI ChatGPT (GPT-5.6 Sol) was used during portions of the project for technical discussion, drafting assistance, documentation organization, troubleshooting discussion, and review.

AI-generated recommendations were not treated as authoritative technical evidence.

Network configurations and security controls were entered, tested, observed, and validated within Cisco Packet Tracer. Cybersecurity concepts used in final project documentation were reviewed against authoritative resources including NIST, CISA, and SANS materials.

Detailed disclosure is available in:

**`AVMC AI Use Attribution and Verification Notes.md`**

---

## Author

**James Jordon**  
Cybersecurity Capstone  
Fall 2026

---

*Appalachian Valley Medical Center | Information Technology & Security*  
*Fictional healthcare environment created for educational purposes.*
