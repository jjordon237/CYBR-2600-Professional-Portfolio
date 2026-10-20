---
layout: default
title: James Jordon | Cybersecurity Portfolio
---

<div align="center">

<h1>James Jordon</h1>
<h3>CYBERSECURITY &amp; NETWORK SYSTEMS</h3>
<p><strong>Security Analysis · Incident Response · Network Infrastructure · Governance &amp; Risk</strong></p>
<p>
<img src="https://img.shields.io/badge/PROGRAM-CYBERSECURITY_%26_NETWORK_SYSTEMS-2563EB?style=flat-square&amp;labelColor=101827" alt="Program">
<img src="https://img.shields.io/badge/GPA-3.93-15803D?style=flat-square&amp;labelColor=101827" alt="GPA">
<img src="https://img.shields.io/badge/PRACTICUM-CYBR--2600-2563EB?style=flat-square&amp;labelColor=101827" alt="Practicum">
<img src="https://img.shields.io/badge/GRADUATION-DEC_2026-475569?style=flat-square&amp;labelColor=101827" alt="Graduation">
</p>
<p><strong>Hocking College</strong> · A.A.S. Cybersecurity &amp; Network Systems (expected December 2026)</p>
<p><strong>Ohio University</strong> · B.A. Psychology</p>
<p><a href="projects/avmc-hospital-network-capstone/">AVMC Capstone</a> · <a href="projects/pdf-download-investigation/">PDF Investigation</a> · <a href="final-practicum/">Practicum</a> · <a href="Competitions/Cyber_Skyline/">Cyber Skyline / NCL</a> · <a href="career-materials/">Career Materials</a> · <a href="https://github.com/jjordon237">GitHub</a></p>

</div>

---

## About Me

I am a cybersecurity and network systems student preparing for entry-level opportunities in security operations, network administration, incident response, and IT support. I bring an interdisciplinary background in psychology, education, social services, and operations to technical problem-solving. My work emphasizes practical testing, clear documentation, responsible decision-making, and the human consequences of security controls.

This portfolio presents selected **academic simulations**, **supervised hands-on IT experience**, and **professional-development activities**. Projects are documented with their objectives, technical approach, evidence, outcomes, and limitations.

## Featured Project: Appalachian Valley Medical Center (AVMC)

<div align="center">
<a href="projects/avmc-hospital-network-capstone/">
<img src="projects/avmc-hospital-network-capstone/Week%2008/images/avmc-logo.png" alt="Appalachian Valley Medical Center — AVMC project logo" width="310">
</a>
</div>

**Simulated Healthcare Network & Cybersecurity Capstone — Cisco Packet Tracer**

Designed, configured, tested, and documented a fictional hospital network using a collapsed-core architecture. The project integrates network segmentation, controlled inter-VLAN connectivity, operational services, healthcare-oriented security policies, and a ransomware incident-response tabletop.

**Technical highlights**

- Multilayer switching with VLANs, trunk links, switched virtual interfaces (SVIs), and inter-VLAN routing.
- Ten operational VLANs covering Administration, Clinical, Imaging/Lab, Medical IoT, Servers, IT Management, Guest, Facilities/BMS, Cold Backup, and Dietary Services.
- Access control lists (ACLs) to restrict unnecessary traffic between trust zones.
- Internal and public-facing web-service simulations, DNS/DHCP, and representative building-management/IoT devices.
- Subsequent VLAN 100 Dietary Services integration with an 802.1Q uplink, validated inter-VLAN connectivity, and a working internal web portal at `dietary.avmc.org`.
- Before-and-after Packet Tracer tests documenting recovery-zone reachability and subsequent ACL enforcement.
- Acceptable Use, Access Control, and Incident Response policies mapped to NIST CSF 2.0.
- Ransomware tabletop, after-action analysis, corrective actions, and technical evidence.

**A key learning outcome:** Creating a separate recovery VLAN did not by itself prevent routed access. Testing exposed the gap; bidirectional ACLs were then applied and tested. The results demonstrate selected network isolation—not backup immutability, full ransomware resistance, or production readiness.

**[Explore the AVMC capstone →](projects/avmc-hospital-network-capstone/)**

## Featured Investigation: PDF Viewer Download Failure

**Web Application Troubleshooting — Microsoft Edge, Browser Developer Tools & HTTP Analysis**

Investigated a reproducible download problem in the ChatGPT document viewer using an evidence-first approach. A direct conversation link downloaded the PDF successfully, but the viewer's download control produced no corresponding Edge Downloads entry. Network inspection showed successful HTTP responses, including JSON download metadata and PDF content headers; **the underlying root cause remains unconfirmed**.

**Technical highlights**

- Used Edge Developer Tools to inspect requests, HTTP status codes, response headers, and JSON metadata.
- Compared a working direct-link download with a failing viewer-control workflow.
- Examined `Content-Type: application/pdf` and `Content-Disposition: attachment` without confusing successful responses with a completed browser save.
- Documented a confirmed workaround, competing hypotheses, investigation limitations, and supporting screenshots.
- Restricted testing to my own file and authorized browser diagnostics; no security vulnerability or exploit is claimed.

