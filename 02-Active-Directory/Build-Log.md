# Build Log - Lab 002 Windows Server and Active Directory

## 2026-08-23 - Started Lab 002 Documentation Structure

Milestone:
Created the Lab 002 documentation and evidence structure before building the Windows Server VM.

Purpose:
Prepare a professional evidence trail for the Windows Server and Active Directory deployment.

Evidence:
- Evidence/Screenshots/001-Lab002-Folder-Structure-Created.png

Validation:
Lab 002 folder structure created locally and verified in File Explorer.

Snapshot:
None. No VM changes have been made yet.

Git:
Commit after the initial Lab 002 structure and first evidence checkpoint are verified.

## 2026-08-23 - Downloaded Windows Server Evaluation ISO

Milestone:
Downloaded the Windows Server evaluation ISO for the DC01 build.

Configuration:
- ISO location: C:\CyberLab\ISOs
- ISO filename: 26100.32230.260111-0550.lt_release_svc_refresh_SERVER_EVAL_x64FRE_en-us.iso
- ISO size: 7.59 GB

Purpose:
Prepare the Windows Server installation media required to create the first domain controller.

Evidence:
- Evidence/Screenshots/002-Windows-Server-ISO-Downloaded.png

Validation:
ISO file is visible in C:\CyberLab\ISOs.

Snapshot:
None. No VM changes have been made.

Git:
Commit after DC01 VM shell is created and documented.

## 2026-08-23 - Created DC01 Virtual Machine Shell

Milestone:
Created the DC01 virtual machine in VirtualBox.

Configuration:
- VM name: DC01
- VM folder: C:\CyberLab\Virtual Machines\DC01
- Operating system profile: Windows Server 2022 (64-bit)
- Installation media: Windows Server 2025 Standard Evaluation ISO
- Memory: 4096 MB
- CPUs: 2
- EFI: Enabled
- Virtual disk: 80 GB VDI
- Storage allocation: Dynamic

Purpose:
Provision the Windows Server VM that will become the first Active Directory domain controller.

Evidence:
- Evidence/Screenshots/003-DC01-VM-Creation-Name-and-ISO.png
- Evidence/Screenshots/004-DC01-Hardware-Configured.png
- Evidence/Screenshots/005-DC01-Virtual-Disk-Configured.png
- Evidence/Screenshots/006-DC01-VM-Created-VirtualBox-List.png

Validation:
DC01 appears in VirtualBox Manager and is powered off, ready for network configuration.

Snapshot:
None. Snapshot will be created after network settings are configured and verified.

Git:
Commit after DC01 network configuration is documented.

## 2026-08-23 - Configured DC01 Network Adapter

Milestone:
Configured DC01 Adapter 1 for the internal enterprise LAN.

Configuration:
- Adapter 1: Enabled
- Attached to: Internal Network
- Network name: LAB-LAN
- Adapter type: Intel PRO/1000 MT Desktop (82540EM)
- Promiscuous mode: Deny
- Virtual cable: Connected

Purpose:
Connect DC01 to the protected enterprise LAN behind pfSense so it can later provide Active Directory and DNS services to lab clients.

Evidence:
- Evidence/Screenshots/007-DC01-Network-Adapter-LAB-LAN.png

Validation:
Adapter 1 is attached to LAB-LAN and the virtual cable is connected.

Snapshot:
Created snapshot `DC01-001-VMCreated-NetworkConfigured` before starting the Windows Server installation.

Git:
Commit after the baseline snapshot evidence is captured.

## 2026-08-23 - Captured DC01 Baseline Snapshot

Milestone:
Captured the first DC01 snapshot after VM creation and network configuration.

Snapshot:
- Snapshot name: DC01-001-VMCreated-NetworkConfigured

Purpose:
Create a clean rollback point before installing Windows Server.

Evidence:
- Evidence/Screenshots/008-DC01-Snapshot-VMCreated-NetworkConfigured.png

Validation:
Snapshot is visible in VirtualBox Manager and DC01 remains powered off.

Git:
Commit this DC01 baseline checkpoint locally before starting the operating system installation.

## 2026-08-23 - Installed Windows Server on DC01

Milestone:
Installed Windows Server 2025 Standard Evaluation with Desktop Experience on DC01.

Configuration:
- Edition: Windows Server 2025 Standard Evaluation (Desktop Experience)
- Install type: Clean installation
- Target disk: Disk 0, 80 GB
- Local account: Administrator

Purpose:
Install the base Windows Server operating system before configuring server identity, static networking, and Active Directory Domain Services.

Evidence:
- Evidence/Screenshots/009-Windows-Server-Setup-Started.png
- Evidence/Screenshots/010-Windows-Server-Edition-Selection.png
- Evidence/Screenshots/011-Windows-Server-Disk-Selection.png
- Evidence/Screenshots/012-Windows-Server-Ready-To-Install.png
- Evidence/Screenshots/013-Windows-Server-Installation-Progress.png
- Evidence/Screenshots/014-Windows-Server-Administrator-Password-Screen.png
- Evidence/Screenshots/015-Windows-Server-Installed-Lock-Screen.png
- Evidence/Screenshots/016-Windows-Server-First-Login-Server-Manager.png

Validation:
DC01 booted successfully after installation and Server Manager opened at first login.

Snapshot:
Pending first-login and network validation.

Git:
Commit after Windows Server installation, network validation, and baseline snapshot are captured.

## 2026-08-23 - Validated Initial DC01 Network Connectivity

Milestone:
Validated that DC01 received network configuration from pfSense and could reach the gateway, Internet, and DNS.

