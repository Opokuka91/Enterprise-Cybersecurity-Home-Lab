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

## 2026-07-27 - Downloaded pfSense Installer

Milestone:
Downloaded the Netgate/pfSense installer for PFSENSE-FW01.

Purpose:
The installer will be used to install pfSense as the enterprise firewall operating system.

Installer File:
netgate-installer-v1.2-RELEASE-amd64.iso

Evidence:
- 005-pfSense-ISO-Downloaded.png

Validation:
pfSense installer file is stored in C:\CyberLab\ISOs.

## 2026-07-27 - Attached pfSense Installer ISO

Milestone:
Attached the Netgate/pfSense installer ISO to PFSENSE-FW01.

Configuration:
- ISO attached: netgate-installer-v1.2-RELEASE-amd64.iso
- VM: PFSENSE-FW01

Purpose:
This prepares the VM to boot into the pfSense installer.

Evidence:
- 006-pfSense-ISO-Attached.png

Validation:
VirtualBox Storage settings show the Netgate installer ISO attached to PFSENSE-FW01.

## 2026-07-27 - Booted pfSense Installer

Milestone:
Started PFSENSE-FW01 and booted into the Netgate/pfSense installer.

Purpose:
This confirms that the VM can boot from the attached installer ISO.

Evidence:
- 007-pfSense-Installer-Boot-Screen.png

Validation:
The Netgate/pfSense installer boot screen appears successfully and no boot device error appears.

## 2026-07-27 - Accepted Installer Notice

Milestone:
Accepted the Netgate installer copyright and distribution notice.

Purpose:
This allowed the installation workflow to continue.

Evidence:
- 008-pfSense-Install-Menu.png

Validation:
Installer advanced to the pfSense installation menu.

## 2026-07-27 - Started pfSense Installation Workflow

Milestone:
Selected Install pfSense from the installer menu.

Purpose:
This begins the pfSense firewall operating system installation process.

Evidence:
- 009-pfSense-Install-Target-Selection.png

Validation:
Installer advanced to the next installation configuration screen.

## 2026-07-27 - Reviewed WAN Network Mode Setup

Milestone:
Reviewed the WAN interface network mode settings during pfSense installation.

Configuration:
- WAN interface: em0
- Interface mode: DHCP client
- VLAN tagging: disabled
- Use local resolver: false

Purpose:
The WAN interface will receive an upstream address from VirtualBox NAT, which represents the outside network for this lab firewall.

Evidence:
- 010-pfSense-WAN-Network-Mode-Setup.png

Validation:
WAN network mode settings match the planned VirtualBox NAT design.

## 2026-07-27 - Detected Unassigned LAN Interface

Milestone:
Reached the interface assignment confirmation screen and identified that the LAN interface was not assigned.

Issue:
The installer detected WAN as em0, but LAN was listed as not assigned.

Purpose:
pfSense requires both WAN and LAN interfaces for this enterprise firewall design. WAN represents the outside network, and LAN represents the trusted internal lab network.

Evidence:
- 011-pfSense-Interface-Assignment-LAN-Not-Assigned.png

Validation:
Installation paused before continuing so the LAN interface can be assigned correctly.

## 2026-07-27 - Reviewed Default LAN Interface Settings

Milestone:
Assigned LAN to em1 and reviewed the default LAN network settings.

Default Configuration Observed:
- LAN interface: em1
- Interface mode: Static
- IP address: 192.168.1.1/24
- DHCP enabled: true
- DHCP range: 192.168.1.100 - 192.168.1.199

Purpose:
The LAN interface must use the planned enterprise lab subnet before installation continues.

Evidence:
- 012-pfSense-LAN-em1-Default-Settings.png

Validation:
LAN is assigned to em1, but the default subnet must be changed to 10.10.10.1/24 for the lab design.

## 2026-07-27 - Configured pfSense LAN Subnet

Milestone:
Configured the pfSense LAN interface with the planned enterprise lab subnet.

Configuration:
- LAN interface: em1
- Interface mode: Static
- LAN IP address: 10.10.10.1/24
- DHCP enabled: true
- DHCP range start: 10.10.10.100
- DHCP range end: 10.10.10.199

Purpose:
The 10.10.10.0/24 subnet separates the cybersecurity lab network from the home network and provides a clean enterprise-style internal address space.

Evidence:
- 013-pfSense-LAN-Configured-10-10-10.png

