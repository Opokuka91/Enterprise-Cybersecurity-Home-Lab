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

## 2026-08-30 - Installed Active Directory Domain Services Role

Milestone:
Installed the Active Directory Domain Services role and required management tools on DC01.

Configuration:
- Server: DC01
- Role installed: Active Directory Domain Services
- Additional tools installed: Group Policy Management and AD DS administrative tools

Purpose:
Prepare DC01 to become the first domain controller for the enterprise home lab.

Evidence:
- Evidence/Screenshots/032-ADDS-Add-Roles-And-Features-Started.png
- Evidence/Screenshots/033-ADDS-Installation-Type-Selected.png
- Evidence/Screenshots/034-ADDS-Server-Selection-DC01.png
- Evidence/Screenshots/035-ADDS-Server-Role-Selected.png
- Evidence/Screenshots/036-ADDS-Features-Defaults.png
- Evidence/Screenshots/037-ADDS-Confirmation-Before-Install.png
- Evidence/Screenshots/038A-ADDS-Role-Installation-Progress.png
- Evidence/Screenshots/038-ADDS-Role-Installation-Succeeded.png

Validation:
Role installation completed successfully and Server Manager displayed the option to promote the server to a domain controller.

Snapshot:
None. Snapshot was deferred until domain controller promotion and DNS validation completed.

Git:
Commit after promotion, troubleshooting documentation, and final validation are captured.

## 2026-08-30 - Promoted DC01 to Domain Controller

Milestone:
Promoted DC01 as the first domain controller for the new Active Directory forest.

Configuration:
- Deployment operation: Add a new forest
- Root domain name: kaotech.home.arpa
- NetBIOS domain name: KAOTECH
- Forest functional level: Windows Server 2025
- Domain functional level: Windows Server 2025
- DNS Server role: Enabled
- Global Catalog: Enabled
- DNS delegation: Not created
- Database folder: C:\WINDOWS\NTDS
- Log files folder: C:\WINDOWS\NTDS
- SYSVOL folder: C:\WINDOWS\SYSVOL

Purpose:
Create centralized identity, authentication, DNS, and Group Policy infrastructure for the enterprise lab.

Evidence:
- Evidence/Screenshots/039-ADDS-Promotion-Deployment-Configuration.png
- Evidence/Screenshots/040-ADDS-New-Forest-Domain-Entered.png
- Evidence/Screenshots/041-ADDS-Domain-Controller-Options.png
- Evidence/Screenshots/042A-ADDS-DNS-Options-Delegation-Checked-Before-Correction.png
- Evidence/Screenshots/042-ADDS-DNS-Options-No-Delegation.png
- Evidence/Screenshots/043-ADDS-NetBIOS-Domain-Name.png
- Evidence/Screenshots/044-ADDS-Default-Paths.png
- Evidence/Screenshots/045-ADDS-Review-Options.png
- Evidence/Screenshots/046-ADDS-Prerequisites-Check-Passed.png
- Evidence/Screenshots/047-ADDS-Domain-Controller-Promotion-Complete.png
- Evidence/Screenshots/047A-ADDS-Promotion-Domain-Login-After-Reset.png
- Evidence/Screenshots/048A-ADDS-Post-Promotion-Whoami-Validation.png
- Evidence/Screenshots/048-ADDS-Post-Promotion-Identity-Network-Validation.png
- Evidence/Screenshots/049A-ADDS-Post-Promotion-IPConfig-Confirmed.png

Validation:
DC01 rebooted after promotion. Login changed to the KAOTECH domain context and `whoami` returned `kaotech\administrator`.

Snapshot:
Deferred until AD DNS validation passed.

Git:
Commit after DNS issue resolution, snapshot evidence, and documentation update.

## 2026-08-30 - Resolved AD DNS SRV Record Registration

Milestone:
Resolved an initial `dcdiag /test:Connectivity` failure caused by missing or delayed AD DNS service record registration.

Issue:
`dcdiag` could not resolve an `_msdcs.kaotech.home.arpa` record and reported that DC01 failed the Connectivity test.

