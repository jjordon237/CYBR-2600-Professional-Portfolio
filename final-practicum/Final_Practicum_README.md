<div align="center">

<h1>Final Practicum Portfolio</h1>
<h3>JAMES JORDON | CYBERSECURITY &amp; NETWORK SYSTEMS</h3>
<p>
<img src="https://img.shields.io/badge/PROGRAM-CYBR--2600-2563EB?style=flat-square&amp;labelColor=101827" alt="Program">
<img src="https://img.shields.io/badge/FOCUS-PRACTICAL_IT_%26_CAREER_READINESS-172B4D?style=flat-square&amp;labelColor=101827" alt="Focus">
<img src="https://img.shields.io/badge/EVIDENCE-DOCUMENTED_%26_ONGOING-475569?style=flat-square&amp;labelColor=101827" alt="Status">
</p>
<p><strong>Supervised infrastructure work · Network security capstone · Professional development · Evidence-based reflection</strong></p>
<p><a href="../README.md">Portfolio Home</a> · <a href="../projects/avmc-hospital-network-capstone/">AVMC Capstone</a> · <a href="../technical-work/">Technical Work</a> · <a href="../career-materials/">Career Materials</a></p>

</div>

---

## Practicum Overview

This page brings together my **CYBR-2600 Cyber Security & Network Practicum** experience at Hocking College. It distinguishes **supervised physical IT work**, **academic network simulations**, and **professional-development simulations**. My goal is to show what I worked on, what I learned, how I approached problems, and where further verification or experience is needed.

## Featured Supervised Experience: Computer-Lab Deployment

As part of supervised practicum activities, I helped with the rearrangement and preparation of Hocking College computer labs. My most detailed documented example is **JL357**, where I moved and positioned **18 Alienware desktop computers**, arranged monitors, staged Corsair and Dell keyboards and assorted mice, and organized DVI/HDMI and power cables for students in the Hardware class to complete assembly. I worked alongside Owen while supporting a classroom of approximately 20 students.

The experience taught me that workstation spacing, cable placement, and room layout matter for safe movement and practical classroom use.

**Equipment exception — Esports006:** One workstation remained at the login screen and did not respond to multiple keyboards or mice tried during the activity. The cause was not determined. We documented the problem and continued supplying equipment to the rest of the class. Based on my reported outcome, **17 of 18 workstations were functional (about 94.4%)**; this is a field observation, not a formal acceptance-test result. Age and storage conditions were possible explanations, not verified causes.

**Evidence:** Original photographs document equipment staging, workstation placement, and classroom use. Selected equipment-focused photographs are included in the separate JL357 appendix; publication of images showing recognizable classmates requires appropriate permission.

**Other lab work:** Additional classroom redesign activities were reported, but dates, scope, and individual contributions should be added only when confirmed.

## Featured Technical Project: Appalachian Valley Medical Center

[**Explore the AVMC Healthcare Network Capstone**](../projects/avmc-hospital-network-capstone/)

AVMC is a **fictional Cisco Packet Tracer healthcare environment**, developed as a separate academic capstone. Its collapsed-core design, functional VLAN segmentation, inter-VLAN routing, ACL controls, network services, and ransomware tabletop provide documented evidence of technical problem-solving and security governance.

One important test revealed that creating a recovery VLAN did **not** automatically isolate it from routed production traffic. I added bidirectional ACL restrictions and validated the intended denials through testing and ACL counters. **A later demonstration revealed unexpected Guest Laptop access to the internal EHR; that issue remains open for investigation.** These results demonstrate selected controls within Packet Tracer, not production-grade backup immutability or full ransomware resilience.

## Evidence Index

| Competency | Supporting work | Evidence location | Status |
|---|---|---|---|
| Physical IT deployment | JL357 deployment and other supervised lab activities | This page; original photographs and separate appendix | JL357 details documented; other lab details pending |
| Network architecture and segmentation | AVMC VLANs, SVIs, trunking, and ACLs | [AVMC](../projects/avmc-hospital-network-capstone/) | Documented academic simulation |
| Incident response and governance | AVMC ransomware tabletop, AUP, ACP, IRP | [AVMC Week 08](../projects/avmc-hospital-network-capstone/Week%2008/) | Documented academic work |
| Security awareness | Mastercard phishing simulation design and results interpretation | [Forage](../Forage/) | Completed October 6, 2026 |
| Web application security learning | Commonwealth Bank-associated authorized labs; Deloitte simulation | [Forage](../Forage/) | In progress |
| Cloud foundations | AWS Academy Cloud Foundations, 20-hour training badge | [Certification](../certification/) | Training completed; certification exam not yet passed |
| Professional communication | Updated public résumé and career materials | [Career Materials](../career-materials/) | Portfolio materials prepared |
| KC7 investigation | No assignment yet | [KC7](../k7-cyber/) | Not started / awaiting assignment |