Observed Configuration:
- DHCP IPv4 address: 10.10.10.101
- Subnet mask: 255.255.255.0
- Default gateway: 10.10.10.1
- DNS suffix: home.arpa

Validation:
- Ping 10.10.10.1 passed with 0 percent packet loss.
- Ping 8.8.8.8 passed with 0 percent packet loss.
- Ping google.com passed with 0 percent packet loss.

Evidence:
- Evidence/Screenshots/017-DC01-Initial-IPConfig-DHCP.png
- Evidence/Screenshots/018-DC01-Internet-DNS-Ping-Validation.png
- Evidence/Screenshots/019-DC01-Gateway-Ping-Validation.png

Snapshot:
Created snapshot `DC01-002-WindowsServerInstalled-NetworkValidated` before assigning a static IP address.

Git:
Commit after the post-install snapshot evidence is captured.

## 2026-08-23 - Captured DC01 Post-Install Snapshot

Milestone:
Captured a DC01 snapshot after Windows Server installation and initial network validation.

Snapshot:
- Snapshot name: DC01-002-WindowsServerInstalled-NetworkValidated

Purpose:
Create a recovery point before changing DC01 from DHCP to static addressing.

Evidence:
- Evidence/Screenshots/020-DC01-Snapshot-WindowsServerInstalled-NetworkValidated.png

Validation:
Snapshot is visible in VirtualBox Manager after Windows Server installation and network testing.

Git:
Commit this Windows Server installation checkpoint locally.

## 2026-08-30 - Configured DC01 Static IPv4 Address

Milestone:
Changed DC01 from a pfSense DHCP lease to a planned static IPv4 address.

Configuration:
- IPv4 address: 10.10.10.10
- Subnet mask: 255.255.255.0
- Default gateway: 10.10.10.1
- DNS server: 10.10.10.1
- DHCP enabled: No
- Current Windows hostname: WIN-SV3LHDQESMT

Purpose:
Assign DC01 a stable server address before installing Active Directory Domain Services and DNS.

Evidence:
- Evidence/Screenshots/021-pfSense-Pre-Static-IP-Verification.png
- Evidence/Screenshots/022-DC01-Logged-In-Before-Static-IP.png
- Evidence/Screenshots/023-DC01-Network-Connections-Opened.png
- Evidence/Screenshots/024-DC01-IPv4-Properties-Before-Static-IP.png
- Evidence/Screenshots/025-DC01-IPv4-Static-IP-Entered-Before-Apply.png
- Evidence/Screenshots/026-DC01-Static-IPConfig-Verified.png
- Evidence/Screenshots/026A-DC01-Static-IPConfig-All-Start.png
- Evidence/Screenshots/026B-DC01-Static-IPConfig-All-Hostname.png
- Evidence/Screenshots/026C-DC01-Static-IPConfig-All-DNS-Verified.png

Validation:
Static IPv4 configuration is visible in ipconfig and ipconfig /all. Gateway, Internet, and DNS ping validation passed through pfSense.

Snapshot:
Created snapshot `DC01-003-StaticIPValidated` after DC01 was cleanly shut down.

Git:
Commit after static IP validation evidence and snapshot evidence are captured.

## 2026-08-30 - Captured DC01 Static IP Snapshot

Milestone:
Captured a DC01 recovery snapshot after static IPv4 addressing and connectivity validation were completed.

Snapshot:
- Snapshot name: DC01-003-StaticIPValidated

Purpose:
Create a rollback point before renaming the Windows Server hostname and installing Active Directory Domain Services.

Evidence:
- Evidence/Screenshots/028-DC01-Snapshot-StaticIPValidated.png

Validation:
Snapshot is visible in VirtualBox Manager and DC01 is powered off.

Git:
Commit and push this static IP validation milestone to GitHub.

## 2026-08-30 - Renamed Windows Server Hostname to DC01

Milestone:
Renamed the Windows Server computer name from the default installer-generated hostname to DC01.

Configuration:
- Previous hostname: WIN-SV3LHDQESMT
- New hostname: DC01
- IPv4 address: 10.10.10.10/24
- Default gateway: 10.10.10.1
- Temporary DNS server: 10.10.10.1

Purpose:
Set the server identity before installing Active Directory Domain Services. A domain controller should have a clear, stable hostname before promotion because the name becomes part of DNS records, management tools, logs, documentation, and troubleshooting workflows.

Evidence:
- Evidence/Screenshots/029-DC01-Computer-Name-Changed-Before-Restart.png
- Evidence/Screenshots/030-DC01-Hostname-Rename-Validated.png
- Evidence/Screenshots/030A-DC01-Rename-Ping-Gateway-Internet-Partial.png
- Evidence/Screenshots/030B-DC01-Rename-DNS-Ping-Validated.png

Validation:
The hostname command returned DC01 after reboot. Gateway, Internet, and DNS ping validation passed after the rename.

Snapshot:
Created snapshot `DC01-004-Renamed-StaticIPValidated` after hostname and network validation.

Git:
Commit and push this hostname rename milestone to GitHub.

## 2026-08-30 - Captured DC01 Hostname Rename Snapshot

Milestone:
Captured a recovery snapshot after DC01 was renamed and validated.

Snapshot:
- Snapshot name: DC01-004-Renamed-StaticIPValidated

Purpose:
Create a rollback point before installing the Active Directory Domain Services role and promoting the server to a domain controller.

Evidence:
- Evidence/Screenshots/031-DC01-Snapshot-Renamed-StaticIPValidated.png

Validation:
Snapshot is visible in VirtualBox Manager and DC01 is powered off.

Git:
Commit and push this pre-Active Directory checkpoint.