Resolution:
- Flushed the DNS resolver cache.
- Initiated DNS record registration.
- Restarted the Netlogon service.
- Ran `nltest /dsregdns` to force domain controller DNS registration.
- Re-ran SRV record lookup and `dcdiag /test:Connectivity`.

Evidence:
- Evidence/Screenshots/049B-ADDS-DCDIAG-Connectivity-Failed.png
- Evidence/Screenshots/049C-ADDS-DCDIAG-Connectivity-Failure-Details.png
- Evidence/Screenshots/050A-ADDS-DNS-Flush-Register-Netlogon-Stop.png
- Evidence/Screenshots/050B-ADDS-Netlogon-Started-NLTest-DSRegDNS-Success.png
- Evidence/Screenshots/051A-ADDS-SRV-Record-Validation-Passed.png
- Evidence/Screenshots/051B-ADDS-DCDIAG-Connectivity-Passed.png

Validation:
The `_ldap._tcp.dc._msdcs.kaotech.home.arpa` SRV record resolved to `dc01.kaotech.home.arpa`, and `dcdiag /test:Connectivity` passed.

Snapshot:
Created snapshot `DC01-005-ADDS-Promoted-DNSValidated` after shutting down DC01 cleanly.

Git:
Commit and push this AD DS promotion and DNS validation milestone.

## 2026-08-30 - Captured DC01 AD DS Promotion Snapshot

Milestone:
Captured a recovery snapshot after DC01 was promoted and AD DNS validation passed.

Snapshot:
- Snapshot name: DC01-005-ADDS-Promoted-DNSValidated

Purpose:
Create a rollback point before joining the Windows 11 client to the new Active Directory domain.

Evidence:
- Evidence/Screenshots/052-DC01-Snapshot-ADDS-Promoted-DNSValidated.png

Validation:
Snapshot is visible in VirtualBox Manager and DC01 is powered off.

Git:
Commit and push this completed Active Directory promotion checkpoint.

## 2026-11-15 - Started pfSense for the Windows 11 domain join

Started PFSENSE-FW01 and verified that the console displayed LAN IPv4 10.10.10.1/24 before starting DC01.

Evidence: [pfSense LAN interface](Evidence/Screenshots/053-pfSense-LAN-Ready-for-Domain-Join.png)

### DC01 readiness before client startup

DC01 passed `dcdiag /test:Connectivity`. A direct DNS query to 10.10.10.10 for `_ldap._tcp.dc._msdcs.kaotech.home.arpa` returned dc01.kaotech.home.arpa on LDAP port 389 with IPv4 address 10.10.10.10.

Evidence: [DC01 connectivity and LDAP SRV lookup](Evidence/Screenshots/054-DC01-PreJoin-AD-DNS-Ready.png)

### Windows 11 network before the join

KAO-W11-LAB01 was in WORKGROUP. Ethernet had IPv4 address 10.10.10.100 and used 10.10.10.1 for both its default gateway and DNS.

Evidence: [055-Windows11-PreJoin-Network.png](Evidence/Screenshots/055-Windows11-PreJoin-Network.png)

Changed Ethernet DNS to 10.10.10.10 and verified the configured IPv4 resolver. Both the gateway and DC01 answered ICMP. The client resolved the domain LDAP SRV record to dc01.kaotech.home.arpa on port 389, with IPv4 address 10.10.10.10.

Evidence: [056-Windows11-AD-DNS-and-Connectivity.png](Evidence/Screenshots/056-Windows11-AD-DNS-and-Connectivity.png)

### Windows 11 domain join

The first Add-Computer attempt returned an incorrect username or password error. The retry for KAO-W11-LAB01 returned HasSucceeded=True and requested a restart to apply membership in kaotech.home.arpa.

Evidence: [Domain join results](Evidence/Screenshots/057-Windows11-Domain-Join-Result.png)

### Verified Windows 11 domain sign-in and trust

On KAO-W11-LAB01, whoami returned kaotech\administrator. Domain membership and Test-ComputerSecureChannel both returned True for kaotech.home.arpa. DC01 resolved to 10.10.10.10 and the gateway and DC01 both answered ping.