Validation:
LAN interface settings match the planned lab network design.

## 2026-07-27 - Confirmed Correct Interface Assignment

Milestone:
Confirmed the corrected pfSense interface assignment before continuing installation.

Configuration:
- WAN: em0
- LAN: em1

Issue Resolved:
The installer previously showed LAN as not assigned. After using Assign/Configure, LAN was correctly mapped to em1.

Evidence:
- 014-pfSense-Interface-Assignment-Corrected.png

Validation:
Both firewall interfaces are active and assigned to the correct roles.

## 2026-07-27 - Started Installer Connectivity Check

Milestone:
Started the Netgate installer Internet connectivity check.

Purpose:
The installer verifies that the WAN interface can reach Netgate servers through the VirtualBox NAT connection.

Evidence:
- 015-pfSense-Connectivity-Check.png

Validation:
Connectivity check started after WAN and LAN interfaces were correctly assigned.

## 2026-07-27 - Selected pfSense Community Edition Path

Milestone:
Reached the subscription validation screen and selected the Community Edition installation path.

Purpose:
pfSense Community Edition is the free edition appropriate for this home lab and portfolio project.

Evidence:
- 016-pfSense-Install-CE-Selection.png

Validation:
Installer reached the pfSense CE selection screen after completing the online validation step.

## 2026-07-27 - Reviewed Installation Storage Options

Milestone:
Reviewed the pfSense installation options for file system and partition scheme.

Configuration:
- File system: ZFS
- Partition scheme: GPT compatible with MBR

Purpose:
ZFS is the recommended default for the installer and GPT is appropriate for a modern VM deployment.

Evidence:
- 017-pfSense-Installation-Options-ZFS-GPT.png

Validation:
Installation options match the recommended default settings.

## 2026-07-27 - Selected ZFS Stripe Layout

Milestone:
Selected the ZFS virtual device layout for the pfSense installation.

Configuration:
- ZFS virtual device type: Stripe
- Redundancy: None
- Disk count: 1 virtual disk

Purpose:
The lab VM uses a single virtual disk, so stripe/no redundancy is the appropriate layout. Redundancy would require multiple disks and is outside the scope of this first firewall build.

Evidence:
- 018-pfSense-ZFS-Stripe-No-Redundancy.png

Validation:
Selected storage layout matches the VM disk design.

## 2026-07-27 - Selected pfSense Installation Disk

Milestone:
Selected the target virtual disk for pfSense installation.

Configuration:
- Disk selected: ada0
- Disk size: 20 GB
- Disk type: VirtualBox hard disk
- File system: ZFS
- Partition scheme: GPT

Purpose:
The selected virtual disk is the dedicated 20 GB disk created for PFSENSE-FW01.

Evidence:
- 019-pfSense-Disk-Selection.png

Validation:
Installer shows the 20 GB VirtualBox hard disk selected for installation.

## 2026-07-27 - Confirmed pfSense Virtual Disk Erase Prompt

Milestone:
Reached the final disk erase confirmation prompt before installing pfSense.

Target Disk:
- ada0

Purpose:
The installer requires confirmation before formatting the selected virtual disk and installing pfSense.

Evidence:
- 020-pfSense-Disk-Erase-Confirmation.png

Validation:
The confirmation prompt targets only the selected VirtualBox disk ada0.

## 2026-07-27 - Selected pfSense CE Version

Milestone:
Selected the pfSense Community Edition version to install.

Configuration:
- Selected version: pfSense CE 2.8.1
- Release channel: Current Stable Version

Purpose:
Installing the current stable version provides the latest supported Community Edition features and fixes for the home lab firewall.

Evidence:
- 021-pfSense-Version-Selection-2-8-1.png

Validation:
Installer shows pfSense CE 2.8.1 selected as the current stable version.

## 2026-07-27 - Began pfSense Installation

Milestone:
Started the pfSense CE 2.8.1 installation process.

Installation Details:
- Package: pfSense-base 2.8.1
- Download size: 103 MiB
- Additional required space: 104 MiB

Purpose:
This installs the pfSense firewall operating system onto the selected 20 GB virtual disk.

Evidence:
- 022-pfSense-Installation-Progress.png

Validation:
Installer is actively downloading and installing pfSense CE 2.8.1 packages.

## 2026-07-27 - Completed pfSense Installation

