[README.md](https://github.com/user-attachments/files/32989651/README.md)
# Week 8 Image Evidence

This folder contains the AVMC logo and curated evidence for the *Apply: Defend the Company* assignment.

| File | Evidence demonstrated |
|---|---|
| `avmc-logo.png` | AVMC branding used by the policy Markdown files |
| `final-avmc-topology.png` | Final labeled Week 8 Packet Tracer architecture, including VLAN 90 recovery remediation |
| `final-avmc-topology-detail.png` | Closer architecture view emphasizing segmentation and recovery environment |
| `cold-backup-before-hardening-connectivity.png` | Before-hardening test showing the new recovery VLAN could still route into production |
| `cold-backup-outbound-isolation-validated.png` | After-hardening test showing recovery-to-production traffic blocked while the local gateway remains reachable |
| `cold-backup-outbound-acl-hit-counters.png` | `COLD-BACKUP-OUT` ACL counters proving blocked recovery-to-production attempts |
| `cold-backup-clinical-access-blocked.png` | NURSE-PC1 in the Clinical VLAN denied access to COLD-BACKUP1 |
| `cold-backup-inbound-acl-hit-counters.png` | `COLD-BACKUP-IN` ACL counter showing four production-to-recovery attempts denied |

These images document a complete security-engineering sequence: **identify weakness → modify architecture → test before/after behavior → verify enforcement with ACL counters**.