Evidence: [Domain identity, membership, trust, DNS, and connectivity](Evidence/Screenshots/058-Windows11-Domain-Identity-and-Trust.png)

The client shut down cleanly after validation. VirtualBox created KAO-W11-LAB01-003-DomainJoinValidated. A fresh showvminfo query confirmed the VM was powered off and the named snapshot was current. The capture below displays the selected fields from that query.

Evidence: [Current client snapshot and power state](Evidence/Screenshots/059-Windows11-DomainJoinValidated-Snapshot.png)

## 2026-11-15 - Created the parent lab OU

In Active Directory Users and Computers on DC01, selected kaotech.home.arpa and created the KAO Lab organizational unit with accidental-deletion protection selected. Verified that KAO Lab appeared directly under the domain and its contents pane was empty.

Evidence: [KAO Lab OU](Evidence/Screenshots/060-KAO-Lab-OU.png)

Verified in Active Directory Users and Computers on DC01 that the newly created Lab Users OU is directly inside KAO Lab. The selected OU showed no child objects.

Evidence: [Lab Users OU under KAO Lab](Evidence/Screenshots/061-Lab-Users-OU.png)

Verified on DC01 that Lab Groups and Lab Users are sibling OUs directly under KAO Lab. Lab Groups was selected and its contents pane was empty.

Evidence: [Lab Groups OU under KAO Lab](Evidence/Screenshots/062-Lab-Groups-OU.png)

Verified on DC01 that the Lab Groups OU under KAO Lab contains GG-Helpdesk. Active Directory Users and Computers displayed its type as Security Group - Global.

Evidence: [GG-Helpdesk location, type, and scope](Evidence/Screenshots/063-GG-Helpdesk-Global-Security-Group.png)

Queried DC01 with Get-ADUser after the creation wizard finished. Lab Support 01 is enabled, has sign-in name lab.support01@kaotech.home.arpa, and resides in KAO Lab / Lab Users. The pwdLastSet value was 0, consistent with the selected requirement to change the password at next sign-in.

Evidence: [Verified practice account](Evidence/Screenshots/064-Lab-Support01-Account-Verified.png)

Queried GG-Helpdesk on DC01 using Get-ADGroupMember without recursion. The direct membership list returned Lab Support 01, account lab.support01, object class user.

Evidence: [Direct membership on DC01](Evidence/Screenshots/065-GG-Helpdesk-Direct-Membership.png)

After DC01 shut down, VirtualBox created DC01-006-OU-User-Group-Validated. A separate showvminfo query confirmed the server was powered off and this snapshot was current.

Evidence: [Selected VirtualBox snapshot fields](Evidence/Screenshots/066-DC01-Identity-Snapshot.png)

### Verified helpdesk membership in the Windows 11 session

The initial client check ran under KAOTECH\Administrator and returned no helpdesk group row. After switching users, hostname returned KAO-W11-LAB01, whoami returned kaotech\lab.support01, and whoami /groups listed KAOTECH\GG-Helpdesk as enabled by default and enabled in the current session.

Evidence: [Windows 11 session identity and group membership](Evidence/Screenshots/067-Windows11-LabSupport01-Helpdesk-Token.png)

## 2026-11-15 - Read-only helpdesk folder on DC01

Created a dedicated folder and assigned access to the existing global security group. On this new folder, the following elevated PowerShell commands set the file system and share permissions:

```powershell
New-Item C:\HelpdeskDocs -ItemType Directory
icacls C:\HelpdeskDocs /inheritance:r /grant:r 'BUILTIN\Administrators:(OI)(CI)F' 'SYSTEM:(OI)(CI)F' 'KAOTECH\GG-Helpdesk:(OI)(CI)RX'
Set-Content C:\HelpdeskDocs\Welcome.txt 'KAO Lab: Helpdesk reference file.'
New-SmbShare -Name HelpdeskDocs -Path C:\HelpdeskDocs -ReadAccess 'KAOTECH\GG-Helpdesk' -FullAccess 'BUILTIN\Administrators'
```

