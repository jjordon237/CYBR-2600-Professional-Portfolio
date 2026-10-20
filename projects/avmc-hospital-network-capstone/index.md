---
layout: default
title: AVMC Hospital Network Capstone
---

<div align="center">

<img src="Week%2008/images/avmc-logo.png" alt="Appalachian Valley Medical Center logo" width="390">

<h1>Appalachian Valley Medical Center</h1>
<h3>HEALTHCARE NETWORK SECURITY · CAPSTONE CASE STUDY</h3>
<p><strong>Cisco Packet Tracer · Network Architecture · Segmentation · Incident Response</strong></p>

<p>
<img src="https://img.shields.io/badge/PROJECT-CAPSTONE-15803D?style=flat-square&amp;labelColor=101827" alt="Capstone project">
<img src="https://img.shields.io/badge/NETWORK-10_OPERATIONAL_VLANS-2563EB?style=flat-square&amp;labelColor=101827" alt="Ten operational VLANs">
<img src="https://img.shields.io/badge/VALIDATION-CONNECTIVITY_TESTED-2563EB?style=flat-square&amp;labelColor=101827" alt="Connectivity tested">
<img src="https://img.shields.io/badge/GOVERNANCE-NIST_CSF_2.0-475569?style=flat-square&amp;labelColor=101827" alt="NIST CSF 2.0 governance">
</p>

<p>
<a href="#architecture-at-a-glance">Architecture</a> ·
<a href="#dietary-services-network-expansion">Dietary Services</a> ·
<a href="#security-validation-and-results">Security Evidence</a> ·
<a href="#ransomware-tabletop-and-recovery-redesign">Incident Response</a> ·
<a href="#project-artifacts">Documentation</a> ·
<a href="../../">Portfolio Home</a>
</p>

</div>

---

## Executive Overview

**Appalachian Valley Medical Center (AVMC)** is a fictional rural hospital network that I designed, configured, tested, and documented as an eight-week cybersecurity capstone, with subsequent infrastructure enhancements.

Using Cisco Packet Tracer, I developed a segmented healthcare environment representing clinical care, imaging and laboratory operations, medical IoT, administrative systems, protected services, IT management, guest access, facilities and physical security, backup recovery, and Dietary Services.

**Engineering objective:** Permit network traffic required for healthcare operations while restricting unnecessary communication between zones with different trust and security requirements.

The project progressed through network design, configuration, implementation, connectivity testing, troubleshooting, security-policy development, a ransomware tabletop exercise, and corrective engineering changes.

The environment now includes **10 operational VLANs**, Layer 3 inter-VLAN routing, IEEE 802.1Q trunking, centralized DNS, internal web applications, and simulated healthcare infrastructure.

**This is an educational simulation, not a deployed healthcare system or a compliance certification.**

## Architecture at a Glance

![Labeled AVMC topology](Week%2008/images/final-avmc-topology-labeled.png)

The design uses a **two-tier collapsed-core architecture**. A Cisco 3560 multilayer switch (`CORE-SW1`) provides switched virtual interfaces (SVIs), inter-VLAN routing, and ACL enforcement. Cisco 2960 access switches connect departmental devices. Simulated edge and ISP routers provide an external test path.

| VLAN | Security zone | IPv4 subnet | Primary function |
|---:|---|---|---|
| 10 | Administration | `10.40.10.0/27` | Registration, billing, operations |
| 20 | Clinical | `10.40.20.0/26` | Care-team and clinical workstations |
| 30 | Imaging / Lab | `10.40.30.0/27` | Diagnostic and laboratory workflows |
| 40 | Medical IoT | `10.40.40.0/27` | Representative medical-device endpoints |
| 50 | Servers | `10.40.50.0/28` | Internal application and infrastructure services |
| 60 | IT Management | `10.40.60.0/28` | Restricted administrative access |
| 70 | Guest | `10.40.70.0/26` | Visitor / patient connectivity |
| 80 | Facilities / BMS | `10.40.80.0/28` | Building controls, cameras, physical security |
| 90 | Backup / Recovery | `10.40.90.0/28` | Restricted recovery network |
| **100** | **Dietary Services** | **`10.40.100.0/27`** | **Food services, inventory workstation, and internal dietary web portal** |

