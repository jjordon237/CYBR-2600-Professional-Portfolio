[WEEK_7_PROGRESS.md](https://github.com/user-attachments/files/32981128/WEEK_7_PROGRESS.md)
# AVMC Capstone - Week 07 Progress Report

**Project:** Appalachian Valley Medical Center (AVMC)  
**Student:** James Jordon  
**Course:** NET-2650 Capstone Planning and Implementation  
**Phase:** Week 7 - Facilities, Physical Security, and Guest Wireless Implementation  

---

## 1. Week 7 Summary

Week 7 expanded the AVMC healthcare network beyond the core clinical and server environment by adding a realistic **Facilities / Building Management Systems (BMS)** segment and a dedicated **Guest Wireless** environment for patients and visitors.

The Facilities work added a BMS server, facilities workstation, HVAC/thermostat components, security doors, representative wireless cameras, and a dedicated facilities wireless access point. The Guest network was then populated with a mixed set of personal devices to emulate a hospital waiting room, including a laptop, two smartphones, a tablet, and a smart-TV simulation.

The week also included several Packet Tracer troubleshooting exercises involving inconsistent IoT object behavior, stale DHCP behavior, wireless registration, and device replacement. These issues were resolved without unnecessarily redesigning working network infrastructure.

Week 7 ended with both VLAN 80 FACILITY and VLAN 70 GUEST operating successfully at baseline. Security restrictions are deliberately reserved for Week 8 so that the project retains a clear pre-hardening state for comparison.

---

## 2. Existing Network Context

The Week 7 work built on the previously completed AVMC architecture, including:

- CORE-SW1 as the multilayer core switch
- Inter-VLAN routing enabled at the core
- Centralized DHCP/DNS services on VLAN 50
- Routed connectivity to EDGE-RTR
- Departmental VLANs for administration, clinical systems, imaging/lab, medical IoT, servers, IT management, guest access, and facilities
- Dedicated access switches and trunk links
- DHCP relay through `ip helper-address 10.40.50.2`

Relevant Week 7 VLANs:

| VLAN | Name | Subnet | Default Gateway |
|---|---|---|---|
| 70 | GUEST | `10.40.70.0/26` | `10.40.70.1` |
| 80 | FACILITY | `10.40.80.0/28` | `10.40.80.1` |
| 50 | SERVERS | `10.40.50.0/28` | `10.40.50.1` |

---

## 3. Facilities / BMS Implementation

### 3.1 BMS Server

A dedicated **BMS-SRV1** server was added to VLAN 80 and connected to `EDGE-SW1 Fa0/14`.

The server uses a static address:

- IP address: `10.40.80.2`
- Subnet mask: `255.255.255.240`
- Default gateway: `10.40.80.1`
- DNS server: `10.40.50.2`

The server was configured to provide Packet Tracer IoT registration services for facilities devices.

The switch port was configured as a hardened access port using VLAN assignment, PortFast, and BPDU Guard.

```text
interface fa0/14
 description BMS-SRV1
 switchport mode access
 switchport access vlan 80
 spanning-tree portfast
 spanning-tree bpduguard enable
 no shutdown
```

Connectivity testing from BMS-SRV1 confirmed reachability to the VLAN 80 gateway and central AVMC server resources.

### 3.2 Facilities Workstation

`FACILITIES-PC1` was moved to VLAN 80 after an initial cabling mistake placed it on the guest network. Once corrected, the workstation received a valid VLAN 80 DHCP lease and successfully communicated with the BMS server.

This troubleshooting event reinforced an important practical lesson: when a device receives an unexpected subnet, verify the **physical switch port and VLAN assignment first** before assuming DHCP is malfunctioning.

### 3.3 Facilities Wireless Access Point

A dedicated access point was installed for facilities IoT devices and connected to `EDGE-SW1 Fa0/15`.

```text
interface fa0/15
 description AP_FACILITY_IOT
 switchport mode access
 switchport access vlan 80
 spanning-tree portfast
 spanning-tree bpduguard enable
 no shutdown
```

The facilities WLAN was configured with WPA2-PSK and AES encryption. The actual pre-shared key is intentionally excluded from this public documentation.

### 3.4 HVAC / Thermostat Integration

The environment includes:

- `BMS-THERM1`
- `BMS-FURN1`
- `BMS-AC1`
- local SBC controller representation

`BMS-THERM1` joined the facilities wireless network, received a VLAN 80 DHCP address, and registered successfully with BMS-SRV1.

Packet Tracer's device model supports thermostat outputs for heating and cooling control. The SBC was retained as a local controller representation, while BMS-SRV1 remains the network-facing management system.

### 3.5 Physical Security Doors

Three representative security doors were successfully registered:

- `ER-SEC-DOOR1`
- `PHARM-SEC-DOOR1`
- `SERVER-ROOM-DOOR1`

These devices joined the VLAN 80 wireless network and were registered with BMS-SRV1 for centralized monitoring/control.

One door object repeatedly failed to obtain normal service despite identical network conditions. Replacing the Packet Tracer object immediately resolved the problem. This became an important troubleshooting lesson: if multiple identical devices work on the same WLAN/VLAN but one object remains nonfunctional, test a **fresh replacement object** before changing the network design.

### 3.6 Wireless Security Cameras

Two wireless cameras were retained as representative proof of concept:

- `ER-CAM1`
- `LOBBY-CAM1`

Additional camera objects exhibited inconsistent Packet Tracer IoT behavior. Because the WLAN, VLAN, DHCP service, BMS server, doors, thermostat, and two cameras were all already functioning, the issue was treated as a simulator object limitation rather than evidence of a broader network fault.

The two working cameras are sufficient to demonstrate the intended design pattern while avoiding unnecessary redesign around simulator instability.

---

## 4. Facilities DHCP Capacity Adjustment

The original VLAN 80 DHCP pool was too restrictive for the growing collection of facilities devices. The DHCP pool was expanded within the existing `/28` network.

Final design:

- Network: `10.40.80.0/28`
- Gateway: `10.40.80.1`
- BMS-SRV1 static: `10.40.80.2`
- Reserved infrastructure space: `10.40.80.3`
- DHCP range begins at: `10.40.80.4`
- Maximum DHCP users: 11
- Broadcast: `10.40.80.15`

This allowed the subnet to support the planned Facilities/BMS environment while preserving a clear distinction between infrastructure and dynamic endpoints.

---

## 5. Guest Wireless Implementation

### 5.1 Guest WLAN

A dedicated guest access point was configured for VLAN 70 and connected through `EDGE-SW1 Fa0/1`.

The WLAN uses WPA2-PSK with AES encryption. As with the facilities WLAN, the actual pre-shared key is excluded from the public portfolio.

### 5.2 Waiting-Room BYOD Simulation

The guest environment was designed to look and behave like a hospital waiting room with a mixed collection of patient/visitor devices rather than a single test client.

Representative guest endpoints include:

- `GUEST-LAPTOP1`
- `PERSONAL-PHONE1`
- `PERSONAL-PHONE2`
- `PERSONAL-TABLET1`
- `WAITING-ROOM-TV1`

The devices were visually clustered around the guest access point to make the topology easier to interpret during presentation.

### 5.3 Smart-TV Simulation

Packet Tracer does not provide a suitable native smart-TV endpoint for this use case. A generic wireless endpoint was therefore configured as `WAITING-ROOM-TV1` and given a custom television image for visual realism.

Functionally, the device remains a real wireless guest endpoint on VLAN 70 rather than a decorative object. It received a valid DHCP lease and participated in the same network as the other waiting-room devices.

This approach demonstrates a practical modeling technique: use the available simulator object for network behavior while customizing its appearance to better represent the real-world endpoint being modeled.

---

## 6. Guest DHCP Capacity Planning

VLAN 70 uses:

- Network: `10.40.70.0/26`
- Subnet mask: `255.255.255.192`
- Gateway: `10.40.70.1`
- Broadcast: `10.40.70.63`
- Total usable host addresses: 62

The guest DHCP pool begins at `10.40.70.10`.

During Week 7, the maximum guest DHCP users was increased from **40 to 50** to better support a realistically busy waiting room and reduce the chance of address exhaustion.

The resulting address plan is:

| Range | Purpose |
|---|---|
| `10.40.70.1` | VLAN 70 default gateway |
| `10.40.70.2 - 10.40.70.9` | Reserved / future infrastructure |
| `10.40.70.10 - 10.40.70.59` | 50 DHCP guest leases |
| `10.40.70.60 - 10.40.70.62` | Reserved / future use |
| `10.40.70.63` | Broadcast |

This capacity increase uses the `/26` efficiently without requiring a subnet redesign.

---

## 7. Guest Validation Results

The guest network was validated in stages.

### DHCP and WLAN Validation

`GUEST-LAPTOP1` successfully received:

- IPv4 address: `10.40.70.12`
- Subnet mask: `255.255.255.192`
- Default gateway: `10.40.70.1`
- DNS: `10.40.50.2`

`WAITING-ROOM-TV1` also received a valid VLAN 70 address (`10.40.70.15` during testing), confirming that the custom smart-TV simulation was functioning as a real network endpoint.

### Gateway Reachability

`GUEST-LAPTOP1` successfully pinged `10.40.70.1` with 0% packet loss, proving:

- wireless association
- DHCP addressing
- AP-to-switch connectivity
- VLAN 70 access-port placement
- VLAN 70 SVI/gateway operation

### Internal Baseline Reachability

Guest devices were also able to reach `10.40.50.2`, the internal AVMC DNS/DHCP server, before security hardening.

This is intentionally retained as **pre-ACL baseline evidence**. In Week 8, guest traffic will be restricted so that visitors can reach approved public resources without reaching protected AVMC internal networks.

---

## 8. Troubleshooting Lessons From Week 7

Week 7 produced several useful real-world troubleshooting lessons.

### Verify Layer 1 / Layer 2 Placement First

When FACILITIES-PC1 unexpectedly received a guest address, the cause was a physical connection to the wrong access port. The correct response was to verify cabling and VLAN assignment before changing DHCP configuration.

### First-Ping Failure Can Be Normal

Some first ICMP attempts timed out before succeeding on subsequent attempts. This behavior was consistent with ARP resolution and Packet Tracer timing rather than a persistent routing fault.

### Do Not Dismantle Working Infrastructure for One Bad IoT Object

A security door and several camera objects behaved inconsistently even though identical devices worked on the same WLAN. Replacing a malfunctioning object proved more effective than changing a known-good AP, switch port, DHCP pool, or BMS server configuration.

### Watch DHCP Capacity and Simulator Lease Behavior

As the number of IoT and guest devices increased, address-pool planning became increasingly important. Packet Tracer can also retain leases in ways that make troubleshooting appear inconsistent, so subnet capacity and active client counts should be checked before assuming routing or wireless failure.

### Simulator Limitations Should Be Documented, Not Hidden

Using two representative cameras rather than forcing six unstable camera objects provides valid proof of design while honestly documenting the simulator limitation.

---

## 9. Security Posture at the End of Week 7

Week 7 deliberately ends with a functioning baseline rather than the final restricted state.

At this point:

- guest devices can obtain DHCP and route successfully
- facilities IoT devices can reach BMS-SRV1
- inter-VLAN routing remains broadly available
- access ports already use controls such as PortFast and BPDU Guard where appropriate
- unused switch ports from earlier phases remain assigned to VLAN 999 and administratively shut down

The remaining segmentation and hardening work is intentionally reserved for Week 8 so that security controls can be applied and validated against a known-good baseline.

---

## 10. Week 8 Final-Phase Objectives

The final week will focus on security hardening, verification, and presentation readiness.

Planned work includes:

- create a custom AVMC internal EHR/intranet landing page
- create a separate AVMC public-facing website
- validate public/edge connectivity
- restrict VLAN 70 guest access to internal AVMC networks
- preserve approved public/Internet access for guest users
- restrict MED-IOT and FACILITY communications according to function
- harden device management access
- apply additional Layer 2 controls where Packet Tracer supports them
- validate SSH/management restrictions
- build a formal allow/deny test matrix
- capture ACL counters and before/after evidence
- perform final end-to-end network validation
- clean up topology labels and presentation layout
- produce final portfolio and presentation artifacts

---

## 11. Week 7 Completion Statement

Week 7 completed the AVMC Facilities/BMS and Guest Wireless implementation at baseline. VLAN 80 now supports representative building-management, HVAC, physical-security, and camera devices. VLAN 70 now supports a realistic patient/visitor waiting-room environment with mixed BYOD endpoints and an emulated smart-TV endpoint.

The environment is now intentionally positioned for Week 8 security hardening. The next phase will transform the current functional baseline into a segmented and policy-enforced healthcare network while preserving evidence of the before-and-after behavior.
