<p align="center">
  <img src="../images/avmc-logo.png" alt="Appalachian Valley Medical Center (AVMC) logo" width="400">
</p>

# AVMC AI Use, Attribution, and Verification Notes

**Appalachian Valley Medical Center**  
**Cybersecurity Capstone – Week 8**  
**Student:** James Jordon  
**AI System Used:** OpenAI ChatGPT – GPT-5.6 Sol  
**Purpose:** Drafting assistance, technical discussion, documentation organization, and review

---

## 1. Purpose of This Disclosure

Artificial intelligence was used during portions of the Appalachian Valley Medical Center (AVMC) cybersecurity capstone as a drafting, organizational, troubleshooting, and learning aid.

AI-generated material was not treated as an authoritative cybersecurity source. Technical claims, security-framework mappings, and incident-response recommendations were reviewed against authoritative sources including the National Institute of Standards and Technology (NIST), the Cybersecurity and Infrastructure Security Agency (CISA), and SANS Institute materials.

The AVMC Packet Tracer environment, configurations, troubleshooting, testing, screenshots, incident-response decisions, and final design choices were performed, reviewed, or approved by the student.

No real patient information, protected health information (PHI), organizational credentials, or real company data were entered into the AI system. AVMC is a fictional healthcare organization created for educational purposes.

---

## 2. AI System Attribution

The primary generative AI system used during this phase of the project was:

> **OpenAI. ChatGPT (GPT-5.6 Sol) [Large language model]. Used October 2026.**

ChatGPT was used interactively throughout the project rather than as a single one-time document generator.

The AI system assisted with:

- organizing technical documentation;
- explaining networking and cybersecurity concepts;
- discussing Packet Tracer configuration steps;
- helping interpret test results;
- drafting portions of security-policy language;
- organizing NIST CSF 2.0 mappings;
- structuring the ransomware tabletop exercise;
- converting student decisions into professional incident-response language;
- organizing the After-Action Report;
- creating GitHub-ready Markdown;
- suggesting evidence organization and file naming;
- identifying areas requiring additional verification;
- improving readability and presentation.

AI output was reviewed before being incorporated into final project artifacts.

---

## 3. Work Performed by the Student

The student remained responsible for the AVMC network design and final decisions.

Student-performed work included:

- building and modifying the Cisco Packet Tracer topology;
- configuring network devices;
- creating VLANs and SVIs;
- configuring addressing and subnetting;
- configuring DHCP and DNS services;
- connecting and configuring AVMC endpoints;
- configuring Guest, Medical IoT, Facilities/BMS, server, clinical, administrative, management, and recovery environments;
- creating and applying ACLs;
- performing connectivity tests;
- interpreting Packet Tracer behavior;
- troubleshooting failed configurations and connectivity;
- verifying ACL hit counters;
- creating and testing the AVMC public website;
- creating and testing the internal EHR portal;
- configuring the Facilities/BMS environment;
- performing the ransomware tabletop decisions;
- deciding how AVMC should respond to each ransomware inject;
- identifying the missing isolated backup tier during the tabletop;
- implementing VLAN 90 and `COLD-BACKUP1`;
- testing recovery-network connectivity before and after hardening;
- selecting the final architecture and security controls;
- reviewing and approving final policy language;
- capturing screenshots used as technical evidence;
- reviewing final documentation before publication.

The AI system did not directly operate Cisco Packet Tracer.

Commands suggested by AI were entered, observed, tested, and validated by the student before being accepted as part of the final design.

---

## 4. Security Policy Drafting

AI assistance was used to help draft the three required AVMC security policies:

1. Acceptable Use Policy
2. Access Control Policy
3. Incident Response Policy

The policies were written specifically for the fictional AVMC environment rather than copied directly from a generic organizational template.

### Acceptable Use Policy

AI assisted with initial structure and wording.

The student reviewed and edited the policy before designating it as final.

The final policy addresses:

- authorized use of AVMC systems;
- credential protection;
- prohibited activities;
- phishing and email safety;
- network and wireless use;
- protection of sensitive information;
- security monitoring;
- incident reporting;
- organizational responsibilities.

### Access Control Policy

AI assisted with structuring access-control requirements around the actual AVMC network.

The student reviewed the policy and finalized it after confirming that it reflected the implemented architecture.

The policy specifically documents:

- least privilege;
- account and credential management;
- Guest VLAN restrictions;
- Medical IoT restrictions;
- Facilities/BMS restrictions;
- privileged administrative access;
- ACL enforcement;
- access review and monitoring.

### Incident Response Policy

AI assisted with drafting an incident-response structure based on the AVMC environment and NIST incident-response concepts.

The student read the policy in full and explicitly approved the final substantive version.

The policy addresses:

- incident reporting;
- response authority;
- prioritization;
- containment;
- evidence preservation;
- eradication;
- recovery;
- ransomware response;
- backup compromise;
- data disclosure;
- communications;
- post-incident review;
- exercises and improvement.

---

## 5. Authoritative Verification Sources

AI-generated cybersecurity statements were checked against authoritative or established cybersecurity references.

Primary verification sources included:

### NIST Cybersecurity Framework 2.0