**Additional infrastructure control:** VLAN 999 is used as the native VLAN on configured trunks and as an unused-port isolation VLAN. It is not an operational department network.

### Services and controls

- **Network:** 802.1Q trunks, VLANs, SVIs, IPv4 subnetting, DHCP relay, DNS, routing, and NAT/PAT.
- **Access enforcement:** Extended ACLs, guest isolation, Medical IoT and Facilities/BMS restrictions, and recovery isolation.
- **Switch hardening:** Restricted trunk VLAN lists, appropriate PortFast and BPDU Guard, unused-port controls, and management-plane security configuration.
- **Applications:** Internal EHR demonstration at `ehr.avmc.local` (`10.40.50.3`, HTTPS), public website simulation at `www.avmc.org`, and Dietary Services portal at `dietary.avmc.org` (`10.40.100.2`, HTTP).
- **Operational modeling:** Clinical workstations, imaging endpoints, medical IoT stand-ins, building-management devices, physical-security devices, and food-services operations.

## Dietary Services Network Expansion

Following the initial capstone implementation, I expanded AVMC to include a dedicated **Dietary Services VLAN (VLAN 100)**.

The expansion demonstrates how a new hospital department can be integrated into an existing segmented network without redesigning the established collapsed-core infrastructure.

### Network configuration

| Component | Configuration |
|---|---|
| Department VLAN | `100 — DIETARY` |
| IPv4 subnet | `10.40.100.0/27` |
| Subnet mask | `255.255.255.224` |
| Default gateway | `10.40.100.1` |
| Core switch | `CORE-SW1` |
| Access switch | `DIET-SW1` |
| Core trunk interface | `GigabitEthernet0/2` |
| Dietary trunk interface | `GigabitEthernet0/1` |
| Trunk encapsulation | IEEE 802.1Q |
| Allowed trunk VLANs | `100,999` |
| Native VLAN | `999` |
| Central DNS server | `10.40.50.2` |

### Connected departmental devices

| Device | IPv4 address | Switch interface | Purpose |
|---|---|---|---|
| DIET-PC1 | `10.40.100.10` | Fa0/1 | Dietary workstation |
| DIET-SRV1 | `10.40.100.2` | Fa0/2 | Departmental web server |
| DIET-FSTORAGE1 | `10.40.100.11` | Fa0/3 | Food-storage inventory workstation |

The access ports were configured for VLAN 100 with PortFast and BPDU Guard. The dedicated uplink was configured as an 802.1Q trunk with a restricted VLAN allowance.

### Network troubleshooting

During implementation, the core switch rejected trunk mode because trunk encapsulation was set to automatic negotiation.

I corrected the configuration by explicitly enabling IEEE 802.1Q encapsulation on CORE-SW1.

A subsequent native VLAN mismatch between CORE-SW1 and DIET-SW1 caused a Spanning Tree port-consistency issue.

I resolved the mismatch by configuring native VLAN 999 on both trunk interfaces and verified that VLAN 100 entered the forwarding state.

Additional troubleshooting included checking interface status, VLAN membership, Spanning Tree, MAC address learning, ARP resolution, and end-to-end ICMP connectivity.

**Engineering lesson:** Physical connectivity alone does not guarantee successful communication. Layer 2 forwarding, VLAN consistency, IP addressing, and Layer 3 connectivity must all be verified.

### Connectivity validation

Controlled connectivity testing produced the following results:

