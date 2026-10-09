[README_previous_full.md](https://github.com/user-attachments/files/33229601/README_previous_full.md)
<p align="center">
  <img src="/projects/avmc-hospital-network-capstone/Week%2008/images/avmc-logo.png"
       alt="Appalachian Valley Medical Center (AVMC) logo"
       width="500">
</p>

<h1 align="center">Appalachian Valley Medical Center</h1>

<p align="center">
  <strong>Cybersecurity Capstone — Healthcare Network Architecture, Security Engineering & Incident Response</strong>
</p>

<p align="center">
  Cisco Packet Tracer • Network Segmentation • Healthcare Cybersecurity • ACL Enforcement • Incident Response • NIST CSF 2.0
</p>

---

# AVMC Cybersecurity Capstone

The **Appalachian Valley Medical Center (AVMC)** project is a fictional rural healthcare network designed and implemented as my cybersecurity capstone.

The project began as a network-planning exercise and evolved over eight weeks into a functioning Cisco Packet Tracer healthcare environment incorporating clinical systems, administrative users, imaging and laboratory workflows, medical IoT, protected servers, IT management, guest wireless, Facilities/Building Management Systems (BMS), physical-security devices, public-facing services, and an isolated recovery environment.

The goal was not simply to make the network communicate.

The goal was to design a network in which systems could communicate **only where their operational purpose justified that access**, test those assumptions, document failures, correct weaknesses, and demonstrate the results.

The final project combines:

- network architecture and implementation;
- healthcare-oriented network segmentation;
- least-privilege access control;
- infrastructure hardening;
- DHCP and DNS services;
- internal and public web services;
- Medical IoT segmentation;
- Facilities/BMS and physical-security segmentation;
- guest wireless isolation;
- security testing and ACL validation;
- ransomware incident response;
- policy development;
- recovery architecture;
- troubleshooting and change documentation;
- NIST Cybersecurity Framework alignment;
- AI-use disclosure and verification; and
- portfolio-quality technical documentation.

---

# Final Network Architecture

<p align="center">
  <img src="/projects/avmc-hospital-network-capstone/Week%2008/images/final-avmc-topology-labeled.png"
       alt="Final labeled AVMC network topology"
       width="100%">
</p>

The final AVMC network uses a **two-tier collapsed-core architecture** centered on a Cisco 3560 multilayer switch.

`CORE-SW1` provides Layer 3 switching, VLAN interfaces, inter-VLAN routing, DHCP relay, and ACL enforcement. Cisco 2960 access switches provide connectivity for clinical, administrative, Medical IoT, guest, Facilities/BMS, and management systems.

The simulated Internet edge includes an AVMC edge router, ISP router, and public-facing test server.

---

# Network Segmentation

AVMC separates systems according to function, trust level, and operational requirements.

| VLAN | Security Zone | Network | Purpose |
|---:|---|---|---|
| 10 | Administration | `10.40.10.0/27` | Registration, billing, and administrative operations |
| 20 | Clinical Care | `10.40.20.0/26` | Nursing, providers, pharmacy, ER, and ICU workflows |
| 30 | Imaging & Laboratory | `10.40.30.0/27` | Radiology, laboratory, X-ray, CT/MRI, and ultrasound workstations |
| 40 | Medical IoT | `10.40.40.0/27` | Medical-device and modality stand-ins |
| 50 | Server Infrastructure | `10.40.50.0/28` | Protected AVMC application and infrastructure services |
| 60 | IT Management | `10.40.60.0/28` | Privileged infrastructure administration |
| 70 | Guest Network | `10.40.70.0/26` | Patient and visitor wireless access |
| 80 | Facilities / BMS | `10.40.80.0/28` | Building management and physical-security systems |
| 90 | Backup / Recovery | `10.40.90.0/28` | Isolated recovery environment |
| 999 | Native / Unused | N/A | Native VLAN and unused-port isolation |

VLANs provide logical separation, while ACLs enforce communication policy between routed security zones.

One of the most important lessons from the project was that:

> **Segmentation is not the same thing as isolation. A VLAN creates a boundary, but security requires policy enforcement across that boundary.**

---

# Healthcare Environment

The AVMC simulation contains representative healthcare systems rather than generic PCs alone.

## Clinical Care

Representative systems include:

- nursing workstations;
- provider workstation;
- pharmacy workstation;
- emergency department workstation;
- ICU workstation; and
- nursing/unit administration.

## Imaging & Laboratory

Representative systems include:

- radiology;
- laboratory;
- X-ray;
- CT/MRI; and
- vascular ultrasound workstations.

Human-operated imaging workstations are intentionally separated from specialized modality/device stand-ins.

## Medical IoT

VLAN 40 contains representative devices including:

- bedside monitor;
- infusion pump;
- ultrasound console;
- ECG/telemetry monitor;
- vital-sign monitor; and
- X-ray console.

These systems are restricted according to least privilege rather than receiving unrestricted access to AVMC internal networks.

## Facilities / BMS

AVMC also models operational technology and physical-security systems, including:

- Facilities workstation;
- Building Management System server;
- HVAC/environmental controls;
- security cameras;
- secured doors; and
- other building/physical-security devices.

These systems occupy a separate trust zone from clinical and administrative systems.

---

# AVMC Internal EHR

AVMC includes a simulated internal clinical application:

**Hostname:** `ehr.avmc.local`  
**Service:** HTTPS  
**Server:** `EHR-SRV1`  
**Address:** `10.40.50.3`

The EHR portal represents a protected internal clinical service.

Access-control testing was used to demonstrate that approved systems could reach required services while unrelated security zones could be denied.

For example, Medical IoT systems were permitted required application access without receiving unrestricted access to the entire server environment.

---

# Public AVMC Website

The environment also includes a simulated public-facing resource:

**Hostname:** `www.avmc.org`

This service is intentionally distinct from the protected internal EHR.

The distinction demonstrates an important architectural boundary:

**Public resources are not equivalent to protected internal clinical services.**

Guest users can reach approved public resources while protected AVMC networks remain restricted.

---

# Security Architecture

The final AVMC implementation includes security controls such as:

- VLAN-based segmentation;
- extended ACLs;
- least-privilege inter-VLAN access;
- Guest network isolation;
- Medical IoT restrictions;
- Facilities/BMS restrictions;
- dedicated IT management segmentation;
- SSH-restricted infrastructure administration;
- VLAN 999 for native/unused ports;
- administrative shutdown of unused switch ports;
- PortFast on appropriate endpoint-facing ports;
- BPDU Guard;
- controlled trunk allowed-VLAN lists;
- centralized DHCP and DNS;
- DHCP relay;
- routing and NAT/PAT;
- security logging concepts;
- ACL hit-counter validation;
- positive and negative connectivity testing; and
- isolated backup/recovery controls.

The project deliberately includes both **successful traffic and intentionally blocked traffic** as evidence.

---

# Ransomware Tabletop and Architecture Change

One of the most significant changes to AVMC occurred during the Week 8 ransomware tabletop exercise.

The tabletop revealed that the original architecture did not explicitly include an isolated cold-storage or immutable recovery tier.

Rather than documenting this only as a recommendation, I modified the actual Packet Tracer architecture.

The final design added:

**VLAN 90 — `BACKUP_RECOVERY`**  
**Network — `10.40.90.0/28`**  
**Gateway — `10.40.90.1`**  
**Recovery Server — `COLD-BACKUP1` (`10.40.90.2`)**

The environment represents an off-site, isolated cold/immutable backup concept within the limitations of Cisco Packet Tracer.

---

# Testing the Recovery Design

The first test produced an important result.

After VLAN 90 was created, `COLD-BACKUP1` could still communicate with production networks.

The VLAN existed.

The addressing was correct.

The recovery server was separated at Layer 2.

**But `CORE-SW1` was still routing between the networks.**

The recovery environment was segmented, but it was not yet sufficiently isolated.

AVMC therefore implemented bidirectional ACL controls around VLAN 90.

## Recovery → Production

`COLD-BACKUP-OUT` restricts traffic originating from the recovery environment.

Testing confirmed that the recovery gateway remained available while unauthorized production access was denied.

ACL counters recorded **12 denied production-network attempts**.

## Production → Recovery

`COLD-BACKUP-IN` restricts routed traffic entering the recovery environment.

A test from `NURSE-PC1` toward `COLD-BACKUP1` resulted in four failed ICMP attempts.

The corresponding ACL recorded:

`4 match(es)`

This provided evidence that the security control—not a broken endpoint or routing failure—was responsible for the denied traffic.

The complete remediation cycle became:

> **Tabletop Finding → Architecture Change → Security Control → Testing → Validation**

---

# Security Validation

Security controls were tested rather than assumed to work because they appeared in the configuration.

Validation included:

### Guest Network

Guest systems retained required public connectivity while protected internal AVMC resources were denied.

### Medical IoT

Medical IoT systems retained approved application access while unrelated internal and public access was restricted.

### Facilities / BMS

Building-management and physical-security systems retained their operational functionality while access to unrelated clinical resources was denied.

### Backup / Recovery

Recovery-to-production and production-to-recovery communication were explicitly tested after hardening.

### ACL Verification

Where appropriate, ACL hit counters were inspected after connectivity tests.

This was important because:

> **A failed ping alone does not prove a security control worked.**

The test methodology attempted to distinguish intentional policy enforcement from addressing, routing, cabling, service, or endpoint failures.

---

# Troubleshooting as Evidence

AVMC was not built by hiding failed configurations.

Troubleshooting became part of the project evidence.

Examples included:

- native VLAN mismatches;
- incorrect VLAN assignments;
- subnet-mask corrections;
- SVI state troubleshooting;
- DHCP/DNS troubleshooting;
- ACL direction and policy corrections;
- expected ARP/MAC learning behavior;
- service-versus-ICMP testing;
- Facilities segmentation testing; and
- recovery-network isolation testing.

The final architecture therefore represents multiple cycles of:

**Configure → Test → Observe → Troubleshoot → Correct → Retest → Document**

---

# Security Policies

Week 8 expanded the technical architecture into formal organizational governance.

AVMC includes three security policies:

- **Acceptable Use Policy**
- **Access Control Policy**
- **Incident Response Policy**

The policies define responsibilities, acceptable behavior, access-control expectations, incident-response procedures, and accountability within the fictional AVMC environment.

The policies were mapped to applicable areas of the **NIST Cybersecurity Framework 2.0**.

See:

[`Week 08/AVMC Policies/`](Week%2008/AVMC%20Policies/)

---

# Incident Response

The AVMC Incident Response Policy was exercised through a ransomware tabletop rather than remaining an untested document.

The scenario required decisions involving:

- workstation isolation;
- server containment;
- evidence preservation;
- log review;
- phishing investigation;
- account compromise;
- lateral movement;
- ransomware propagation;
- data exfiltration;
- legal/privacy coordination;
- law-enforcement involvement;
- executive communication;
- public communication;
- ransom-payment considerations;
- recovery; and
- post-incident improvement.

The resulting After-Action Report documents what worked, what failed, and the improvements identified during the exercise.

The isolated recovery environment was one of those improvements and was subsequently implemented in the network.

---

# Project Evolution

AVMC was developed incrementally rather than created as a finished topology in one session.

| Phase | Major Focus |
|---|---|
| **Week 1** | Initial capstone concept, healthcare use case, project scope, and requirements |
| **Week 2** | Architecture planning, addressing, subnetting, and initial design decisions |
| **Week 3** | Packet Tracer topology development and infrastructure planning |
| **Week 4** | VLANs, trunks, switching, routing, and foundational implementation |
| **Week 5** | Layer 3 architecture, management plane, troubleshooting, and hardening |
| **Week 6** | DHCP, DNS, servers, endpoint populations, and service validation |
| **Week 7** | Security controls, Guest/Medical-IoT/Facilities segmentation, testing, and final architecture development |
| **Week 8** | Security policies, ransomware tabletop, recovery redesign, tool evidence, validation, and final documentation |

Each weekly directory preserves the development history rather than replacing earlier work with only the final result.

---

# Repository Navigation

This repository intentionally preserves the chronological development of the capstone.

### Weekly Project Documentation

- [`Week 01`](Week%2001/)
- [`Week 02`](Week%2002/)
- [`Week 03`](Week%2003/)
- [`Week 04`](Week%2004/)
- [`Week 05`](Week%2005/)
- [`Week 06`](Week%2006/)
- [`Week 07`](Week%2007/)
- [`Week 08`](Week%2008/)

### Final Packet Tracer Build

See the Packet Tracer directory within Week 8 for the final `.pkt` implementation and its dedicated documentation.

### Final Policies

See:

[`Week 08/AVMC Policies`](Week%2008/AVMC%20Policies/)

### Tool Evidence

See the Week 8 Tool Evidence documentation for the final security-validation results.

### Ransomware Tabletop

See the Week 8 ransomware tabletop and After-Action Report for the incident-response exercise and resulting architecture changes.

---

# Skills Demonstrated

This capstone demonstrates practical experience with:

### Networking

- IPv4 addressing and subnetting
- VLAN design
- 802.1Q trunking
- Layer 2 switching
- Layer 3 switching
- SVIs
- inter-VLAN routing
- static and default routing
- DHCP
- DHCP relay
- DNS
- NAT/PAT
- wireless networking

### Network Security

- trust-zone design
- network segmentation
- extended ACLs
- least privilege
- Guest isolation
- Medical IoT segmentation
- Facilities/OT segmentation
- management-plane restrictions
- SSH administration
- switch-port hardening
- native/unused VLAN design
- PortFast
- BPDU Guard
- ACL verification

### Cybersecurity

- incident response
- ransomware response
- evidence preservation
- containment strategy
- recovery planning
- security-policy development
- NIST CSF 2.0 mapping
- security validation
- risk-based architecture improvement
- tabletop exercises
- after-action reporting

### Technical Practice

- Cisco Packet Tracer
- Cisco IOS CLI
- structured troubleshooting
- change control
- checkpointing
- positive/negative testing
- technical writing
- evidence collection
- GitHub documentation
- portfolio development

---

# Production Limitations

AVMC is a **fictional educational simulation**, not a production hospital network.

Cisco Packet Tracer cannot fully reproduce technologies and operational requirements such as:

- enterprise next-generation firewalls;
- EDR/XDR;
- production SIEM/SOC operations;
- enterprise IAM;
- MFA;
- production NAC;
- vulnerability-management platforms;
- true immutable storage;
- physically offline backup media;
- high-availability infrastructure;
- production medical-device protocols;
- DICOM/PACS workflows;
- vendor-specific clinical systems;
- full encryption/key-management infrastructure;
- production disaster-recovery platforms;
- application-aware inspection;
- clinical engineering controls; and
- complete healthcare regulatory and patient-safety processes.

The project therefore distinguishes between **controls actually implemented and validated in Packet Tracer** and controls that would be required in a real healthcare environment.

---

# Responsible AI Use

OpenAI ChatGPT (GPT-5.6 Sol) was used during portions of the capstone for:

- technical discussion;
- troubleshooting assistance;
- drafting support;
- documentation organization;
- review;
- evidence organization; and
- converting technical work into portfolio-ready documentation.

AI-generated recommendations were not treated as authoritative evidence.

Configurations were entered, tested, observed, and validated in Cisco Packet Tracer. Cybersecurity concepts used in final documentation were reviewed against authoritative resources including NIST, CISA, SANS, course materials, and observed lab results.

Detailed attribution and verification documentation is included in Week 8.

---

# Dedication

This project is dedicated to **my wife, the love of my life**.

Her belief, encouragement, patience, and support made this project possible. She believed in me during the moments when I struggled to believe in myself and made sure I had the tools—including the ROG Strix on which much of AVMC was built—to pursue this work at the level I wanted.

AVMC represents weeks of configuration, troubleshooting, redesign, testing, documentation, and persistence.

Her support is part of every one of those accomplishments.

A complete dedication is included with the project documentation.

---

# Author

**James Jordon**  
Cybersecurity Capstone  
NET-2650 — Capstone Planning and Implementation  
Fall 2026

---

## Project Status

**AVMC Packet Tracer Build:** Complete  
**Final Architecture:** Complete  
**Security Validation:** Complete  
**Security Policies:** Complete  
**Ransomware Tabletop:** Complete  
**After-Action Report:** Complete  
**Portfolio Documentation:** Complete  

**Final Packet Tracer Version:** `AVMC_Capstone_James_Jordon_v6.0_Week_8_Final.pkt`

---

<p align="center">
  <strong>Appalachian Valley Medical Center</strong><br>
  <em>Care Close to Home.</em>
</p>

<p align="center">
  Fictional healthcare environment created for cybersecurity education and portfolio demonstration.
</p>
