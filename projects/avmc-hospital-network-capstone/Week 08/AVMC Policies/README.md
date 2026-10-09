[README.md](https://github.com/user-attachments/files/33231000/README.md)
<div align="center">
  
<p align="center">
  <img src="../images/avmc-logo.png"
       alt="Appalachian Valley Medical Center logo"
       width="320">
</p>

# AVMC | Security Policy Library

**Appalachian Valley Medical Center**  
*Healthcare Cybersecurity Governance | Employee Onboarding | Incident Readiness*

![Governance](https://img.shields.io/badge/GOVERNANCE-NIST_CSF_2.0-2563EB?style=flat-square&labelColor=101827)
![Policy Set](https://img.shields.io/badge/POLICIES-AUP_%7C_ACP_%7C_IRP-172B4D?style=flat-square&labelColor=101827)
![Environment](https://img.shields.io/badge/ENVIRONMENT-EDUCATIONAL_SIMULATION-475569?style=flat-square&labelColor=101827)

[AVMC Project Home](../../README.md) | [Professional Portfolio](../../../../README.md)

</div>

## Overview

This folder contains the **approved final policy set** for Appalachian Valley Medical Center (AVMC), a fictional healthcare network developed as a cybersecurity capstone. The policies are written as operational onboarding and governance documents, rather than short classroom summaries. They define expected behavior, access authorization, security responsibilities, and incident-response coordination.

**Version control:** The final, revised policy documents supersede earlier drafts. Older Markdown or PDF exports must not be presented as current unless their contents have been checked against the approved final DOCX policies.

## Policy Index

| Policy | Purpose | NIST CSF 2.0 alignment | Final source |
|---|---|---|---|
| **Acceptable Use Policy (AUP)** | Sets expectations for appropriate use of AVMC systems, accounts, information, and connected devices. | **GOVERN, PROTECT** | [Final AUP (DOCX)](AVMC_Acceptable_Use_Policy_Final_Final_FINAL.docx) |
| **Access Control Policy (ACP)** | Establishes identity, role-based authorization, least privilege, access reviews, and restrictions around protected systems and recovery assets. | **GOVERN, PROTECT** | [Final ACP (DOCX)](AVMC_Access_Control_Policy_Final_Final_FINAL.docx) |
| **Incident Response Policy (IRP)** | Defines incident escalation, containment, evidence handling, coordinated response, recovery, and post-incident improvement. | **GOVERN, DETECT, RESPOND, RECOVER** | [Final IRP (DOCX)](AVMC_Incident_Response_Policy_Final_Final_FINAL.docx) |

*Function mappings summarize policy relevance; consult the full documents for their actual requirements and detailed mappings.*

## Important Final Revisions

Peer review identified a recovery-design and documentation gap: VLAN 90's isolation controls restricted routine connectivity, but the policy set also needed to explain **how authorized backups enter the recovery environment**. The final ACP and IRP address controlled backup transfer, authorization, and recovery responsibilities. A separate backup network is not proof of physically offline or immutable storage; those capabilities remain outside the Packet Tracer simulation.

The final policies should be read together: the AUP defines user responsibilities, the ACP establishes access boundaries, and the IRP governs response when controls fail or an incident occurs.

## Markdown and PDF Editions

The files below may be useful for browser reading and portfolio presentation **only after they are synchronized with the final approved DOCX versions**:

- [AUP Markdown](AVMC_Acceptable_Use_Policy.md)
- [ACP Markdown](AVMC_Access_Control_Policy.md)
- [IRP Markdown](AVMC_Incident_Response_Policy.md)

**Maintenance note:** Replace outdated Markdown content with faithful exports of the final policies before using these links as authoritative policy references. Likewise, regenerate any outdated PDF copies. Do not merge older drafts into the final text.

## Scope and Attribution

AVMC is an **educational simulation**, not a real healthcare provider or a claim of HIPAA certification. Policy drafting and formatting included AI assistance; final requirements, technical claims, and testing evidence remain subject to human review and verification.

---

*Appalachian Valley Medical Center | Care Close to Home.*
