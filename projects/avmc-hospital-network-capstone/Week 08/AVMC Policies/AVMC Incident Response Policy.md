[AVMC_Incident_Response_Policy_Final_James_Jordon.md](https://github.com/user-attachments/files/32986533/AVMC_Incident_Response_Policy_Final_James_Jordon.md)
```{=html}
<p align="center">
```
`<img src="images/avmc-logo.png" alt="Appalachian Valley Medical Center (AVMC) logo" width="400">`{=html}
```{=html}
</p>
```
# Appalachian Valley Medical Center

## Incident Response Policy

**AVMC Information Technology & Security**

  -----------------------------------------------------------------------
  Document Control                    Details
  ----------------------------------- -----------------------------------
  **Policy Owner**                    AVMC Information Technology and
                                      Security

  **Applies To**                      All workforce members, contractors,
                                      students, vendors, systems,
                                      services, and authorized devices

  **Status**                          Approved/Final

  **Review Cycle**                    At least annually and following
                                      significant incidents, exercises,
                                      technology changes, or
                                      cybersecurity-risk changes
  -----------------------------------------------------------------------

## 1. Purpose

The Appalachian Valley Medical Center (AVMC) Incident Response Policy
establishes requirements for identifying, reporting, analyzing,
containing, eradicating, recovering from, and learning from
cybersecurity incidents.

AVMC depends on information systems to support patient care, clinical
operations, medical devices, imaging and laboratory services, pharmacy
operations, administration, physical security, building management, and
communications. Cybersecurity incidents affecting these systems may
disrupt patient care, compromise sensitive information, impair hospital
operations, or create safety risks.

AVMC shall respond to cybersecurity incidents in a coordinated manner
that prioritizes patient safety, preservation of critical services,
protection of information, containment of threats, preservation of
evidence, accurate communication, and timely recovery.

## 2. Scope

This policy applies to suspected or confirmed cybersecurity incidents
involving AVMC-owned, managed, or authorized systems and information.

Covered resources include:

-   clinical workstations and applications;
-   the AVMC electronic health record;
-   servers and infrastructure;
-   administrative systems;
-   imaging and laboratory systems;
-   Medical IoT devices;
-   Facilities/BMS and physical-security systems;
-   network infrastructure and wireless networks;
-   guest-network infrastructure;
-   public-facing AVMC services;
-   user accounts and credentials;
-   organizational data;
-   third-party services used by AVMC.

Examples of incidents include ransomware, malware, phishing,
unauthorized access, credential compromise, data disclosure, network
intrusion, loss or theft of devices, denial of service, and suspicious
activity affecting AVMC operations.

## 3. Incident Reporting

All AVMC users shall promptly report suspected cybersecurity incidents
to AVMC IT/Security.

Users shall report indicators including:

-   ransomware messages or unexpected file extensions;
-   inaccessible or unexpectedly modified files;
-   suspicious email attachments or links;
-   unexpected authentication prompts;
-   malware or endpoint-security alerts;
-   unauthorized account activity;
-   suspected disclosure of sensitive information;
-   unusual network or system behavior;
-   lost or stolen AVMC devices.

Users shall not independently delete evidence, wipe systems, negotiate
with attackers, pay ransom demands, or conduct unauthorized
investigations.

Reports shall be triaged and validated to determine whether an incident
has occurred and what level of response is required.

## 4. Incident Response Authority

AVMC IT/Security is responsible for coordinating the technical incident
response.

When an incident is declared, AVMC shall designate an **Incident
Response Lead** who coordinates containment, investigation,
documentation, recovery, and technical communications.

Depending on the nature and severity of the incident, the response may
also involve:

-   executive leadership;
-   clinical leadership;
-   department managers;
-   privacy/compliance personnel;
-   legal counsel;
-   communications/public-relations personnel;
-   Facilities/BMS personnel;
-   affected technology vendors or service providers;
-   cyber-insurance representatives;
-   law enforcement or government authorities when appropriate.

Only personnel specifically authorized by AVMC leadership may
communicate externally on behalf of AVMC regarding an active
cybersecurity incident.

## 5. Incident Prioritization

Incidents shall be evaluated according to their operational and
cybersecurity impact.

Factors include:

-   effects on patient safety or patient care;
-   loss of availability of clinical services;
-   number and criticality of affected systems;
-   evidence of lateral movement;
-   compromise of privileged accounts;
-   involvement of sensitive or regulated information;
-   effects on Medical IoT, Facilities/BMS, or physical-security
    systems;
-   effects on backups or recovery systems;
-   evidence of external data disclosure;
-   likelihood that the incident remains active.

Incidents affecting patient care, critical clinical services, multiple
network zones, backups, privileged infrastructure, or sensitive
information shall receive immediate escalation.

## 6. Containment

AVMC shall contain cybersecurity incidents as quickly as reasonably
possible while considering patient safety, operational continuity, and
evidence preservation.

Authorized containment actions may include:

-   disconnecting affected endpoints from the network;
-   disabling compromised accounts;
-   blocking malicious traffic;
-   modifying ACLs or network security controls;
-   isolating affected VLANs or network segments;
-   disabling compromised wireless or switch ports;
-   restricting communication between affected zones;
-   suspending vulnerable services;
-   isolating infected Medical IoT or Facilities/BMS devices when
    operationally safe;
-   preventing compromised systems from communicating with backup
    infrastructure.

Network segmentation shall be used to limit lateral movement when
possible.

For example, AVMC's existing separation of Guest, MED-IOT,
Facilities/BMS, Clinical, Server, and management environments provides
boundaries that may be used during containment.

Containment decisions affecting clinical technology shall be coordinated
with appropriate clinical personnel when immediate disconnection could
affect patient care.

## 7. Evidence Preservation and Investigation

AVMC shall preserve relevant evidence before destructive remediation
whenever circumstances permit.

Evidence may include:

-   system and application logs;
-   authentication records;
-   network logs;
-   ACL and firewall records;
-   suspicious email messages and attachments;
-   malicious files;
-   ransom notes;
-   affected filenames and file extensions;
-   timestamps;
-   system configuration information;
-   affected IP and MAC addresses;
-   screenshots;
-   relevant user reports;
-   available volatile or forensic data.

Incident responders shall document significant investigative and
response actions, including who performed the action, what was done, and
when it occurred.

Evidence shall be protected from unauthorized alteration or destruction.

## 8. Eradication

After adequate containment and investigation, AVMC shall remove the
identified cause and artifacts of the incident.

Actions may include:

-   removing malware;
-   disabling compromised accounts;
-   resetting affected credentials;
-   removing unauthorized persistence;
-   patching exploited vulnerabilities;
-   correcting insecure configurations;
-   rebuilding compromised systems;
-   blocking identified malicious indicators;
-   replacing compromised devices when necessary.

Responders shall consider whether an attacker retains access through
additional systems, credentials, or persistence mechanisms before
declaring eradication complete.

## 9. Recovery

AVMC shall restore affected services in a controlled and prioritized
manner.

Recovery priorities shall consider patient safety and the operational
importance of affected systems.

Before restoring a system to production, AVMC should verify that:

-   the threat has been removed or adequately contained;
-   required security controls are operating;
-   restored systems are appropriately patched and configured;
-   credentials have been reset when necessary;
-   backups used for restoration are believed to be trustworthy;
-   restored systems are monitored for recurrence.

Critical services should be restored before lower-priority systems when
operational conditions require prioritization.

## 10. Backup and Ransomware Response

AVMC shall treat compromise of backup infrastructure as a significant
escalation condition.

When ransomware is suspected:

-   affected systems shall be isolated where operationally safe;
-   further spread shall be investigated;
-   backup systems shall be protected from affected systems;
-   ransom notes and malicious artifacts shall be preserved;
-   the suspected entry point shall be investigated;
-   compromised credentials shall be identified and secured;
-   the integrity of available backups shall be evaluated before
    restoration.

The discovery that backups are encrypted, unavailable, or otherwise
compromised shall be immediately communicated to the Incident Response
Lead and AVMC leadership because it materially changes recovery options.

No AVMC employee may independently negotiate or authorize ransom
payment.

Any decision involving a ransom demand requires appropriate executive,
legal, financial, insurance, and law-enforcement considerations
according to organizational requirements.

## 11. Data Breach and External Disclosure

Evidence that AVMC information has been accessed, removed, or publicly
disclosed shall trigger immediate escalation to leadership and
appropriate privacy/legal personnel.

AVMC shall determine, to the extent reasonably possible:

-   what information was affected;
-   whose information was affected;
-   whether information was accessed, exfiltrated, altered, or publicly
    disclosed;
-   the likely scope of the exposure;
-   applicable contractual, legal, regulatory, or notification
    obligations.

AVMC shall not speculate publicly about unverified facts.

External statements shall be coordinated through authorized leadership,
legal/privacy personnel, and communications personnel.

## 12. Communications

Incident communications shall be accurate, timely, coordinated, and
appropriate to the audience.

**Employees** shall receive instructions necessary to protect systems
and continue operations safely.

**Leadership** shall receive information about incident scope,
operational impact, containment, recovery status, material risks, and
decisions requiring executive authority.

**Patients, customers, partners, regulators, law enforcement, and the
public** shall receive information when appropriate and through
authorized channels.

Personnel shall distinguish confirmed facts from information still under
investigation.

## 13. Post-Incident Review and Improvement

Following significant incidents and exercises, AVMC shall conduct a
post-incident review or after-action process.

The review should identify:

-   what occurred;
-   how the incident was detected;
-   what decisions were made;
-   what worked;
-   what failed or caused delay;
-   whether network segmentation and other controls limited impact;
-   whether communications were effective;
-   whether recovery resources functioned as expected;
-   changes needed to technology, policy, training, staffing, or
    procedures.

Improvement actions shall be assigned, prioritized, tracked, and
incorporated into AVMC cybersecurity risk management activities as
appropriate.

## 14. Testing and Exercises

AVMC shall periodically test incident-response capabilities through
tabletop exercises, technical testing, or other appropriate activities.

Exercises should include realistic scenarios affecting critical AVMC
services and should evaluate:

-   notification and escalation;
-   containment decisions;
-   evidence preservation;
-   communications;
-   recovery decisions;
-   roles and responsibilities.

Lessons learned from exercises shall be used to improve this policy and
related procedures.

## 15. Roles and Responsibilities

**All users** shall recognize and promptly report suspected incidents
and follow instructions from authorized responders.

**AVMC IT/Security** shall triage reports, perform or coordinate
technical investigation, implement authorized containment and
eradication actions, preserve technical evidence, support recovery, and
document response activities.

**Incident Response Lead** shall coordinate response activities,
maintain situational awareness, escalate material issues, and ensure
significant decisions are documented.

**Managers and clinical/system owners** shall provide operational
context, assist in determining system criticality, and support
continuity and recovery decisions.

**Privacy/legal personnel** shall evaluate data-exposure and
notification considerations.

**Communications personnel** shall coordinate authorized external
messaging.

**AVMC leadership** shall provide executive direction and authorize
significant organizational decisions outside the authority of technical
responders.

## 16. NIST Cybersecurity Framework 2.0 Mapping

  -----------------------------------------------------------------------
  CSF 2.0 Area            AVMC Policy Alignment   Application
  ----------------------- ----------------------- -----------------------
  **DE.CM - Continuous    Supports detection of   Sections 3, 7
  Monitoring**            suspicious activity     
                          through system and      
                          network monitoring.     

  **RS.MA - Incident      Establishes             Sections 3-5
  Management**            declaration, triage,    
                          prioritization,         
                          escalation, and         
                          coordinated response.   

  **RS.AN - Incident      Requires investigation, Sections 5, 7
  Analysis**              scope determination,    
                          documentation, and      
                          evidence preservation.  

  **RS.CO - Incident      Coordinates internal    Sections 4, 11-12
  Response Reporting and  and external incident   
  Communication**         communications.         

  **RS.MI - Incident      Establishes containment Sections 6, 8, 10
  Mitigation**            and eradication         
                          requirements.           

  **RC.RP - Incident      Establishes controlled  Sections 9-10
  Recovery Plan           restoration of affected 
  Execution**             systems and services.   

  **ID.IM - Improvement** Uses incidents and      Sections 13-14
                          exercises to identify   
                          and implement           
                          improvements.           

  **GV.RR - Roles,        Defines                 Sections 4, 15
  Responsibilities, and   incident-response       
  Authorities**           responsibilities and    
                          decision authority.     
  -----------------------------------------------------------------------

## References

National Institute of Standards and Technology. (2024). *The NIST
Cybersecurity Framework (CSF) 2.0.* NIST CSWP 29.

Nelson, A., Rekhi, S., Scarfone, K., & Souppaya, M. (2025). *Incident
Response Recommendations and Considerations for Cybersecurity Risk
Management: A CSF 2.0 Community Profile.* NIST SP 800-61 Rev. 3.

CISA. *Tabletop Exercise Packages.*

SANS Institute. *Security Policy Templates.*

------------------------------------------------------------------------

*Appalachian Valley Medical Center \| Information Technology & Security
\| Incident Response Policy \| October 2026*
