# AVMC | Ransomware Tabletop — Image Evidence

**Appalachian Valley Medical Center**  
*Cybersecurity Incident Response | Ransomware Tabletop | Network Recovery*

---

## Overview

This directory contains screenshots and visual evidence supporting the Appalachian Valley Medical Center (AVMC) ransomware tabletop exercise and subsequent network recovery improvements.

The exercise simulated a ransomware incident affecting a fictional rural healthcare organization. It examined incident escalation, clinical continuity, backup protection, containment decisions, and recovery planning.

## Tabletop Exercise and Evidence

The tabletop followed four escalating scenarios:

1. **Initial Incident:** Unreadable files and a ransom note triggered investigation and incident response.
2. **Incident Escalation:** Simulated ransomware activity spread across hospital departments.
3. **Backup Compromise:** The scenario exposed weaknesses in recovery-network isolation.
4. **Public Disclosure:** The organization faced communication, reporting, and recovery decisions.

Supporting screenshots document network configuration, connectivity testing, ACL enforcement, and recovery isolation.

## Technical Findings

The exercise led to the implementation of **VLAN 90 — BACKUP_RECOVERY** (`10.40.90.0/28`).

The recovery server, `COLD-BACKUP1` (`10.40.90.2`), was placed in a separate network segment.

Extended access control lists were configured to restrict traffic between the recovery network and production systems.

Controlled tests demonstrated that selected traffic permitted before hardening was subsequently denied by the configured ACLs.

## Evidence Limitations

All scenarios and results are from an educational Cisco Packet Tracer simulation.

The screenshots demonstrate selected network configurations and connectivity outcomes. They do not establish real-world ransomware prevention, immutable backups, successful restoration, or production security assurance.

## Professional Skills Demonstrated

- Incident response planning and tabletop analysis
- Network segmentation and recovery isolation
- Extended ACL configuration and validation
- Evidence-based troubleshooting
- Security control testing and documentation
- Risk identification and corrective engineering

## Project Navigation

[Return to AVMC Capstone](../../README.md)

---

**James Taylor Jordon**  
*NET-2650 Capstone | Fall 2026*

*Appalachian Valley Medical Center — Care Close to Home.*
