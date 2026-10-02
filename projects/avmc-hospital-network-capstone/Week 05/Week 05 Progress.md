[WEEK_5_PROGRESS_UPDATED.md](https://github.com/user-attachments/files/32938779/WEEK_5_PROGRESS_UPDATED.md)

# AVMC Capstone — Week 5 Progress Report (Updated)

**Project:** Appalachian Valley Medical Center (AVMC) Packet Tracer Capstone  
**Student:** James Jordon  
**Course:** NET-2650 Capstone Planning and Implementation  
**Original Week 5 checkpoint:** October 1, 2026  
**Documentation revision:** October 1, 2026  
**Week 5 Packet Tracer checkpoint:** `AVMC_Capstone_James Jordon_v1.0.pkt`  
**Current project checkpoint:** `AVMC_Capstone_James Jordon_v3.0_Week 6.pkt`

> **Week 5 stopping point:** All four access switches were fully trunked, segmented, assigned management SVIs, and hardened. CORE-SW1 was performing inter-VLAN routing for the active hospital VLANs, management reachability was verified to every access switch, and a default route toward EDGE-RTR was installed. VLAN 50 was configured but intentionally remained `up/down` until the internal servers were connected in the following phase.

> **Revision note:** This update preserves the Week 5 historical checkpoint while adding a clear follow-through section showing which Week 5 next steps were completed during Week 6 and which tasks remain for the next build phase. It does not rewrite later work as if it occurred during Week 5.

## Scope and privacy boundary

AVMC is a fictional rural healthcare training environment. The topology, addressing, services, endpoints, security controls, and troubleshooting evidence in this report are simulated for coursework and portfolio demonstration and do not represent the internal network of a real hospital.

## 1. Week 5 objective

Week 5 focused on completing the access layer and moving the simulation from basic Layer 2 connectivity into a routed hospital network. The work included completing DEV-SW1 and EDGE-SW1, bringing CLIN-SW1 and OPS-SW1 up to the same management and hardening standard, enabling inter-VLAN routing on CORE-SW1, validating the management plane, and establishing a default route toward the edge router.

## 2. Week 5 accomplishments at a glance

| Area | Completed work | Week 5 status |
|---|---|---|
| DEV-SW1 | VLAN 40/60/999 trunking, MED-IOT access ports, management SVI, PortFast/BPDU Guard, unused-port hardening | Complete |
| EDGE-SW1 | VLAN 60/70/80/999 trunking, guest/facility port plan, management SVI, unused-port hardening | Complete |
| CLIN-SW1 | Clinical/imaging access ports, management SVI, hardening, trunk re-verification | Complete |
| OPS-SW1 | Admin/IT access ports, management SVI, hardening, trunk re-verification | Complete |
| CORE-SW1 | `ip routing`, SVIs for VLANs 10–80, routed management reachability, default route | Complete |
| VLAN 50 SERVERS | Gateway `10.40.50.1/28` created; server-facing VLAN prepared | Prepared for Week 6 |
| Management plane | CORE-SW1 verified reachability to all four access-switch management SVIs | Complete |
| Troubleshooting evidence | Native-VLAN mismatch, STP recovery, VLAN-name typo, port-range error, mask correction, ARP learning behavior | Documented |

## 3. Access-layer design completed

The four access trunks use VLAN 999 as the native/unused VLAN and carry only the VLANs required by each switch.

| CORE-SW1 port | Access switch | VLANs allowed | Native VLAN |
|---|---|---|---:|
| Fa0/21 | CLIN-SW1 Gi0/1 | 20, 30, 60, 999 | 999 |
| Fa0/22 | OPS-SW1 Gi0/1 | 10, 60, 999 | 999 |
| Fa0/23 | DEV-SW1 Gi0/1 | 40, 60, 999 | 999 |
| Fa0/24 | EDGE-SW1 Gi0/1 | 60, 70, 80, 999 | 999 |

### Management addressing

| Device | Management SVI | Address |
|---|---|---|
| CORE-SW1 | VLAN 60 | `10.40.60.1/28` |
| CLIN-SW1 | VLAN 60 | `10.40.60.2/28` |
| OPS-SW1 | VLAN 60 | `10.40.60.3/28` |
| DEV-SW1 | VLAN 60 | `10.40.60.4/28` |
| EDGE-SW1 | VLAN 60 | `10.40.60.5/28` |

## 4. DEV-SW1 — medical IoT access layer

DEV-SW1 was a major Week 5 build target. VLANs 40 (`MED-IOT`), 60 (`IT-MGMT`), and 999 (`NATIVE-UNUSED`) were created locally. Gi0/1 was configured as an 802.1Q trunk carrying VLANs 40, 60, and 999.

![DEV-SW1 native VLAN mismatch and STP consistency protection](images/01_dev_native_vlan_mismatch.png)

The first trunk attempt produced a CDP native-VLAN mismatch because DEV-SW1 was already using native VLAN 999 while CORE-SW1 Fa0/23 was still using VLAN 1. STP correctly blocked the inconsistent VLAN condition until the CORE side was corrected. After Fa0/23 was configured with native VLAN 999 and allowed VLANs 40,60,999, the consistency condition cleared and the trunk returned to forwarding.

### DEV-SW1 access-port plan

| Port range | Purpose | VLAN | Security treatment |
|---|---|---:|---|
| Fa0/1–Fa0/8 | Medical/IoT endpoint ports | 40 | Access mode, PortFast, BPDU Guard |
| Gi0/1 | Uplink to CORE-SW1 | trunk | 40,60,999; native 999 |
| Fa0/9–Fa0/24 | Unused | 999 | Access mode, shutdown |
| Gi0/2 | Unused | 999 | Access mode, shutdown |

The planned VLAN 40 endpoints include `BEDSIDE-MON1`, `INFUSION-PUMP1`, `US-CONSOLE1`, `ECG-MON1`, `VITALS-MON1`, `XRAY-CONSOLE1`, and representative medical-device stand-ins. Week 5 prepared the access-layer ports for these devices; endpoint deployment itself continued in Week 6 and remains partially unfinished.

### Week 5 field note: NED-IOT

Packet Tracer's tiny CLI font won one round. VLAN 40 was initially named **`NED-IOT`** instead of **`MED-IOT`**. The VLAN ID and port membership were unaffected; the name was corrected in place with `vlan 40` → `name MED-IOT`.

![NED-IOT corrected to MED-IOT](images/02_dev_med_iot_typo_correction.png)

### Troubleshooting: Fa0/2 entered witness protection

While hardening unused ports, `interface range fastEthernet0/2` was entered instead of the intended `fastEthernet0/9-24`. This moved Fa0/2 into VLAN 999 and shut it down. `show vlan brief` exposed the mistake immediately. Fa0/2 was restored to VLAN 40 with PortFast/BPDU Guard and `no shutdown`, then the correct Fa0/9–24 range was hardened.

![Fa0/2 temporarily moved into VLAN 999 and shut down](images/03_dev_accidental_fa02_hardening.png)

Final DEV-SW1 management was configured as `10.40.60.4/28` with default gateway `10.40.60.1`. The final verification showed Gi0/1 `up/up`, VLAN 60 `up/up`, and unused ports administratively down.

![DEV-SW1 final management and hardening verification](images/04_dev_final_management_hardening.png)

## 5. EDGE-SW1 — guest and facility/security access layer

EDGE-SW1 was configured with VLANs 60 (`IT-MGMT`), 70 (`GUEST`), 80 (`FACILITY`), and 999 (`NATIVE-UNUSED`). Its Gi0/1 trunk carries only 60,70,80,999.

Like DEV-SW1, the first connection generated a native-VLAN mismatch until both sides used native VLAN 999. The console showed STP consistency protection followed by `Port consistency restored`, and the final spanning-tree output showed all four VLANs in forwarding state.

![EDGE-SW1 native-VLAN correction and STP recovery](images/05_edge_trunk_stp_recovery.png)

### EDGE-SW1 endpoint plan

| Port | Endpoint role | VLAN |
|---|---|---:|
| Fa0/1 | GUEST-AP1 | 70 |
| Fa0/9 | FACILITY-PC1 | 80 |
| Fa0/10 | CAMERA-01 | 80 |
| Fa0/11 | DOOR-CTRL1 | 80 |
| Fa0/12 | HVAC-CTRL1 | 80 |
| Fa0/13 | BADGE-READER1 | 80 |

Unused ports Fa0/2–8, Fa0/14–24, and Gi0/2 were moved to VLAN 999 and shut down. EDGE-SW1 management was configured at `10.40.60.5/28`.

![EDGE-SW1 final VLAN, management, hardening, and trunk verification](images/06_edge_final_verification.png)

Week 5 completed the switch-side foundation for guest and facility/security networks. The guest AP, facility/security endpoints, VLAN 80 feature set, and final guest-access policy are intentionally listed as unfinished work because they were not completed at this checkpoint.

## 6. CLIN-SW1 — clinical and imaging completion

CLIN-SW1 had a working trunk from Week 4, but Week 5 completed its endpoint-facing configuration and management plane.

| Port range | Role | VLAN |
|---|---|---:|
| Fa0/1–7 | Nursing/provider/pharmacy/ER/ICU/NURSE-ADMIN1 | 20 CLINICAL |
| Fa0/13–17 | Radiology/lab/X-ray/CT-MRI/ultrasound workstations | 30 IMG-LAB |
| Fa0/8–12, Fa0/18–24, Gi0/2 | Unused | 999 |

Endpoint ports use PortFast and BPDU Guard. Unused ports are administratively shut down. The VLAN 60 management SVI is `10.40.60.2/28`, and the Gi0/1 trunk remained healthy with VLANs 20,30,60,999 allowed, active, and forwarding.

![CLIN-SW1 final verification](images/07_clin_final_verification.png)

A harmless CLI typo (`switchpoer mode access`) was rejected by IOS and immediately corrected, providing another useful example of why verification output matters.

## 7. OPS-SW1 — administration and IT completion

OPS-SW1 was completed using the same access-layer security standard.

| Port | Endpoint role | VLAN |
|---|---|---:|
| Fa0/1 | REG-PC1 | 10 ADMIN |
| Fa0/2 | BILLING-PC1 | 10 ADMIN |
| Fa0/9 | IT-ADMIN1 | 60 IT-MGMT |
| Fa0/3–8, Fa0/10–24, Gi0/2 | Unused | 999 |

The VLAN 60 management SVI is `10.40.60.3/28`. Gi0/1 remains an 802.1Q trunk with native VLAN 999 and VLANs 10,60,999 allowed, active, and forwarding.

![OPS-SW1 final verification](images/08_ops_final_verification.png)

## 8. CORE-SW1 — inter-VLAN routing activated

With the access layer complete, CORE-SW1 was moved into its intended Layer 3 role using `ip routing` and switched virtual interfaces (SVIs).

| VLAN | Name | Gateway | Prefix |
|---:|---|---|---:|
| 10 | ADMIN | `10.40.10.1` | /27 |
| 20 | CLINICAL | `10.40.20.1` | /26 |
| 30 | IMG-LAB | `10.40.30.1` | /27 |
| 40 | MED-IOT | `10.40.40.1` | /27 |
| 50 | SERVERS | `10.40.50.1` | /28 |
| 60 | IT-MGMT | `10.40.60.1` | /28 |
| 70 | GUEST | `10.40.70.1` | /26 |
| 80 | FACILITY | `10.40.80.1` | /28 |

The routed transit link to EDGE-RTR remained `10.40.254.1/30` on CORE-SW1 Gi0/1, with EDGE-RTR at `10.40.254.2/30`.

![CORE-SW1 SVI status; VLAN 50 remains up/down pending server links](images/09_core_svi_status_vlan50_pending.png)

### Why VLAN 50 was `up/down`

VLAN 50 was configured correctly but did not yet have an active Layer 2 member. The server-facing ports had not been physically connected to DHCP-DNS1, EHR-SRV1, or LOG-SRV1, so the SVI was administratively up while its line protocol remained down. This was an expected dependency, not a routing error. Week 6 later activated this VLAN by connecting the servers.

## 9. Troubleshooting: VLAN 10 subnet mask correction

VLAN 10 was initially entered with `255.255.255.192` (/26). The planned ADMIN subnet is `/27`, so the SVI was corrected to `255.255.255.224`.

![VLAN 10 mask correction from /26 to /27](images/10_core_vlan10_mask_correction.png)

The corrected routing table later confirmed `10.40.10.0/27` as directly connected on Vlan10.

## 10. Routing and management verification

After the SVIs were active, CORE-SW1 successfully learned connected routes for VLANs 10,20,30,40,60,70,80 and the routed transit network. VLAN 50 was correctly absent from the connected table while its SVI line protocol remained down.

The first ICMP tests to the management SVIs returned 60% and the first transit test returned 80%. This was consistent with Packet Tracer resolving ARP/MAC information on the first pass rather than a persistent reachability fault.

![Initial ping results during address resolution](images/11_core_initial_arp_ping_results.png)

The tests were repeated after the tables had populated. All access-switch management addresses and EDGE-RTR then returned 100% (5/5):

- `10.40.60.2` — CLIN-SW1
- `10.40.60.3` — OPS-SW1
- `10.40.60.4` — DEV-SW1
- `10.40.60.5` — EDGE-SW1
- `10.40.254.2` — EDGE-RTR

CORE-SW1 was then given a default route:

```text
ip route 0.0.0.0 0.0.0.0 10.40.254.2
```

The final routing table showed:

```text
S* 0.0.0.0/0 [1/0] via 10.40.254.2
```

![Final 100% management pings and default route](images/12_core_final_routing_pings_default_route.png)

## 11. Troubleshooting and lessons learned

| Event | Symptom/evidence | Resolution | Lesson |
|---|---|---|---|
| DEV native-VLAN mismatch | CDP mismatch + STP PVID inconsistency | Set both sides to native VLAN 999 | Trunk parameters must match end-to-end |
| `NED-IOT` typo | `show vlan brief` displayed wrong name | Renamed VLAN 40 to `MED-IOT` | Labels matter for documentation even when forwarding is unaffected |
| Fa0/2 accidental hardening | Fa0/2 appeared in VLAN 999 and admin-down | Restored Fa0/2 to VLAN 40; hardened Fa0/9–24 instead | Verify ranges before and after bulk changes |
| EDGE native-VLAN mismatch | STP blocked inconsistent VLAN | Corrected EDGE/Core native VLAN to 999 | STP consistency protection is valuable evidence, not noise |
| CLIN CLI typo | IOS rejected `switchpoer` | Re-entered valid command | IOS error messages are part of normal troubleshooting |
| VLAN 10 wrong mask | Route showed `10.40.10.0/26` | Corrected SVI to `/27` | `show ip route` verifies subnet intent, not just interface IPs |
| First-pass ping loss | 60–80% initial ICMP success | Repeated after ARP/MAC learning | Do not diagnose from a single transient test |
| VLAN 50 `up/down` | SVI IP configured but line protocol down | Deferred until server links were connected in Week 6 | Interface state must be interpreted in topology context |

## 12. Configuration checkpoint at the end of Week 5

```text
CORE-SW1
  Gi0/1 -> EDGE-RTR 10.40.254.1/30    UP/UP
  Fa0/21 -> CLIN-SW1                   UP/UP
  Fa0/22 -> OPS-SW1                    UP/UP
  Fa0/23 -> DEV-SW1                    UP/UP
  Fa0/24 -> EDGE-SW1                   UP/UP

Management VLAN 60
  CORE-SW1  10.40.60.1/28
  CLIN-SW1  10.40.60.2/28
  OPS-SW1   10.40.60.3/28
  DEV-SW1   10.40.60.4/28
  EDGE-SW1  10.40.60.5/28

CORE default route
  0.0.0.0/0 -> 10.40.254.2

Pending dependency at this checkpoint
  Vlan50 10.40.50.1/28 -> configured, line protocol down until a server link is active
```

## 13. Week 5 next steps — updated follow-through

The original Week 5 report correctly identified the next technical dependencies. This revision records what happened afterward without changing the Week 5 historical stop point.

| Week 5 next step | Current status after Week 6 | Notes |
|---|---|---|
| Add EDGE-RTR return route for `10.40.0.0/16` via `10.40.254.1` | Completed | Return routing was validated during Week 6. |
| Connect VLAN 50 servers to CORE-SW1 | Completed | DHCP-DNS1, EHR-SRV1, and LOG-SRV1 brought VLAN 50 up/up. |
| Assign server IPs | Completed | `10.40.50.2`, `.3`, `.4` with gateway `10.40.50.1`. |
| Configure DHCP relay and pools | Completed | Pools operational for ADMIN, CLINICAL, IMG-LAB, MED-IOT, GUEST, and FACILITY. |
| Configure internal DNS | Completed | `dhcp.avmc.local`, `ehr.avmc.local`, and `logs.avmc.local` created. |
| Validate EHR application path | Completed | `https://ehr.avmc.local` resolved and loaded from tested clients. |
| Bring representative ADMIN/CLINICAL/IMG-LAB clients online | Completed | DHCP, gateway, DNS, EHR and name-resolution tests succeeded. |
| Begin MED-IOT deployment | In progress | `BEDSIDE-MON1` and the MED-IOT AP were validated; the remaining VLAN 40 IoT endpoints still need deployment/testing. |
| Deploy VLAN 80 facility/security endpoints | Not yet complete | CAMERA-01, DOOR-CTRL1, HVAC-CTRL1, BADGE-READER1 and related controls remain. |
| Complete guest access | Not yet complete | Guest AP/client deployment, Internet-only policy, and isolation testing remain. |
| Enforce ACL/security policy | Not yet complete | MED-IOT, GUEST, FACILITY, management, and other least-privilege ACL tests remain. |
| Complete edge Internet/NAT/PAT and broader hardening | Not yet complete | To be completed with the remaining security phase. |

## 14. Remaining project work after the Week 6 checkpoint

The next build phase should complete the unfinished endpoint populations before final security enforcement. The order matters because baseline connectivity should be demonstrated before ACLs are allowed to block traffic.

1. Finish the remaining **VLAN 40 MED-IOT** devices and verify addressing and intended application paths.
2. Deploy the **VLAN 80 FACILITY/security** endpoints and validate their baseline connectivity.
3. Complete **VLAN 70 GUEST** wireless access and verify DHCP/basic reachability.
4. Establish any remaining **edge/Internet and NAT/PAT** functionality needed by the project design.
5. Apply and test **least-privilege ACLs** for MED-IOT, GUEST, FACILITY, and management traffic.
6. Add remaining infrastructure hardening supported by Packet Tracer, such as management restrictions, port security, DHCP protections, and IPv6 containment/design decisions where appropriate.
7. Capture explicit **allowed vs. denied** tests, ACL counters, and failure/recovery evidence for the portfolio.

## 15. Week 5 reflection

Week 5 moved the AVMC simulation from a partially trunked topology into a structured routed network with a consistent management plane. The strongest part of the work was not that every command worked on the first try—it did not—but that each configuration error was visible in Cisco output, traced to a specific cause, corrected, and verified with a second command or connectivity test.

The updated view also shows why the Week 5 foundation mattered. The server activation, DHCP relay, DNS, client testing, and first MED-IOT deployment completed in Week 6 all depended on the access trunks, SVIs, management plane, routing, and port hardening built here. Week 5 therefore represents the transition from device-level configuration into an architecture that could support real service and endpoint validation in the following phase.

## 16. Evidence index

| # | Evidence file | What it demonstrates |
|---:|---|---|
| 1 | `01_dev_native_vlan_mismatch.png` | DEV-SW1 native-VLAN mismatch and STP consistency protection |
| 2 | `02_dev_med_iot_typo_correction.png` | VLAN 40 label corrected from NED-IOT to MED-IOT |
| 3 | `03_dev_accidental_fa02_hardening.png` | Fa0/2 accidental move/shutdown and troubleshooting evidence |
| 4 | `04_dev_final_management_hardening.png` | DEV-SW1 final management, trunk, and unused-port state |
| 5 | `05_edge_trunk_stp_recovery.png` | EDGE-SW1 native-VLAN correction and STP recovery |
| 6 | `06_edge_final_verification.png` | EDGE-SW1 final VLAN, management, hardening, and trunk state |
| 7 | `07_clin_final_verification.png` | CLIN-SW1 final clinical/imaging access-layer configuration |
| 8 | `08_ops_final_verification.png` | OPS-SW1 final ADMIN/IT access-layer configuration |
| 9 | `09_core_svi_status_vlan50_pending.png` | CORE-SW1 SVI state with VLAN 50 pending an active server link |
| 10 | `10_core_vlan10_mask_correction.png` | ADMIN SVI subnet correction to `/27` |
| 11 | `11_core_initial_arp_ping_results.png` | Initial ICMP behavior during ARP/MAC learning |
| 12 | `12_core_final_routing_pings_default_route.png` | Final management reachability and CORE default route |

### Evidence selection note

Duplicate and near-duplicate screenshots were intentionally excluded. The retained set shows a distinct configuration milestone, troubleshooting event, correction, or final verification state. Later Week 6 screenshots remain in the Week 6 evidence set rather than being copied into this Week 5 folder, preserving a clean chronological portfolio trail.