**National Institute of Standards and Technology. (2024). _The NIST Cybersecurity Framework (CSF) 2.0._ NIST CSWP 29.**

Used to verify:

- GOVERN concepts;
- PROTECT concepts;
- identity and access control;
- incident detection;
- incident management;
- incident analysis;
- incident communication;
- mitigation;
- recovery;
- continuous improvement.

Official source:

https://doi.org/10.6028/NIST.CSWP.29

### NIST SP 800-61 Revision 3

**Nelson, A., Rekhi, S., Scarfone, K., & Souppaya, M. (2025). _Incident Response Recommendations and Considerations for Cybersecurity Risk Management: A CSF 2.0 Community Profile._ NIST SP 800-61 Rev. 3.**

Used to verify:

- incident-response lifecycle concepts;
- incident triage;
- containment;
- evidence preservation;
- recovery;
- lessons learned;
- integration of incident response with CSF 2.0.

Official source:

https://csrc.nist.gov/pubs/sp/800/61/r3/final

### CISA Tabletop Exercise Packages

**Cybersecurity and Infrastructure Security Agency. _CISA Tabletop Exercise Packages._**

Used as a reference for cybersecurity tabletop-exercise concepts and structured incident-response discussion.

Official source:

https://www.cisa.gov/resources-tools/services/cisa-tabletop-exercise-packages

### CISA Ransomware Guidance

CISA ransomware guidance was used to verify concepts involving:

- ransomware containment;
- protection of backups;
- offline recovery copies;
- compromised credentials;
- recovery planning.

Official CISA cybersecurity guidance was treated as authoritative guidance rather than AI-generated information.

### SANS Security Policy Resources

**SANS Institute. _Security Policy Templates._**

Used as a reference for common organizational security-policy structure and policy topics.

Official source:

https://www.sans.org/information-security-policy

---

## 6. AI Recommendations That Were Reviewed or Modified

AI recommendations were not automatically accepted.

Several recommendations were changed, refined, or rejected during the project.

### Ransom Note Interpretation

During the ransomware tabletop, the ransom note was initially interpreted as possibly being a physical note associated with the affected workstation.

After reviewing the scenario wording, this interpretation was corrected because the scenario specified that the ransom demand appeared as a **text file on the desktop**.

The response was modified accordingly.

Physical-security footage would be preserved only if later evidence suggested unauthorized physical access.

### Ransomware Containment

Initial discussion considered increasingly broad isolation as ransomware spread.

The final approach was refined to avoid automatically shutting down the entire AVMC network.

Systems were instead considered according to three categories:

- confirmed compromised;
- suspected or exposed;
- no current indicators of compromise.

This allowed containment decisions to consider patient safety and continuity of clinical operations.

### HIPAA and Law-Enforcement Discussion

During the tabletop, the student initially questioned whether HIPAA automatically required law-enforcement notification following ransomware.

This was reviewed and corrected.

The final response distinguishes between:

- cybersecurity incident response;
- recommended law-enforcement coordination;
- breach assessment;
- applicable breach-notification obligations.

The project does not state that every ransomware incident automatically creates the same HIPAA notification requirement.

### Cold-Storage Architecture

The original AVMC design did not contain an explicitly isolated cold-storage or immutable recovery tier.

This weakness was discovered during the ransomware tabletop rather than being silently corrected afterward.

The student chose to modify the actual Packet Tracer architecture by adding:

- VLAN 90 – `BACKUP_RECOVERY`;
- `COLD-BACKUP1`;
- recovery-specific addressing;
- recovery-to-production ACL restrictions;
- production-to-recovery ACL restrictions.

The modified architecture was then tested.

### VLAN Separation Versus Security Isolation

Initial VLAN 90 testing demonstrated that `COLD-BACKUP1` could still route to production networks.

The student and AI discussion identified that creation of a VLAN alone did not create sufficient security isolation because `CORE-SW1` performed Layer 3 routing.

ACLs were therefore added and the tests were repeated.

This resulted in an important project lesson:

> **Network segmentation requires policy enforcement. VLAN membership alone does not guarantee isolation.**

### Packet Tracer Limitations

AI recommendations involving enterprise security technologies were limited to what Cisco Packet Tracer could reasonably simulate.

The final documentation explicitly identifies Packet Tracer limitations rather than claiming unsupported capabilities.

For example, `COLD-BACKUP1` represents an isolated cold or immutable recovery tier but is not a true immutable storage platform or physically offline backup device.

---

## 7. Student Decision-Making During the Ransomware Tabletop

The ransomware tabletop was conducted interactively.

The student made the initial response decisions for each inject before those decisions were organized into the final After-Action Report.

Examples of student decisions included:

- isolating the initially affected workstation;
- isolating the affected shared server resource;
- preserving workstation, server, authentication, and security logs;
- expanding containment after multiple departments became affected;
- investigating the phishing email labeled `Invoice`;
- reviewing potentially compromised accounts and authentication activity;
- escalating the incident to leadership, legal/privacy, cybersecurity, and communications personnel;
- recommending a limited factual public statement while the investigation remained incomplete;
- recommending against ransom payment;
- continuing technical investigation after confirmed data exfiltration;
- identifying the need for an isolated backup/recovery tier.