**[Explore the PDF download investigation and evidence →](projects/pdf-download-investigation/)**

## Supervised Practicum: Computer Lab Infrastructure

Participated in the redesign and physical deployment of **two Hocking College computer labs**, including workstation relocation, installation and connection of Alienware systems, cable organization, and functional verification. The practicum connects classroom networking concepts to real equipment handling, deployment discipline, troubleshooting, and documentation.

The portfolio will include verified deployment evidence and final workstation outcomes as they are documented.

**[View practicum work →](final-practicum/)**

## Additional Work & Evidence

| Portfolio area | What it demonstrates |
| --- | --- |
| [National Cyber League / Cyber Skyline](Competitions/Cyber%20Skyline/) | Four verified competition participations; individual and team scouting reports, OSINT, cryptography, and network analysis |
| [PDF Download Investigation](projects/pdf-download-investigation/) | Browser DevTools, HTTP diagnostics, controlled reproduction, and documented findings |
| [Technical Work](technical-work/) | Security labs, networking, troubleshooting, and technical documentation |
| [KC7 Cyber Investigations](k7-cyber/) | Investigation methods, log analysis, and evidence-based findings |
| [Forage Job Simulations](Forage/) | Employer-designed virtual tasks and completed simulation evidence |
| [Career Materials](career-materials/) | Résumé, professional background, and career-development materials |
| [Certification & Training](certification/) | Verified training, assessment evidence, and certification preparation |
| [Final Practicum](final-practicum/) | Supervised lab work, project evidence, and professional reflection |


## National Cyber League — Cyber Skyline Competitions

Participated in four National Cyber League (NCL) competitions during Fall 2025 and Spring 2026. Official certificates and scouting reports document both individual and team performance in authorized cybersecurity challenges.

| Competition | National result | Percentile |
|---|---:|---:|
| Spring 2026 Team — Royal Flush | 229 of 3,634 | 94th |
| Fall 2025 Team — HockingCyberHawks | 435 of 4,214 | 90th |
| Fall 2025 Individual | 2,081 of 7,873 | 74th |
| Spring 2026 Individual | 2,673 of 7,010 | 62nd |

Areas practiced include open-source intelligence (OSINT), password security, cryptography, log analysis, and network traffic analysis. Team results reflect shared performance, not individual rankings.

**[Explore verified NCL certificates and scouting reports →](Competitions/Cyber%20Skyline/)**

## Selected Training & Recognition

- **Phi Theta Kappa** honor society member.
- **Mastercard Cybersecurity Job Simulation (Forage)** — completed October 2026; included phishing-simulation planning and interpretation.
- **AWS Certified Cloud Practitioner (CLF-C02) official practice exam** — training/practice completion; **not** an AWS certification.
- Continuing coursework and independent learning in networking, cybersecurity, incident response, and governance.

Credentials are identified as completed, in progress, or planned; simulation certificates are not represented as employment or professional certifications.

## Technical Areas

**Networking:** TCP/IP, VLANs, subnetting, Cisco Packet Tracer, DNS, DHCP, switching, routing, and ACL testing.  
**Security:** Incident-response fundamentals, access control, network segmentation, vulnerability analysis, risk assessment, and security policy.  
**Systems & tools:** Windows, Linux, Wireshark, VirtualBox, Nmap, Git/GitHub, and technical documentation.  
**Governance:** NIST CSF 2.0 mapping, AI-use considerations, privacy, ethics, and organizational accountability.

My skills continue to develop through formal coursework, guided labs, independent practice, and review. Python and advanced networking coursework are part of my upcoming studies.

## How I Document Projects

For substantial work, I aim to show **the problem, the environment, the approach, the evidence, the result, the limitations, and the next improvement**. I distinguish simulated behavior from production capabilities and do not treat a blocked ping as proof of comprehensive security.

## Career Interests

I am interested in opportunities in **SOC/security analysis, incident response, network and systems administration, IT support, and cybersecurity governance** where I can contribute, learn from experienced professionals, and grow through hands-on responsibility.

**[Explore career materials →](career-materials/)**

## Security, Privacy & Attribution

This public portfolio contains work from authorized academic or practice environments. Sensitive information, credentials, confidential records, and private third-party data should not be published. AI tools have assisted with research, troubleshooting, document organization, and editing; I remain responsible for verifying claims, documenting actual results, and accurately describing my contributions. The AVMC hospital is fictional and the simulation is not a claim of production deployment or regulatory certification.

---

**James Jordon** · Cybersecurity & Network Systems  
[GitHub Profile](https://github.com/jjordon237) · [Portfolio Repository](https://github.com/jjordon237/CYBR-2600-Professional-Portfolio)
