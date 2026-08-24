# Host Maintenance Log

## 2026-08-23 - Verified VirtualBox Upgrade

Milestone:
Verified Oracle VirtualBox after winget upgrade.

Configuration:
- VirtualBox version: 7.2.16 r174877
- Qt version: 6.8.0
- Host OS: Windows

Purpose:
Confirm the virtualization platform version before starting Lab 002 - Windows Server / Active Directory.

Evidence:
- Evidence/Screenshots/001-VirtualBox-7-2-16-Upgrade-Verified.png

Validation:
VirtualBox graphical interface opened successfully and displayed version 7.2.16.

## 2026-08-23 - Checked VirtualBox Extension Pack

Milestone:
Checked the installed Oracle VirtualBox Extension Pack after upgrading VirtualBox.

Configuration:
- VirtualBox application version: 7.2.16 r174877
- Extension Pack installed: Yes
- Extension Pack version observed: requires verification against 7.2.16

Purpose:
Confirm the Extension Pack matches the installed VirtualBox version before starting Lab 002 - Windows Server / Active Directory.

Evidence:
- Evidence/Screenshots/002-VirtualBox-Extension-Pack-7-2-16-Delete-Prompt.png
- Evidence/Screenshots/003-VirtualBox-Extension-Pack-Version-Check.png

Validation:
Extension Pack Manager opened successfully. Version should be corrected if it does not match VirtualBox 7.2.16.

## 2026-08-23 - Installed Matching VirtualBox Extension Pack

Milestone:
Installed the Oracle VirtualBox Extension Pack matching the upgraded VirtualBox version.

Configuration:
- VirtualBox application version: 7.2.16 r174877
- Extension Pack version: 7.2.16 r174877
- Extension Pack status: Active

Purpose:
Ensure VirtualBox host features are aligned before continuing to Lab 002 - Windows Server / Active Directory.

Evidence:
- Evidence/Screenshots/004-VirtualBox-Extension-Pack-License-Prompt.png
- Evidence/Screenshots/005-VirtualBox-Extension-Pack-7-2-16-Verified.png

Validation:
Extension Pack Manager shows Oracle VirtualBox Extension Pack active with version 7.2.16 r174877.

## 2026-08-23 - Verified pfSense Boot After VirtualBox Upgrade

Milestone:
Started PFSENSE-FW01 after upgrading VirtualBox and installing the matching Extension Pack.

Observed Configuration:
- pfSense version: 2.8.1-RELEASE amd64
- WAN interface: em0
- WAN IPv4 address: 10.0.2.15/24
- LAN interface: em1
- LAN IPv4 address: 10.10.10.1/24

Purpose:
Confirm the firewall still boots correctly after VirtualBox host maintenance before starting Lab 002.

Evidence:
- Evidence/Screenshots/006-pfSense-Post-VirtualBox-Upgrade-Boot-Check.png

Validation:
pfSense booted to the console menu successfully with the expected WAN and LAN addresses.

## 2026-08-23 - Captured Post-Upgrade Windows Client Snapshot

Milestone:
Created a stable VirtualBox snapshot after confirming the Windows 11 lab client worked through pfSense following the VirtualBox upgrade.

Snapshot:
- VM: KAO-Tech-Windows11-Lab
- Snapshot name: KAO-W11-LAB01-002-PostUpgradeNetworkValidated

Purpose:
Create a recovery point after confirming the client network was restored and validated.

Evidence:
- Evidence/Screenshots/007-Windows11-Post-VirtualBox-Upgrade-Boot-Check.png
- Evidence/Screenshots/012-Windows11-DHCP-and-Ping-Validation-After-pfSense-Restart.png
- Evidence/Screenshots/013-Windows11-PostUpgradeNetworkValidated-Snapshot.png

Validation:
Windows 11 client validated Internet and DNS connectivity through pfSense, then a post-upgrade snapshot was captured.
