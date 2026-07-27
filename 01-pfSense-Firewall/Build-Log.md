## 2026-07-27 - Repository and Evidence Structure Created

Milestone:
Created the local GitHub repository and evidence folder structure for Lab 001 - pfSense Firewall.

Completed:
- Created Enterprise-Cybersecurity-Home-Lab repository folder.
- Created 01-pfSense-Firewall project folder.
- Created Evidence folders for screenshots, configuration backups, and snapshots.
- Initialized the folder as a Git repository.

Evidence:
- 001-Repository-Folder-Structure.png

Validation:
Repository folder structure exists and is ready for lab documentation.

## 2026-07-27 - Configured pfSense WAN Adapter

Milestone:
Configured Adapter 1 on PFSENSE-FW01 as the WAN interface.

Configuration:
- Adapter 1 enabled.
- Attached to NAT.
- Adapter type: Intel PRO/1000 MT Desktop.
- Cable connected enabled.

Purpose:
The WAN adapter provides upstream Internet access to pfSense through the VirtualBox NAT interface.

Evidence:
- 002-pfSense-Adapter1-WAN-NAT.png

Validation:
Adapter 1 is enabled and attached to NAT.

## 2026-07-27 - Configured pfSense LAN Adapter

Milestone:
Configured Adapter 2 on PFSENSE-FW01 as the LAN interface.

Configuration:
- Adapter 2 enabled.
- Attached to Internal Network.
- Internal network name: LAB-LAN.
- Cable connected enabled.

Purpose:
The LAN adapter creates the isolated enterprise network where future systems such as DC01, WIN11-CLIENT01, and KALI-ATTACK01 will connect.

Evidence:
- 003-pfSense-Adapter2-LAN-LAB-LAN.png

Validation:
Adapter 2 is enabled and attached to Internal Network named LAB-LAN.

## 2026-07-27 - Created Initial pfSense Network Snapshot

Milestone:
Created the first VirtualBox snapshot for PFSENSE-FW01 after configuring the firewall network adapters.

Snapshot:
PFSENSE-FW01-001-NetworkAdaptersConfigured

Snapshot Description:
pfSense VM created with 2 vCPUs, 2 GB RAM, 20 GB dynamic disk, Adapter 1 configured as NAT/WAN, and Adapter 2 configured as Internal Network/LAB-LAN. Ready for pfSense ISO attachment and installation.

Evidence:
- 004-pfSense-Snapshot-NetworkAdaptersConfigured.png

Validation:
Snapshot exists and captures the pre-installation baseline for PFSENSE-FW01.
