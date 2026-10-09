[README.md](https://github.com/user-attachments/files/33229746/README.md)
<div align="center">

<img src="Week%2008/images/avmc-logo.png" alt="Appalachian Valley Medical Center logo" width="390">

# Appalachian Valley Medical Center

### HEALTHCARE NETWORK SECURITY · CAPSTONE CASE STUDY

**Cisco Packet Tracer · Network Architecture · Segmentation · Incident Response**

![Status](https://img.shields.io/badge/PROJECT-COMPLETED-15803D?style=flat-square&labelColor=101827)
![Network](https://img.shields.io/badge/NETWORK-9_OPERATIONAL_VLANS-2563EB?style=flat-square&labelColor=101827)
![Security](https://img.shields.io/badge/VALIDATION-ACL_TESTING-2563EB?style=flat-square&labelColor=101827)
![Framework](https://img.shields.io/badge/GOVERNANCE-NIST_CSF_2.0-475569?style=flat-square&labelColor=101827)

[**Architecture**](#architecture-at-a-glance) · [**Security Evidence**](#security-validation-and-results) · [**Incident Response**](#ransomware-tabletop-and-recovery-redesign) · [**Documentation**](#project-artifacts) · [**Portfolio Home**](../../)

</div>

---

## Executive Overview

**Appalachian Valley Medical Center (AVMC)** is a fictional rural hospital network that I designed, configured, tested, and documented as an eight-week cybersecurity capstone. I used Cisco Packet Tracer to build a segmented environment representing clinical care, imaging and laboratory operations, medical IoT, administrative systems, protected services, IT management, guest access, facilities and physical security, and a recovery tier.

**Engineering objective:** Permit the network traffic needed for healthcare operations while restricting unnecessary communication between zones with different trust and security requirements.

The project progressed through design, configuration, testing, troubleshooting, security-policy development, a ransomware tabletop, and corrective engineering changes. **It is an educational simulation, not a deployed healthcare system or a compliance certification.**

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

**Additional infrastructure control:** VLAN 999 is used for native/unused-port isolation; it is not a tenth operational department network.

### Services and controls

- **Network:** 802.1Q trunks, VLANs, SVIs, IPv4 subnetting, DHCP relay, DNS, routing, and NAT/PAT.
- **Access enforcement:** Extended ACLs, guest isolation, Medical IoT and Facilities/BMS restrictions, and management-plane controls.
- **Switch hardening:** Restricted trunk VLAN lists, unused-port shutdown, appropriate PortFast and BPDU Guard, and SSH-oriented management.
- **Applications:** Internal EHR demonstration at `ehr.avmc.local` (`10.40.50.3`, HTTPS) and a separate public website simulation at `www.avmc.org`.
- **Operational modeling:** Clinical workstations, imaging endpoints, medical IoT stand-ins, building-management devices, and physical-security devices.

## Security Validation and Results

The project documents **both permitted traffic and intentionally denied traffic**. The most instructive finding was that creating VLAN 90 did not, by itself, isolate the recovery server: the multilayer core still routed traffic to production.

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

**What this proves:** Selected inter-zone restrictions were implemented and validated in the simulation. **What it does not prove:** Actual immutable storage, offline backups, real-world ransomware resistance, clinical availability, or successful restoration.

## Ransomware Tabletop and Recovery Redesign

A four-inject tabletop escalated from unreadable files and a ransom note, to cross-department spread, compromised backups, and public disclosure. The exercise required decisions about containment, evidence preservation, clinical continuity, escalation, recovery, and communication.

The backup inject exposed a design weakness. I added `BACKUP_RECOVERY` (VLAN 90), configured `COLD-BACKUP1` (`10.40.90.2`), tested baseline reachability, added bidirectional ACL controls, and retested the boundary.

> **Tabletop finding → Architecture change → Security control → Controlled test → Documented result**

The final simulation models a **closed, restricted recovery network**. A production deployment would still require tested backup ingestion, integrity verification, restore workflows, and independent recovery assurance.

## Governance and Professional Practice

The project includes an **Acceptable Use Policy (AUP)**, **Access Control Policy (ACP)**, and **Incident Response Policy (IRP)** mapped to relevant NIST CSF 2.0 functions. Peer feedback prompted clarification of backup access, recovery authorization, and policy consistency. The supporting documentation also records AI-assisted research, drafting, troubleshooting, and human verification.

The project reinforced a repeatable engineering method: **configure → test → observe → troubleshoot → correct → retest → document**. Failed tests and control gaps are retained as learning evidence rather than hidden.

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

**Project file:** `AVMC_Capstone_James_Jordon_v6.0_Week_8_Final.pkt` (see Week 8 Packet Tracer directory).

## Limitations and Next Engineering Steps

Packet Tracer does not validate enterprise SIEM/EDR, production medical-device protocols, full IAM/MFA, actual immutable/offline backup storage, or high-availability recovery. The collapsed core is also a central availability dependency. Additional work would require production-grade controls and validated restore procedures.

**Infrastructure update:** A working print-server enhancement was reported after the final v6.0 evidence package. Further departmental printing restrictions, service validation, and documentation are planned separately; they are **not represented as completed in the v6.0 validation results**.

## Responsible AI Use

Generative AI assisted with technical explanations, troubleshooting, document organization, and editorial review. I made design decisions, entered configurations, conducted the Packet Tracer tests, and evaluated the observed results. AI outputs were not treated as independent evidence; the supporting Week 8 records describe attribution and verification.

## Dedication

*Dedicated to my wife, whose encouragement, patience, and support made it possible for me to pursue this project. The full dedication is preserved in the capstone documentation.*

---

<div align="center">

**James Taylor Jordon** · NET-2650 Capstone · Fall 2026  
*Appalachian Valley Medical Center — Care Close to Home.*

[Return to Professional Portfolio](../../)

</div>
