[README_System_Security.md](https://github.com/user-attachments/files/34866684/README_System_Security.md)
# System Security — Cybersecurity Playbook

This page documents how I am building practical cybersecurity investigation skills through structured coursework, evidence review, and careful analyst reasoning. The materials are educational portfolio examples; they do not describe unauthorized testing or production incident response.

## Featured Artifact

### [Artifact 1: Security Event Investigation and Log Analysis](./System_Security_Artifact_1.md)

**Course:** Cisco CCNA Security (2026AU-CYBR-2102-C535): Cisco NetAcad — Data and Tools for Defense Analysts  
**Semester:** Autumn 2026  
**Knowledge Area:** System Security

This artifact combines three guided Frothly scenarios into one investigation workflow:

| Activity | Investigative focus | Key lesson |
| --- | --- | --- |
| 4.1 — Evidence in the Cloud | Cloud logs and S3 changes | Time windows and sourcetypes help narrow evidence without proving intent. |
| 4.2 — Through the Looking Glass | Authentication and identity activity | A username-only filter may miss related activity from the same IP or other accounts. |
| 4.3 — Infected | Symantec and Windows event information | Antivirus events and host counts require corroboration before declaring compromise. |

## Skills Demonstrated

- Selecting and interpreting security-relevant log sources
- Using time, host, account, IP, and event details to organize an investigation
- Distinguishing observations from hypotheses
- Recognizing the limits of narrow searches and alert counts
- Documenting sensible follow-up checks and escalation information
- Reviewing AI-assisted writing for accuracy and attribution

## Evidence and Academic Integrity

These activities used **vendor-provided Splunk views**. I interpreted the supplied walkthroughs rather than executing searches in a live environment. I publish my original reasoning, not vendor slides, answer keys, private account data, or claims of completed hands-on actions I did not perform.

## Repository Structure

```text
System-Security/
├── README.md
├── System_Security_Artifact_1.md
└── images/
    └── (optional sanitized, original evidence images)
```

## Next Steps

I plan to expand this playbook with additional original artifacts and demonstrations of evidence-based analysis as I advance through my cybersecurity coursework.
