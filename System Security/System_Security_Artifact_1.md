# Security Event Investigation and Log Analysis — Frothly Guided Activities

**Course:** Cisco CCNA Security (2026AU-CYBR-2102-C535): Cisco NetAcad - Data and Tools for Defense Analysts

**Semester:** Autumn 2026  
**Knowledge Area:** System Security  
**Crosscutting Concepts:** Confidentiality, Integrity, Availability, Risk, Adversarial Thinking, Systems Thinking, Responsible AI  
**Skills Demonstrated:** Log source selection; evidence correlation; cloud and identity activity analysis; event filtering; endpoint alert interpretation; observation vs. inference; escalation documentation  

## Overview

This artifact is a summary of three guided Cisco Networking Academy Data and Tools for Defense Analysts activities using the fictional Frothly environment provided by Splunk. I utilized the given parameters to make reasonable interpretations Splunk views to practice selecting relevant evidence (4-1), recognizing suspicious activity (4-2), and distinguishing observations from conclusions (4-3).

## What I Did

After reviewing the supplied scenario documentation, I made useful predictions based on evidence before advancing through each walkthrough and compared my initial guesses with the provided results. I did not conduct any of the searches or investigate a production environment as they were predetermined scenarios.
Activity 4.1 — Evidence in the Cloud: I began by predicting a good starting place would be to  analyze the AWS access and endpoint logs to identify who made changes affecting an S3 bucket. The walkthrough demonstrated narrowing the search by sourcetype and a time boundary after August 20, 2018, at 13:01. My recommendations after were to extend reviewing all CloudTrail activity, accounts, and other sources rather than concluding from one filtered view; this increase of scope would allow more important evidence to be collected.
Activity 4.2 — Through the Looking Glass: The scenario involving an old Frothly user account that should have been deactivated, klagerfield@froth.ly, and the IP address 199.66.91.253, stated to be associated with a Canadian sign-in/IP. The activity record reported two Frothly user accounts appearing in activity associated with the same IP and failed attempts marked invalid username/password. I recognized that investigating only one username could omit other relevant identity activity, such as other illegitimate accounts that may have access to sensitive or proprietary information. I recommended checking authorization and authentication logs via sign-in outcomes, IPs, account status, roles, and related activity before determining that lateral movement within the Frothly system or illegitimate account creation occurred by Kevin.
Activity 4.3 — Infected: I focused on Windows event information and Symantec Antivirus logs by focusing on application scans through Windows Event Viewier. I distinguished the event category (sourcetype) from the data source and application context such as Symantec Anitivirus versus Windows alerts, then considered how host-level event counts could guide triage without demonstrating how serious or widespread an infection could potentially be. Those host-level events were only the ones that had been found within the system at that time. I proposed correlating antivirus records with Windows security and endpoint evidence to continue scanning the entire system for more compromised computers or files. I also proposed watching all data logs to maintain integrity of the data within the system as well to make sure data theft  had not occurred. 

## Evidence

Activity 4.1: My original prediction named AWS access and endpoint logs as the primary sources for evidence. My written follow-up identified sourcetype filtering and a specific time boundary as additions in the guided investigation which would provide more explicit and relevant details to the investigation. That is why its so important to continue scanning the system via endpoint logs to  catalog, contain, and document any and all unauthorized changes to the system or S3 buckets. 
Activity 4.2: I documented the account identifier, source IP, two associated Frothly users, and failed sign-ins via my notes and write-up. These observations of multiple Frothly accounts from the same IP warrant additional review but does not independently establish successful access or lateral movement. It does, however, give the evidence to further investigate both accounts which would have been missed if only just the compromised account was scanned and not the IP. That is why its relevant to not limit investigative scans to only one particular source or sourcetype.
Activity 4.3: My notes identify Symantec Antivirus and Windows event records as the primary source of information at this time, and explains that counts in a host summary are insufficient by themselves to confirm compromise. In the Frothly example, we do not have enough information to determine the extent of the infection within the system. We must utilize more than just WMI Event logs to determine the extent and begin quarantining the infected systems. 
Evidence handling: Complete screenshots of the vendor walkthrough and course records submitted shows the use of AWS logs, Azure logs, and WMI Event viewer logs can all be utilized through Splunk to . For my public GitHub portfolio, my published original explanation and a self-created summary/table were used instead of copying vendor slides, answer keys, or assessment materials. 

## AI Use & Verification

AI was used to organize and edit my three existing Week 4 activity records into one portfolio narrative and README. I reviewed the output against my original files: Jordon_W4_Activity41.docx, Jordon_W4_Activity42.docx, and Jordon_W4_Activity43.docx. The synthesis separates observations from hypotheses, clarifies that an IP address is a field value rather than a sourcetype, and avoids stating that suspicious behavior proves compromise. This editorial review is not independent verification against a live Splunk dataset or the complete NetAcad platform. Any final publication should be checked by me against my course views and instructions.

## What I Learned

After conducting these labs and using multiple forms of log analysis from several different companies, I learned that selecting a useful log source initially is only the first step in event analysis. Time windows, source types, user identities, IP addresses, authentication results, and host details are all used as integral evidence for what an analyst can reasonably conclude is currently happening on the system. A narrow filter can help triage a problem quickly, but it can also hide related events and therefore have the potential to create even more problems on the back end if not properly handled. Antivirus detections or event counts need context of the actual event, corroboration by several logs as to wat it is about and why, and careful interpretation before assumptions can occur. 

## Cybersecurity Connection

These exercises are integral to anyone studying cybersecurity as they connect security monitoring, identity and access management, cloud audit logging, endpoint defense, and incident triage to hands-on practice. Cloud change records may point to misconfiguration or unauthorized changes rather than lateral movement within the system; authentication patterns may suggest misuse but require confirmation for any hypothesis can be made; endpoint alerts may indicate suspicious activity but cannot establish severity on their own as the extent of the infection may not always be scanned within the scope of the antivirus initially. The broader defense in depth principle is to corroborate independent evidence such as a multitude of logs while respecting authorization and the limits of each data set, individual employee’s privacy, and maintaining scans within scope of the investigation.

## Professional Connection

These standard methods through Splunk would be used by a junior SOC analyst, security monitoring analyst, cloud security analyst, or incident responder to conduct approved investigations through reviewing alerts, creating timelines, distinguishing confirmed facts from possibilities and conjecture, and preparing a clear documented handoff to their superiors. Appropriate escalation of a situation includes the relevant metadata such as time windows, accounts, hosts or IPs, log sources, observed results, gaps in evidence, and recommended next checks.

## Limitations and Next Checks

These labs were guided educational walkthroughs of Splunk using vendor-provided views; I did not independently execute searches against a live production environment. As a result, the source records cannot establish whether the AWS changes were authorized, whether the observed sign-ins succeeded, whether additional accounts were created, or whether any host was actually compromised. A complete investigation would therefore compare the change events against approved activity, examine authentication successes, failures, and user roles, correlate timestamps across data sources, and review endpoint detections and any response actions taken. 

Cisco Networking Academy, Data and Tools for Defense Analysts, guided activities 4.1 “Evidence in the Cloud,” 4.2 “Through the Looking Glass,” and 4.3 “Infected”; author’s Week 4 activity records (November 2026).
