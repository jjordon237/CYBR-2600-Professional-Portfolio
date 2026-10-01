[AVMC_Week5_Images_README.md](https://github.com/user-attachments/files/32890300/AVMC_Week5_Images_README.md)
# AVMC Week 5 Evidence Images

This folder contains the screenshot evidence used for **Week 5** of the **Appalachian Valley Medical Center (AVMC) Packet Tracer Capstone**.

The images document the actual build process, including successful configuration milestones, troubleshooting mistakes, corrections, and final verification. They are intentionally retained as evidence of the hands-on configuration process rather than showing only a polished final state.

## Evidence Included

The Week 5 screenshots cover:

- DEV-SW1 trunk configuration and native VLAN recovery
- VLAN 40 `MED-IOT` naming correction after the accidental `NED-IOT` typo
- Accidental hardening of `Fa0/2` and its restoration to the MED-IOT VLAN
- DEV-SW1 management SVI and unused-port hardening
- EDGE-SW1 trunk configuration and STP recovery
- EDGE-SW1 guest, facility, and physical-security VLAN preparation
- CLIN-SW1 clinical and imaging endpoint VLAN assignments
- OPS-SW1 administrative and IT-management endpoint assignments
- Management SVI addressing for all four access switches
- CORE-SW1 SVI creation and inter-VLAN routing
- VLAN 10 subnet-mask correction from `/26` to `/27`
- Initial ICMP packet loss caused by ARP/MAC learning
- Successful repeat management pings at 100%
- CORE-SW1 default route installation toward EDGE-RTR
- VLAN 50 remaining pending until the internal servers are connected

## Screenshot Naming

Screenshots are numbered in the approximate order of the Week 5 build and verification process:

```text
01_dev_native_vlan_mismatch.png
02_dev_med_iot_typo_correction.png
03_dev_accidental_fa02_hardening.png
04_dev_final_management_hardening.png
05_edge_trunk_stp_recovery.png
06_edge_final_verification.png
07_clin_final_verification.png
08_ops_final_verification.png
09_core_svi_status_vlan50_pending.png
10_core_vlan10_mask_correction.png
11_core_initial_arp_ping_results.png
12_core_final_routing_pings_default_route.png
```

These images support the accompanying [`WEEK_5_PROGRESS.md`](../WEEK_5_PROGRESS.md) build log and the Week 5 DOCX progress report.

> **Packet Tracer project:** `AVMC_Capstone_James Jordon_v1.0.pkt`

> **Week 5 stopping point:** Access-switch configuration and hardening were completed, CORE-SW1 inter-VLAN routing was established, management connectivity was verified, and the CORE default route toward EDGE-RTR was installed. EDGE-RTR return routing and VLAN 50 server deployment remain for the next build phase.