AI was used to challenge, refine, and professionally document these decisions.

The final After-Action Report therefore represents a combination of student decision-making, technical discussion, authoritative-source verification, and AI-assisted documentation.

---

## 8. AI Assistance With Technical Configuration

AI provided configuration suggestions during portions of the Packet Tracer build.

Suggested commands were not considered valid merely because they were generated by AI.

The validation process was:

1. review the proposed command;
2. enter the command into Packet Tracer;
3. observe Cisco IOS or Packet Tracer output;
4. perform a functional test;
5. inspect relevant status or ACL counters;
6. modify the configuration when the result did not match the intended design;
7. save the configuration only after validation.

This process was particularly important during ACL implementation.

For example, recovery-network security was validated through both connectivity tests and:

    show access-lists COLD-BACKUP-OUT

and:

    show access-lists COLD-BACKUP-IN

ACL match counters confirmed that the configured rules were actively denying the test traffic.

---

## 9. AI Assistance With Documentation

AI was used extensively to help organize the large amount of evidence generated during the capstone.

Assistance included:

- converting technical work into structured prose;
- organizing screenshots;
- creating evidence filenames;
- drafting README files;
- generating Markdown versions of final documents;
- creating consistent document headings;
- improving policy formatting;
- organizing the After-Action Report;
- creating the Tool Evidence report;
- maintaining consistent AVMC terminology;
- identifying duplicate or missing documentation;
- improving GitHub presentation.

This assistance changed the presentation of the project but did not replace the underlying technical work or testing.

---

## 10. Attribution in Portfolio Artifacts

Where appropriate, the AVMC portfolio identifies the use of generative AI as a project-support tool.

The preferred attribution is:

> **AI Assistance:** OpenAI ChatGPT (GPT-5.6 Sol) was used for drafting assistance, technical discussion, documentation organization, and review. AI-generated cybersecurity statements were reviewed against NIST, CISA, SANS, course materials, and observed Packet Tracer results before inclusion. Final network configurations, tests, incident-response decisions, edits, and conclusions were reviewed or performed by the student.

This attribution may be included in the Week 8 README or linked to this document rather than repeated in full throughout every project artifact.

---

## 11. Data Privacy and Responsible AI Use

No real AVMC organization exists.

The project uses a fictional healthcare environment for educational purposes.

The AI system was not provided with:

- real patient records;
- real PHI;
- real medical records;
- real organizational secrets;
- production credentials;
- real customer records;
- confidential employer information.

Screenshots and configuration evidence were reviewed for suitability before portfolio publication.

Passwords and credentials used in the simulation were lab-only credentials and are not intended for use in any real environment.

---

## 12. Limitations of AI Assistance

Generative AI can produce incorrect, incomplete, outdated, or inappropriate technical recommendations.

For that reason, AI output was treated as a starting point for review rather than as proof.

Technical validation relied on:

- Packet Tracer results;
- Cisco IOS output available within the simulation;
- successful and failed connectivity tests;
- ACL hit counters;
- observed application behavior;
- authoritative cybersecurity references;
- student review.

Where the simulation, authoritative source, or observed test contradicted an AI suggestion, the verified evidence took priority.

---

## 13. Final Verification Statement

AI was used as an educational and documentation-support tool during the AVMC cybersecurity capstone.

The student remained responsible for reviewing, testing, correcting, accepting, or rejecting AI-generated recommendations.

Security policies were checked against NIST and SANS resources.

Incident-response concepts were reviewed against NIST SP 800-61 Rev. 3, NIST CSF 2.0, and relevant CISA guidance.

Technical recommendations were validated through the actual Cisco Packet Tracer environment whenever the simulator supported the required behavior.

The project therefore documents both **AI assistance and human verification** rather than presenting AI-generated content as independently authoritative.

---

## References and Attribution

Cybersecurity and Infrastructure Security Agency. (n.d.). *CISA Tabletop Exercise Packages.*  
https://www.cisa.gov/resources-tools/services/cisa-tabletop-exercise-packages

National Institute of Standards and Technology. (2024). *The NIST Cybersecurity Framework (CSF) 2.0.* NIST CSWP 29.  
https://doi.org/10.6028/NIST.CSWP.29

Nelson, A., Rekhi, S., Scarfone, K., & Souppaya, M. (2025). *Incident Response Recommendations and Considerations for Cybersecurity Risk Management: A CSF 2.0 Community Profile.* NIST Special Publication 800-61 Revision 3.  
https://csrc.nist.gov/pubs/sp/800/61/r3/final

OpenAI. (2026). *ChatGPT (GPT-5.6 Sol)* [Large language model]. AI-assisted drafting, technical discussion, documentation organization, and review conducted during the AVMC cybersecurity capstone in September–October 2026.

SANS Institute. (n.d.). *Security Policy Templates.*  
https://www.sans.org/information-security-policy

---

*Appalachian Valley Medical Center | Information Technology & Security*  
*Cybersecurity Capstone – Week 8*  
*Fictional healthcare environment created for educational purposes.*