| Test | Observed result |
|---|---|
| DIET-PC1 → VLAN 100 gateway | Successful, 4/4 ICMP replies |
| CORE-SW1 → DIET-PC1 | Successful, 4/5 ICMP replies during initial test |
| DIET-PC1 → DIET-SRV1 | Successful, 4/4 ICMP replies after troubleshooting |
| DIET-FSTORAGE1 → VLAN 100 gateway | Successful, 4/4 ICMP replies |
| DIET-FSTORAGE1 → DIET-PC1 | Successful, 4/4 ICMP replies |
| DIET-FSTORAGE1 → central DNS server | Successful, 4/4 ICMP replies |
| DIET-PC1 → Dietary HTTP server | Website successfully loaded |
| DIET-PC1 → `dietary.avmc.org` | Hostname successfully resolved and website loaded |

These tests demonstrate local VLAN communication, operational trunking, gateway reachability, inter-VLAN communication, DNS resolution, and HTTP application delivery.

They do not independently demonstrate that all intended Dietary Services ACL restrictions have been enforced.

### Dietary Services Web Portal

**Internal URL:** `http://dietary.avmc.org`

**Server:** `DIET-SRV1 — 10.40.100.2`

I deployed a custom HTML-based Dietary Services portal on the simulated departmental web server, incorporating the Appalachian Valley Medical Center branding and original hospital logo.

The portal includes:

- Meal preparation queue with fictional tray identifiers and dietary instructions.
- Daily menu board.
- Kitchen inventory and replenishment indicators.
- Kitchen equipment register.
- Shift handoff information.
- Training-simulation disclosures and operational reminders.

The website intentionally excludes patient names, diagnoses, and complete EHR records.

Centralized DNS was configured to resolve `dietary.avmc.org` to the departmental server.

The successful browser test demonstrated that the server could deliver the custom HTML application through the configured network.

**Scope limitation:** The portal is a static educational demonstration. It does not provide live patient orders, authenticated access, inventory updates, or real-time equipment telemetry.

### Dietary Services Security Considerations

VLAN 100 provides a separate Layer 2 broadcast domain for Dietary Services.

Additional extended ACL validation remains necessary to confirm least-privilege inter-VLAN access and prevent unnecessary communication with sensitive clinical, administrative, and recovery networks.

Future security testing will include permitted DNS and application access, prohibited inter-department traffic, and guest-to-dietary access restrictions.

## Security Validation and Results

The original capstone documents **both permitted traffic and intentionally denied traffic**. The most instructive finding was that creating VLAN 90 did not, by itself, isolate the recovery server: the multilayer core still routed traffic to production.

| Controlled test | Observed result | Meaning |
|---|---|---|
| Recovery server → production, before hardening | Reachable | Layer 2 separation alone did not prevent Layer 3 access. |
| Recovery server → production, after ACL hardening | Denied; 12 ACL deny matches in recorded test | Selected recovery-originated traffic was blocked by policy. |
| Clinical workstation → recovery server, after hardening | Denied; 4 ACL matches in recorded test | Selected production-originated traffic was blocked by policy. |
| Recovery server → local gateway | Allowed | The recovery subnet retained local gateway reachability. |

**Evidence:** These counters represent matches during controlled ICMP tests, **not** detected ransomware incidents, blocked attackers, or measured prevention rates. ACL direction is relative to the VLAN 90 SVI: `COLD-BACKUP-OUT` was applied **inbound** and `COLD-BACKUP-IN` **outbound**.

<div align="center">
<img src="Week%2008/images/cold-backup-before-hardening-connectivity.png" alt="Recovery network reachability before hardening" width="48%"> <img src="Week%2008/images/cold-backup-outbound-isolation-validated.png" alt="Recovery network isolation after hardening" width="48%">
</div>

[Recovery outbound ACL counters](Week%2008/images/cold-backup-outbound-acl-hit-counters.png) · [Recovery inbound ACL counters](Week%2008/images/cold-backup-inbound-acl-hit-counters.png) · [Clinical-to-recovery denial](Week%2008/images/cold-backup-clinical-access-blocked.png)

**What this proves:** Selected inter-zone restrictions were implemented and validated in the simulation.

**What it does not prove:** Actual immutable storage, offline backups, real-world ransomware resistance, clinical availability, or successful restoration.

## Ransomware Tabletop and Recovery Redesign

A four-inject tabletop escalated from unreadable files and a ransom note, to cross-department spread, compromised backups, and public disclosure.