Milestone:
Completed pfSense CE 2.8.1 installation and post-installation setup.

Installation Result:
- pfSense post-installation setup completed.
- Network settings exported to pfSense.

Purpose:
This confirms the firewall operating system was installed onto the virtual disk and is ready for first boot.

Evidence:
- 023-pfSense-Installation-Complete.png

Validation:
Installer reports pfSense post-installation setup is done.

## 2026-07-27 - Detached pfSense Installer ISO

Milestone:
Removed the Netgate installer ISO from the PFSENSE-FW01 virtual optical drive after installation.

Issue:
After installation, the VM rebooted back into the installer because the ISO was still attached.

Resolution:
Powered off PFSENSE-FW01 and removed the installer ISO from the virtual optical drive.

Purpose:
Detaching the ISO allows the VM to boot from the installed pfSense virtual hard disk.

Evidence:
- 024-pfSense-ISO-Detached.png

Validation:
VirtualBox Storage settings show the virtual optical drive as Empty.

## 2026-07-27 - Verified pfSense First Boot

Milestone:
Booted PFSENSE-FW01 from the installed virtual hard disk and reached the pfSense console menu.

Configuration Verified:
- pfSense version: 2.8.1-RELEASE amd64
- WAN: em0
- WAN IPv4: 10.0.2.15/24
- LAN: em1
- LAN IPv4: 10.10.10.1/24

Purpose:
This confirms the base firewall installation is complete and both interfaces are active with the expected addressing.

Evidence:
- 025-pfSense-First-Boot-Console.png

Validation:
pfSense console menu loaded successfully from the installed disk.

## 2026-07-27 - Validated WAN Internet Connectivity

Milestone:
Tested pfSense WAN connectivity by pinging a public IP address from the pfSense console.

Test:
- Console option: 7) Ping host
- Target: 8.8.8.8
- Packets transmitted: 3
- Packets received: 3
- Packet loss: 0.0%

Purpose:
This confirms PFSENSE-FW01 can reach the Internet through the VirtualBox NAT WAN interface.

Evidence:
- 026-pfSense-WAN-Ping-8-8-8-8.png

Validation:
WAN connectivity test succeeded with 0.0% packet loss.

## 2026-07-27 - Validated DNS Resolution

Milestone:
Tested DNS resolution and Internet reachability by pinging a domain name from the pfSense console.

Test:
- Console option: 7) Ping host
- Target: google.com
- Resolved IP: 173.194.208.100
- Packets transmitted: 3
- Packets received: 3
- Packet loss: 0.0%

Purpose:
This confirms PFSENSE-FW01 can resolve DNS names and reach external hosts through the WAN interface.

Evidence:
- 027-pfSense-DNS-Ping-google-com.png

Validation:
DNS resolution and external connectivity test succeeded with 0.0% packet loss.

## 2026-07-27 - Created Base Install Snapshot

Milestone:
Created the post-installation VirtualBox snapshot for PFSENSE-FW01.

Snapshot:
PFSENSE-FW01-002-BaseInstallComplete

Snapshot Description:
pfSense CE 2.8.1 installed successfully. ISO detached. First boot verified. WAN em0 received 10.0.2.15/24 via VirtualBox NAT. LAN em1 configured as 10.10.10.1/24. WAN ping to 8.8.8.8 passed. DNS ping to google.com passed. Console menu loaded successfully.

Purpose:
This snapshot preserves a clean, validated pfSense base installation before additional firewall configuration and client testing.

Evidence:
- 028-pfSense-Snapshot-BaseInstallComplete.png

Validation:
Snapshot exists and captures the verified base install state.
## 2026-07-27 - Attached pfSense Installer ISO

Milestone:
Attached the Netgate/pfSense installer ISO to PFSENSE-FW01.

Configuration:
- ISO attached: netgate-installer-v1.2-RELEASE-amd64.iso
- VM: PFSENSE-FW01

Purpose:
This prepares the VM to boot into the pfSense installer.

Evidence:
- 006-pfSense-ISO-Attached.png

Validation:
VirtualBox Storage settings show the Netgate installer ISO attached to PFSENSE-FW01.

## 2026-07-27 - Booted pfSense Installer

Milestone:
Started PFSENSE-FW01 and booted into the Netgate/pfSense installer.

Purpose:
This confirms that the VM can boot from the attached installer ISO.

