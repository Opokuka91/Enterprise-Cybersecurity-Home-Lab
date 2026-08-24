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