The group has Read at the SMB share and Read & execute on the NTFS folder, inherited by its files and subfolders. Administrators retain full control. On KAO-W11-LAB01, lab.support01 read Welcome.txt over SMB. Creating write-test.txt returned Access denied, and Test-Path confirmed the file was absent. Get-SmbSession on DC01 identified the client as KAOTECH\lab.support01 at 10.10.10.100.

[Server permissions](Evidence/Screenshots/068-HelpdeskDocs-Permissions.png) | [Client read and write tests](Evidence/Screenshots/069-HelpdeskDocs-Client-Access.png)

After clean shutdown, verified DC01-007-HelpdeskDocs-ReadOnly as the current server snapshot. [VirtualBox snapshot query](Evidence/070-DC01-HelpdeskDocs-Snapshot.txt)

## 2026-11-16 - Group Policy baseline for Lab Users

On DC01, selected KAO Lab / Lab Users in Group Policy Management. Linked Group Policy Objects was empty. Group Policy Inheritance listed Default Domain Policy from kaotech.home.arpa at precedence 1, enabled, with no WMI filter. This inspection recorded the OU baseline before configuring the drive mapping.

Evidence: [Lab Users direct links before the change](Evidence/Screenshots/071-Helpdesk-GPO-Baseline.png)

### HelpdeskDocs drive mapping

In Group Policy Management on DC01:

1. Right-clicked **KAO Lab > Lab Users**, selected **Create a GPO in this domain, and Link it here**, and named it **HelpdeskDocs Drive**. Verified the link was enabled at order 1.
2. Edited **User Configuration > Preferences > Windows Settings > Drive Maps** and created a mapped drive. Set the action to **Create**, the location to `\\DC01\HelpdeskDocs`, the label to **HelpdeskDocs**, and the fixed letter to **H:**.
3. On **Common**, selected **Run in logged-on user's security context** and **Item-level targeting**. In **Targeting > New Item > Security Group**, selected **User in group** and resolved `KAOTECH\GG-Helpdesk`. Saved the item and confirmed it appeared in the editor.
4. On KAO-W11-LAB01, confirmed lab.support01 had no existing network mapping and H: was available. Refreshed user policy, verified the new mapped drive, and read Welcome.txt. The SMB and NTFS permissions on the server continue to govern file access.

[OU link](Evidence/Screenshots/072-Helpdesk-Drive-GPO-Link.png) | [Drive settings](Evidence/Screenshots/073-Helpdesk-Drive-Mapping.png) | [Group targeting](Evidence/Screenshots/074-Helpdesk-Drive-Targeting.png) | [Client result](Evidence/Screenshots/075-Helpdesk-Drive-Client.png)

Verified the powered-off DC01 snapshot [DC01-008-HelpdeskDrive-GPOValidated](Evidence/076-DC01-HelpdeskDrive-Snapshot.txt).

## 2026-11-16 - H drive read and write checks

In the kaotech\lab.support01 session on Windows 11, Get-Content H:\Welcome.txt returned the reference text. New-Item with a unique test filename on H: returned Access denied. Opening the existing Welcome.txt with FileMode.Open and FileAccess.Write also returned Access denied. No write was performed against the reference file. SHA-256 hashes before and after matched. No new snapshot was needed for this validation.

[Read, create, and edit checks](Evidence/Screenshots/077-H-Drive-Read-Create-Edit-Test.png)

## 2026-11-16 - Outside-group access test baseline

On DC01, verified lab.outside01 is enabled in KAO Lab / Lab Users. MemberOf was empty, and Get-ADAccountAuthorizationGroup did not list GG-Helpdesk. Client drive mapping and direct share access tests are pending.

[Outside user baseline](Evidence/Screenshots/078-Outside-User-Baseline.png)

### Outside-user client result

On Windows 11, whoami confirmed kaotech\lab.outside01. After a successful user policy refresh, net use listed no connections, and net use H: returned connection not found (2250). Reading `\\DC01\HelpdeskDocs\Welcome.txt` returned Access is denied. Together with the DC01 membership baseline, this validates skipped drive mapping and denied direct file access for this test user.

[Client result](Evidence/Screenshots/079-Outside-User-Access-Denied.png)
