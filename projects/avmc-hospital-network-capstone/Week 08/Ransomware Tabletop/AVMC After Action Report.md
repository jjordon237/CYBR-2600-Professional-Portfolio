[AVMC Ransomware Tabletop After Action Report.md](https://github.com/user-attachments/files/32989668/AVMC.Ransomware.Tabletop.After.Action.Report.md)
<p align="center">
  <img src="images/avmc-logo.png" alt="Appalachian Valley Medical Center (AVMC) logo" width="400">
</p>
# Ransomware Tabletop Exercise

## After-Action Report

AVMC Information Technology & Security

  Organization    Appalachian Valley Medical Center
  --------------- --------------------------------------
  Exercise Type   Incident Response Tabletop
  Scenario        Ransomware and Data Extortion
  Framework       NIST CSF 2.0 / NIST SP 800-61 Rev. 3
  Status          Final Exercise Record

# 1. Exercise Purpose

The purpose of this tabletop exercise was to evaluate Appalachian Valley
Medical Center's ability to identify, contain, investigate, communicate,
and recover from a ransomware incident using the AVMC network
architecture and Incident Response Policy.

The exercise tested AVMC's technical segmentation, incident-response
decision making, evidence-preservation procedures, escalation process,
communications strategy, and recovery planning.

The scenario progressed through four injects of increasing severity: an
initial ransomware report, spread across multiple departments,
compromise of backup infrastructure, and confirmed public disclosure of
organizational records.

NIST SP 800-61 Rev. 3 treats incident response as an integrated
component of cybersecurity risk management and emphasizes continuous
improvement based on lessons identified during incidents and exercises.

# 2. Scenario Timeline and Decisions

## Inject 1 --- Monday, 7:40 AM

### Scenario

An AVMC employee reported that files on a shared drive could no longer
be opened. Affected filenames ended in .locked, and a text file
containing a ransom demand appeared on the employee's desktop.

### Initial Assessment

AVMC treated the report as a suspected ransomware incident. At this
stage, the scope of the incident was unknown. There was no evidence yet
that the ransomware affected additional departments, that information
had been exfiltrated, or that backup systems had been compromised.

### Notification

The employee would immediately notify AVMC IT/Security. AVMC IT/Security
would designate or notify the Incident Response Lead and inform the
manager or system owner responsible for the affected shared resource.
Leadership would receive an initial notification that a suspected
ransomware incident affecting an organizational resource was under
investigation.

### Containment

The affected workstation would immediately be disconnected from network
access while remaining powered on when practical to preserve volatile
evidence. The affected shared-drive server or resource would also be
temporarily isolated through AVMC's switching and network
infrastructure. AVMC would use targeted containment rather than
immediately disconnecting entire clinical VLANs or shutting down the
hospital network. This decision was made to contain the suspected threat
while avoiding unnecessary interruption of patient-care systems.

### Evidence Preservation

-   the ransom note;
-   examples of .locked files;
-   timestamps;
-   workstation IP and MAC information;
-   server access logs;
-   authentication records;
-   file-access and transfer logs;
-   network and security logs;
-   available ACL/SYSLOG information;
-   screenshots;
-   relevant email information;
-   available volatile or forensic evidence. \### Additional
    Investigation

The original workstation would be investigated to determine whether it
represented the initial point of compromise. AVMC would search other
systems for similar file extensions, ransom messages, abnormal
authentication activity, or related indicators. The original tabletop
discussion initially interpreted the ransom note as potentially
physical. This was corrected when the scenario was reviewed more
closely: the ransom note was a text file on the desktop, making physical
attribution through security-camera footage unnecessary unless later
evidence indicated unauthorized physical access.

### Recovery Protection

Backup infrastructure would be protected from affected systems
immediately. AVMC would not begin restoration at this stage because the
scope of compromise and integrity of recovery assets had not yet been
established.

### Communications

Employees would receive limited operational guidance instructing them
not to access the affected resource, not to open unexpected attachments,
not to perform their own remediation, and to immediately report similar
symptoms. No public statement would be issued at this stage because AVMC
had no verified evidence of data theft or broad organizational
compromise.

### Applicable Policies

-   AVMC Incident Response Policy
-   AVMC Access Control Policy
-   AVMC Acceptable Use Policy \# 3. Inject 2 --- Monday, 8:15 AM

### Scenario

Two additional departments reported similar ransomware symptoms. Help
desk personnel determined that a staff member had opened an email
attachment labeled "Invoice" on Friday afternoon.

### Revised Assessment

The incident was no longer considered potentially isolated. AVMC now had
evidence of a multi-department ransomware event and a probable
phishing-based initial-access vector. The Friday attachment became the
leading hypothesis for the initial compromise, although AVMC would
continue investigating before treating the hypothesis as confirmed.

### Escalation and Notification

-   Incident Response Lead;
-   AVMC IT/Security;
-   CISO/CIO or equivalent technology leadership;
-   executive leadership;
-   affected department and clinical leadership;
-   Privacy/Compliance;
-   Legal;
-   Communications/Public Relations;
-   backup/recovery personnel. \### Containment

All confirmed infected endpoints and affected server resources would be
isolated. AVMC would use network segmentation, VLAN boundaries, switch
controls, ACLs, account restrictions, and other available mechanisms to
prevent lateral movement. However, unaffected clinical infrastructure
would not be indiscriminately disconnected. Systems would instead be
classified according to evidence and operational risk.

### Investigation

-   sender information;

-   headers;

-   attachment;

-   timestamps;

-   recipient information;

-   account activity following execution;

-   DNS/network communications;

-   subsequent authentication events. \### Credential Review

-   abnormal login activity;

-   unusual authentication locations or times;

-   lateral authentication;

-   privileged-account activity;

-   service-account compromise;

-   use of the affected employee's credentials on additional systems.
    \### Scope Determination

AVMC would separately determine impacts to Availability --- what
information or systems were encrypted or unavailable? Integrity --- what
information was modified, damaged, or destroyed? Confidentiality ---
what information was accessed or removed? This distinction prevents AVMC
from assuming that encrypted information was necessarily stolen or that
inaccessible information was necessarily corrupted.

### Communications

Staff would receive an organization-wide security advisory explaining
that AVMC was responding to a cybersecurity incident affecting multiple
departments. Employees would be instructed to avoid unexpected
attachments, affected shared resources, and independent remediation.
Leadership would be informed that multiple departments were affected,
phishing was the suspected initial vector, containment was underway,
data-exposure scope remained unknown, and recovery assets were being
protected. AVMC would not yet claim that patient information had been
stolen because exfiltration had not been established.

# 4. Inject 3 --- Monday, 9:30 AM

### Scenario

The AVMC backup server was discovered to be encrypted. A reporter
contacted AVMC asking whether customer data had been stolen.

### Escalation

Compromise of the backup infrastructure was treated as a significant
escalation because it threatened AVMC's ability to recover without
paying the attacker. The Incident Response Lead would immediately notify
executive leadership, IT/Security leadership, Legal, Privacy/Compliance,
Communications, clinical leadership, and recovery personnel.

### Recovery Decision

During the tabletop, AVMC identified a significant weakness in the
original architecture: the design did not explicitly include an offline
or immutable backup tier. This meant that compromise of the
network-accessible backup environment could become a single point of
failure for ransomware recovery. AVMC therefore determined that its
improved architecture should include an isolated cold-storage or
immutable recovery copy.

### Cold-Storage Recovery

-   establish reasonable containment;
-   investigate persistence;
-   secure compromised credentials;
-   determine whether the backup predates the compromise;
-   validate the backup's integrity;
-   establish a sufficiently trusted recovery environment. \### Reporter
    Inquiry

The Incident Response Lead would not independently speak on behalf of
AVMC. The inquiry would be escalated to authorized leadership,
Legal/Privacy, and Communications personnel. AVMC would provide a
limited factual statement: "Appalachian Valley Medical Center is
responding to a cybersecurity incident affecting certain information
systems. Our incident-response procedures have been activated, and we
are working with cybersecurity professionals and appropriate
law-enforcement authorities to investigate the incident and safely
restore affected services. Our investigation into the nature and scope
of the incident is ongoing. If we determine that individuals'
information was affected, AVMC will provide appropriate notifications in
accordance with applicable requirements." AVMC would neither claim that
data had been stolen nor claim that data had not been stolen because
neither conclusion had yet been established.

# 5. Inject 4 --- Day 2

### Scenario

The attackers publicly posted a sample of AVMC records and increased the
ransom demand.

### Revised Assessment

This inject transformed suspected data exfiltration into confirmed
unauthorized disclosure of AVMC information. The incident now affected
Availability through ransomware encryption, Confidentiality through
confirmed data exfiltration/publication, and potentially Integrity,
pending investigation of whether records had been altered.

### Ransom Decision

AVMC would recommend against paying the ransom and would not authorize
payment merely because the attackers increased pressure. The publication
of records demonstrated that the attackers already possessed
organizational information, and payment could not undo the disclosure or
guarantee that additional copies would be destroyed. Any final
organizational decision concerning ransom payment would require
appropriate executive, legal, insurance, financial, and law-enforcement
consultation rather than being made by an individual technical
responder.

### Privacy and Legal Response

-   what information was disclosed;

-   whether it included PHI/ePHI or other regulated information;

-   which individuals were affected;

-   the likely scope of exposure;

-   applicable notification requirements;

-   contractual or regulatory obligations. \### Technical Response

-   containment of confirmed compromised systems;

-   investigation of suspected systems;

-   credential resets;

-   malicious-indicator blocking;

-   identification of attacker persistence;

-   analysis of lateral movement;

-   investigation of the exfiltration path;

-   validation of unaffected systems;

-   controlled recovery from trusted backup assets. \### System
    Classification

Confirmed compromised: immediately isolated and preserved for
investigation. Suspected/exposed: connectivity restricted while
investigated and validated. No current indicators: required services
maintained with heightened monitoring and unnecessary communication
restricted. This approach allows AVMC to contain the attack while
protecting essential patient-care operations.

# 6. What Worked

### Network Segmentation

AVMC's separation of Clinical, Server, MED-IOT, Guest, Facilities/BMS,
and management functions provides meaningful containment boundaries. The
ACL testing performed before the tabletop demonstrated that AVMC can
restrict lateral communication while preserving authorized business
services.

### Least-Privilege Controls

MED-IOT devices were already limited to required services such as EHR
HTTPS rather than unrestricted internal or Internet access.
Facilities/BMS systems were similarly restricted from clinical and
public networks. These controls reduce potential ransomware lateral
movement.

### Targeted Containment

AVMC's response did not immediately shut down the entire hospital
network. Containment decisions considered patient safety and service
availability while isolating confirmed or suspected compromised systems.

### Evidence Preservation

The Incident Response Policy provided clear requirements for preserving
logs, ransom artifacts, authentication records, network evidence,
affected files, and investigative actions before destructive
remediation.

### Communications Discipline

The tabletop consistently separated confirmed facts, suspected facts,
and unknown information. External communication was reserved for
authorized leadership/communications personnel rather than technical
responders making unsupported statements.

# 7. What Failed or Required Improvement

The exercise identified several weaknesses. The most significant was the
absence of an explicitly isolated backup tier in the original AVMC
architecture.

The exercise also demonstrated that responders initially had to reason
through containment scope, escalation requirements, and communications
responsibilities rather than following a detailed ransomware-specific
playbook.

The phishing-based initial-access scenario further demonstrated that
technical segmentation cannot eliminate risks created by malicious email
attachments and compromised user credentials.

Finally, compromise of the backup server showed that backup systems
require stronger separation from ordinary production credentials and
network access.

# 8. Corrective Actions and Improvements

## Improvement 1 --- Offline/Immutable Backup Tier

AVMC will add an isolated cold-storage or immutable backup tier to the
architecture. The recovery copy should not remain ordinarily writable or
continuously accessible from production systems. Backup integrity and
restoration procedures shall be tested regularly.

Reason: Inject 3 demonstrated that compromise of the online backup
server could otherwise eliminate AVMC's primary recovery path.

Network impact: Addition of an isolated COLD-BACKUP1 or equivalent
recovery environment.

Policy impact: Incident Response and backup/recovery procedures will
explicitly require offline/immutable recovery assets.

## Improvement 2 --- Formal Ransomware Containment Playbook

AVMC will develop a ransomware-specific containment playbook defining
criteria for individual endpoint isolation, server isolation, account
disabling, VLAN isolation, ACL modification, backup-network protection,
and clinical-system escalation.

Reason: Responders should not need to improvise whether one endpoint,
one server, or an entire clinical segment should be disconnected during
an active incident.

Network impact: Existing segmentation and ACL capabilities become
predefined containment tools.

Policy impact: Supplements the Incident Response Policy with actionable
technical procedures.

## Improvement 3 --- Breach Communications and Escalation Matrix

AVMC will establish a formal incident-notification matrix defining when
and how to involve the Incident Response Lead, CISO/CIO, executive
leadership, clinical leadership, Privacy/Compliance, Legal,
Communications, law enforcement, cyber-insurance providers, affected
individuals, regulators, and media when applicable.

Reason: Injects 3 and 4 demonstrated that communications requirements
rapidly become complex when recovery failure, public inquiries, and
confirmed data disclosure occur.

Policy impact: Clarifies authority and prevents inconsistent or
speculative communications.

## Improvement 4 --- Enhanced Phishing Controls and Workforce Training

AVMC will strengthen technical and human defenses against phishing
through recurring phishing-awareness training, simulated phishing
exercises, stronger email filtering where available, attachment and link
protections, clear suspicious-email reporting procedures, and rapid
investigation of reported messages.

Reason: The probable initial-access vector was an Invoice attachment
opened on Friday, while ransomware symptoms were not reported until
Monday morning.

Policy impact: Reinforces requirements already established in the AVMC
Acceptable Use Policy.

## Improvement 5 --- Separate and Harden Backup Credentials and Infrastructure

AVMC will further isolate backup administration from normal production
access through separate backup-administration credentials,
least-privilege permissions, restricted network access to backup
management, stronger authentication, monitoring of backup-administration
activity, and prevention of ordinary production accounts from modifying
or deleting protected recovery copies.

Reason: Ransomware operators frequently target credentials and
accessible backup systems to prevent recovery.

Network impact: Backup infrastructure becomes a separate high-trust
recovery zone rather than another generally accessible production
service.

Policy impact: Access Control and Incident Response policies will
explicitly address privileged backup administration.

# 9. Overall Assessment

The exercise demonstrated that AVMC's segmentation and least-privilege
controls provide useful technical boundaries during a ransomware
incident.

However, the tabletop also identified that network security alone does
not guarantee organizational resilience.

Recovery depends on trustworthy backups, controlled credentials,
practiced containment procedures, effective phishing defenses, clear
communications authority, and coordinated technical and executive
decision-making.

The most significant architectural improvement resulting from the
exercise is the addition of an isolated recovery tier. The most
significant procedural improvements are the development of a ransomware
containment playbook and formal escalation/communications matrix.

NIST SP 800-61 Rev. 3 emphasizes that lessons identified during response
should feed continuous improvement across cybersecurity risk-management
activities.

## Exercise Conclusion

AVMC successfully completed the ransomware tabletop exercise.

The exercise validated several existing security controls while
identifying meaningful improvements to AVMC's recovery architecture,
incident-response procedures, workforce defenses, and communications
planning.

The results will be incorporated into the final AVMC network design and
cybersecurity playbook.

# References

National Institute of Standards and Technology. (2024). The NIST
Cybersecurity Framework (CSF) 2.0. NIST CSWP 29.

Nelson, A., Rekhi, S., Scarfone, K., & Souppaya, M. (2025). Incident
Response Recommendations and Considerations for Cybersecurity Risk
Management: A CSF 2.0 Community Profile. NIST SP 800-61 Rev. 3.

Cybersecurity and Infrastructure Security Agency. StopRansomware Guide
and ransomware recovery guidance.
