[README.md](https://github.com/user-attachments/files/32981157/README.md)
# Week 7 Image Evidence

This folder contains a curated set of Week 7 screenshots selected for GitHub / portfolio use. Credential-revealing screenshots were intentionally excluded.

## Included Images

### 01-week7-topology-overview.png
Overall AVMC Packet Tracer topology showing the expanded Facilities/BMS area and guest waiting-room device cluster.

### 02-guest-laptop-ip-details.png
Guest laptop IP information showing VLAN 70 DHCP configuration, gateway, and DNS without exposing the wireless pre-shared key.

### 03-guest-laptop-gateway-ping.png
`GUEST-LAPTOP1` successfully pinging `10.40.70.1` with 0% packet loss, validating the guest WLAN-to-gateway path.

### 04-guest-tablet-internal-baseline-ping.png
Guest tablet successfully reaching `10.40.50.2` before ACL hardening. This serves as important pre-security baseline evidence for the Week 8 guest-isolation tests.

### 05-waiting-room-tv-network-details.png
`WAITING-ROOM-TV1` network details showing that the custom smart-TV simulation is a real VLAN 70 endpoint.

## Screenshots Deliberately Not Included

Some configuration screenshots visibly contained wireless pre-shared keys or IoT registration credentials. Those images should not be committed to a public repository.

## Suggested GitHub Usage

A clean portfolio sequence would be:

1. topology overview
2. guest DHCP / gateway details
3. successful gateway ping
4. successful pre-ACL internal ping
5. custom smart-TV endpoint details

This creates a clear story from design -> addressing -> connectivity -> baseline security condition.