## Forage Simulations and Web-Security Study

| Activity | What I did or studied | Status / evidence |
|---|---|---|
| **Mastercard Cybersecurity Job Simulation** | Designed a phishing-email simulation and interpreted simulation results to consider awareness improvements. | **Completed October 6, 2026**; Forage certificate obtained. |
| **Deloitte Cybersecurity Job Simulation** | Began the employer-designed learning experience; specific completed deliverables have not yet been verified. | **In progress**; certificate pending. |
| **Commonwealth Bank / authorized web-security study** | Studied SQL injection, NoSQL injection, OAuth, and HTTP request/response behavior through authorized PortSwigger labs and Burp Suite Community Edition. | **In progress**; no completed Forage certificate claimed. |

The simulations are educational activities, not employment or professional certifications. The Mastercard certificate should be uploaded and linked only after its repository path is confirmed.

## Executive Summary and Recommendations

The completed Mastercard exercise reinforced that suspicious email messages can create avoidable organizational risk when employees are unsure how to recognize or report them. The recommended leadership decision is to support a practical awareness program with clear reporting instructions and follow-up measurement. These are recommendations based on the exercise, **not claims of measured improvements**.

1. **Prioritize short phishing-awareness training.** Owner: security awareness lead with HR. Effort: low to medium. Trade-off: time away from other work.
2. **Make suspicious-email reporting simple.** Owner: IT/security team. Effort: medium. Trade-off: more reports for staff to review.
3. **Repeat an authorized exercise and review outcomes.** Owner: security awareness lead. Effort: medium. Trade-off: scheduling and possible training fatigue; protect employee privacy.

## Capstone Briefing and Submission Evidence

A **nine-slide Practicum Capstone Briefing** and **Practicum Capstone Final Package** have been prepared for the course assignment. Add working relative links here only after the actual files have been uploaded into the repository. The separate **JL357 photographic appendix** supports the supervised deployment description. Estimated practicum hours require final review before submission; the briefing is not represented as delivered until it has been presented or recorded.

## AI Use and Verification

ChatGPT assisted with structuring and editing the practicum materials, summarizing technical descriptions for a college-level audience, and drafting executive recommendations. I checked claims against my firsthand JL357 account and photographs, the Mastercard completion certificate, and AVMC project records. Unsupported simulation metrics, unverified repairs, unearned certificates, and unconfirmed hours are not presented as established facts. The AVMC Guest Laptop's unexpected access to the internal EHR is a **known issue awaiting further investigation**, not a resolved security control.

## Professional Reflection

My practicum has reinforced that IT work is more than a successful configuration. Physical deployment requires organization, careful equipment handling, cable management, verification, and follow-through when a workstation does not behave as expected. AVMC similarly taught me to distinguish an intended security design from a tested security outcome: a VLAN alone was not sufficient evidence of isolation.

I have also learned to document limitations honestly. A simulation can demonstrate concepts without reproducing a production environment, and a training badge or virtual job simulation is not the same as industry certification or employment. I want employers to be able to trace my claims to work samples and understand what I would still need to learn on the job.

## Continuing Development

My near-term priorities are completing the remaining Forage simulations, preparing for the AWS Certified Cloud Practitioner examination and CompTIA A+ and SEC+ examinations, strengthening networking skills, and beginning formal Python coursework. I will continue refining this portfolio as new work and verified evidence become available.

## Presentation and Defense

The portfolio supports discussion of technical choices, test results, failures, corrections, and career development. A nine-slide practicum briefing has been prepared; presentation delivery or recording submission is not claimed until completed.

## Evidence and Publication Standards

Only authorized educational or simulated material is published. College-specific asset identifiers, confidential records, credentials, and personal information are excluded. Supervisor verification and any later repair of Esports006 will be added when confirmed. AI assistance may support editing, organization, and review, but reported results and professional claims remain my responsibility.

---

<div align="center">

**James Jordon** · CYBR-2600 Cyber Security & Network Practicum  
[Return to Professional Portfolio](../README.md)

</div>
