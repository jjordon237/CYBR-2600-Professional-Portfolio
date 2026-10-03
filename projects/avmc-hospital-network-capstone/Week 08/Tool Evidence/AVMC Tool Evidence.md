# AVMC Security Tool Evidence and Validation Report

![AVMC Logo](../images/avmc-logo.png)

**Appalachian Valley Medical Center**  
**Cybersecurity Capstone – Week 8**  
**Security Validation Tool:** Cisco Packet Tracer  
**Test Type:** Ping and Access Control List (ACL) Validation  
**Environment:** Fictional healthcare network simulation

---

## 1. Purpose

The purpose of this validation was to determine whether the security controls implemented in the Appalachian Valley Medical Center (AVMC) network successfully enforce network segmentation and least-privilege access.

Cisco Packet Tracer was used to perform connectivity tests and inspect ACL match counters. Particular attention was given to the new recovery environment created following the AVMC ransomware tabletop exercise.

The tabletop identified a significant weakness in the original design: although AVMC had network services and recovery planning, the architecture did not explicitly include an isolated cold-storage or immutable backup tier. AVMC therefore added VLAN 90, `BACKUP_RECOVERY`, and `COLD-BACKUP1` as a simulation of an isolated recovery environment.

---

## 2. Recovery Environment

The recovery environment was configured as:

| Component | Configuration |
|---|---|
| VLAN | VLAN 90 – `BACKUP_RECOVERY` |
| Network | `10.40.90.0/28` |
| Gateway | `10.40.90.1` |
| Recovery Server | `COLD-BACKUP1` |
| Server Address | `10.40.90.2/28` |
| Purpose | Isolated cold/immutable backup simulation |

Packet Tracer does not simulate a truly offline backup repository, immutable storage platform, or physically disconnected media. VLAN 90 and restrictive ACLs therefore represent the logical isolation that would surround a protected recovery environment in a more complete implementation.

---

## 3. Baseline Test – Before ACL Hardening

After VLAN 90 and `COLD-BACKUP1` were created, connectivity was tested before recovery-specific ACLs were applied.

`COLD-BACKUP1` successfully reached:

- `10.40.90.1` – VLAN 90 gateway
- `10.40.50.2` – AVMC production DNS/server resource
- `10.40.20.1` – Clinical VLAN gateway
- `10.40.80.1` – Facilities/BMS VLAN gateway

![Cold backup connectivity before hardening](../images/cold-backup-before-hardening-connectivity.png)

### Interpretation

The test demonstrated an important distinction between **segmentation and isolation**.

Placing the recovery server in a separate VLAN created a distinct Layer 2 network, but CORE-SW1 was performing Layer 3 routing between AVMC VLANs. Therefore, VLAN separation alone did not prevent the recovery environment from communicating with production networks.

If ransomware or another attacker compromised a system with unrestricted routed access to the recovery environment, the protected backup tier could potentially become another reachable target.

Additional access-control enforcement was therefore required.

---

## 4. Recovery-to-Production ACL

AVMC created the extended ACL `COLD-BACKUP-OUT` and applied it inbound to the VLAN 90 SVI.

The ACL allowed limited gateway testing while denying routed access from the recovery network to AVMC production networks and other destinations.

After the ACL was applied, `COLD-BACKUP1` was tested again.

The recovery gateway remained reachable, while attempts to reach production resources were denied.

![Cold backup outbound isolation validation](../images/cold-backup-outbound-isolation-validated.png)

### ACL Counter Validation

AVMC then inspected the ACL using:

```text
show access-lists COLD-BACKUP-OUT