The exercise required decisions about containment, evidence preservation, clinical continuity, escalation, recovery, and communication.

The backup inject exposed a design weakness. I added `BACKUP_RECOVERY` (VLAN 90), configured `COLD-BACKUP1` (`10.40.90.2`), tested baseline reachability, added bidirectional ACL controls, and retested the boundary.

> **Tabletop finding → Architecture change → Security control → Controlled test → Documented result**

The final simulation models a **closed, restricted recovery network**. A production deployment would still require tested backup ingestion, integrity verification, restore workflows, and independent recovery assurance.

## Governance and Professional Practice

The project includes an **Acceptable Use Policy (AUP)**, **Access Control Policy (ACP)**, and **Incident Response Policy (IRP)** mapped to relevant NIST CSF 2.0 functions.

Peer feedback prompted clarification of backup access, recovery authorization, and policy consistency.

The supporting documentation also records AI-assisted research, drafting, troubleshooting, and human verification.

The project reinforced a repeatable engineering method:

**Configure → Test → Observe → Troubleshoot → Correct → Retest → Document**

Failed tests and control gaps are retained as learning evidence rather than hidden.

## Project Artifacts

| Artifact | Location |
|---|---|
| Week 8 final project and documentation | [Week 08](Week%2008/) |
| Final Packet Tracer implementation | [Week 8 Packet Tracer directory](Week%2008/Packet%20Tracer/) |
| Security policies | [Week 8 AVMC Policies](Week%2008/AVMC%20Policies/) |
| Ransomware tabletop and AAR | [Week 8 Ransomware Tabletop](Week%2008/Ransomware%20Tabletop/) |
| Tool evidence and validation | [Week 8 Tool Evidence](Week%2008/Tool%20Evidence/) |
| Peer feedback and AI attribution | [Week 8 Feedback and AI Notes](Week%2008/Feedback%20and%20AI%20Notes/) |
| Topology and test screenshots | [Week 8 images](Week%2008/images/) |
| Full eight-week project history | [Week 01](Week%2001/) · [Week 02](Week%2002/) · [Week 03](Week%2003/) · [Week 04](Week%2004/) · [Week 05](Week%2005/) · [Week 06](Week%2006/) · [Week 07](Week%2007/) · [Week 08](Week%2008/) |

**Original capstone project file:** `AVMC_Capstone_James_Jordon_v6.0_Week_8_Final.pkt`

**Subsequent expansion:** VLAN 100 Dietary Services, custom departmental web portal, and centralized DNS integration.

## Limitations and Next Engineering Steps

Packet Tracer does not validate enterprise SIEM/EDR, production medical-device protocols, full IAM/MFA, actual immutable/offline backup storage, or high-availability recovery.

The collapsed core is also a central availability dependency.

Additional work would require production-grade controls and validated restore procedures.

**Planned enhancements:**

- Complete and validate Dietary Services extended ACL policies.
- Further develop wireless vending and kitchen IoT integrations.
- Evaluate a dedicated IoT services platform.
- Expand monitoring and infrastructure documentation.
- Perform additional application and security-boundary tests.

**Infrastructure update:** A working print-server enhancement was reported after the final v6.0 evidence package. Further departmental printing restrictions, service validation, and documentation are planned separately; they are not represented as completed in the original v6.0 validation results.

## Responsible AI Use

Generative AI assisted with technical explanations, troubleshooting, document organization, and editorial review.

I made design decisions, entered configurations, conducted the Packet Tracer tests, and evaluated the observed results.

AI outputs were not treated as independent evidence; the supporting Week 8 records describe attribution and verification.

## Dedication

*Dedicated to my wife, whose encouragement, patience, and support made it possible for me to pursue this project. The full dedication is preserved in the capstone documentation.*

---

<div align="center">

**James Taylor Jordon** · NET-2650 Capstone · Fall 2026  
*Appalachian Valley Medical Center — Care Close to Home.*

[Return to Professional Portfolio](../../)

</div>