Evidence:
- 007-pfSense-Installer-Boot-Screen.png

Validation:
The Netgate/pfSense installer boot screen appears successfully.

## 2026-07-27 - Accepted Installer Notice

Milestone:
Accepted the Netgate installer copyright and distribution notice.

Purpose:
This allowed the installation workflow to continue.

Evidence:
- 008-pfSense-Install-Menu.png

Validation:
Installer advanced to the next installation menu.

## 2026-07-27 - Started pfSense Installation Workflow

Milestone:
Selected Install pfSense from the installer menu.

Purpose:
This begins the pfSense firewall operating system installation process.

Evidence:
- 009-pfSense-Install-Target-Selection.png

Validation:
Installer advanced to the next installation configuration screen.

## 2026-08-09 - Validated pfSense Console Session

Milestone:
Confirmed that PFSENSE-FW01 was still running and reachable at the pfSense console after the base installation snapshot.

Purpose:
This validates that the firewall VM remained in a usable post-install state before connecting the Windows 11 lab client to the LAN side.

Evidence:
- 029-pfSense-Console-Session-Validation.png

Validation:
pfSense console session loaded successfully and showed the firewall ready for continued lab testing.

## 2026-08-09 - Confirmed Windows 11 Lab Adapter on LAB-LAN

Milestone:
Confirmed the KAO-Tech-Windows11-Lab virtual machine network adapter was assigned to the LAB-LAN internal network.

Configuration:
- VM: KAO-Tech-Windows11-Lab
- Adapter 1: Internal Network
- Internal network name: LAB-LAN

Purpose:
This places the Windows 11 lab client on the same internal network as the pfSense LAN interface so DHCP can be tested.

Evidence:
- 030-Windows11-Adapter1-LAB-LAN.png

Validation:
VirtualBox network settings showed Adapter 1 attached to LAB-LAN.

## 2026-08-09 - Started Windows 11 Lab Client Installation

Milestone:
Started installation of the KAO-Tech-Windows11-Lab virtual machine.

Configuration:
- VM: KAO-Tech-Windows11-Lab
- Adapter 1: Internal Network
- Internal network name: LAB-LAN
- Connected firewall LAN: PFSENSE-FW01 em1 / 10.10.10.1/24
- Virtual disk selected for install: Disk 0 Unallocated Space, 80.0 GB

Purpose:
This creates the Windows 11 client VM that will be used to test pfSense LAN DHCP, default gateway assignment, and client internet access through the firewall.

Evidence:
- 031-Windows11-DHCP-Address.png

Validation:
Passed. KAO-Tech-Windows11-Lab received IPv4 address 10.10.10.100/24 from the pfSense LAN network, with default gateway 10.10.10.1 and DNS suffix home.arpa.

## 2026-08-09 - Validated Windows 11 Client Internet and DNS Connectivity

Milestone:
Confirmed that KAO-Tech-Windows11-Lab can reach the internet through the pfSense firewall and resolve external DNS names.

Tests:
- ping 8.8.8.8
- ping google.com

Purpose:
This validates that the Windows 11 lab client can route outbound traffic through PFSENSE-FW01 and that DNS resolution works from the client network.

Evidence:
- 032-Windows11-Internet-DNS-Ping.png

Validation:
Passed. Ping to 8.8.8.8 returned 4 sent, 4 received, 0 lost. Ping to google.com resolved to 142.250.138.113 and returned 4 sent, 4 received, 0 lost.

## 2026-08-09 - Created Windows 11 Base Install Snapshot

Milestone:
Created the post-installation VirtualBox snapshot for KAO-Tech-Windows11-Lab.

Snapshot:
KAO-W11-LAB01-001-BaseInstall-DHCPValidated

Snapshot Description:
Windows 11 lab client installed successfully. Local user KAOAdmin created. Adapter 1 connected to LAB-LAN. DHCP from pfSense validated with IP 10.10.10.100/24, gateway 10.10.10.1, and DNS suffix home.arpa. Internet and DNS connectivity confirmed through pfSense.

Purpose:
This snapshot preserves a clean, validated Windows 11 lab client before additional hardening, tools installation, or Active Directory/domain configuration work.

Evidence:
- 033-Windows11-Snapshot-BaseInstall-DHCPValidated.png

Validation:
Snapshot exists in VirtualBox and captures the verified Windows 11 client base state.
