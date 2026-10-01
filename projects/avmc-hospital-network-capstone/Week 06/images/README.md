[README.md](https://github.com/user-attachments/files/32933378/README.md)
# AVMC Week 6 Image Evidence

This folder contains the curated screenshot evidence used by `WEEK_6_PROGRESS.md` and the Week 6 DOCX report. Duplicate and near-duplicate captures from the build session were intentionally excluded so the GitHub/portfolio evidence set stays readable.

## Image index

| File | What it proves |
|---|---|
| `01_edge_rtr_return_route_validation.png` | EDGE-RTR has the `10.40.0.0/16` summary return route via `10.40.254.1` and can reach the VLAN 60 management addresses. |
| `02_core_vlan50_servers_online.png` | Vlan50 is `up/up`, the server subnet is connected, CORE-SW1 has its default route, and VLAN 50 server pings are succeeding. |
| `03_core_dhcp_relay_helpers.png` | CORE-SW1 client SVIs contain `ip helper-address 10.40.50.2`. |
| `04_dhcp_pool_configuration.png` | Central DHCP pools exist for ADMIN, CLINICAL, IMG-LAB, MED-IOT, GUEST, and FACILITY. |
| `05_dns_records.png` | Internal DNS A records map `dhcp.avmc.local`, `ehr.avmc.local`, and `logs.avmc.local` to the VLAN 50 servers. |
| `06_admin_reg_pc_connectivity_dns.png` | REG-PC1 can reach its gateway, DHCP/DNS server, EHR server, and `ehr.avmc.local`. |
| `07_admin_reg_pc_https_ehr.png` | REG-PC1 successfully opens `https://ehr.avmc.local`. |
| `08_clinical_nurse_pc_validation.png` | NURSE-PC1 validates the CLINICAL VLAN path to gateway, internal services, and DNS. |
| `09_imaging_rad_pc_validation.png` | RAD-PC1 validates the IMG-LAB VLAN path to gateway, internal services, and DNS. |
| `10_dev_med_iot_ap_port_config.png` | DEV-SW1 Fa0/1 is brought up as the MED-IOT access-point port in VLAN 40 with PortFast/BPDU Guard. |
| `11_med_iot_icmp_troubleshooting.png` | CORE-SW1 ICMP to the wireless bedside monitor fails, documenting the Packet Tracer device-model troubleshooting point. |
| `12_med_iot_final_simple_pdu_success.png` | Packet Tracer reports a successful Simple PDU from BEDSIDE-MON1 to CORE-SW1, establishing the Week 6 stopping point. |

## Portfolio hygiene

Screenshots that exposed the MED-IOT wireless pre-shared key were not retained in this curated folder. The report documents the use of WPA2-PSK/AES without publishing the credential.

## Suggested GitHub layout

```text
Week-6/
├── README.md
├── WEEK_6_PROGRESS.md
├── AVMC_Capstone_Week6_Progress_Report_James_Jordon.docx
├── AVMC_Capstone_James Jordon_v3.0.pkt   # add your saved Packet Tracer checkpoint
└── images/
    ├── README.md
    └── 01...12 PNG evidence files
```
