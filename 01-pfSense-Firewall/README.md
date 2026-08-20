# Lab 001 - pfSense Enterprise Firewall

## Overview

This lab documents the deployment of a pfSense Community Edition firewall in VirtualBox as the network perimeter for an enterprise-style cybersecurity home lab.

The firewall provides separation between an upstream WAN network and an isolated internal lab LAN. A Windows 11 client was connected behind pfSense to validate DHCP, routing, DNS resolution, Internet access, and WebGUI management access.

This project was built as portfolio evidence for hands-on experience in network administration, firewall deployment, virtualization, troubleshooting, documentation, and security hardening.

## Business Objective

Deploy a centralized firewall to control traffic between an internal enterprise lab network and an upstream network, creating a secure foundation for future Active Directory, Windows client, Linux, Kali, Splunk, and Microsoft Sentinel labs.

## Technical Objectives

- Create a pfSense virtual firewall in VirtualBox.
- Configure separate WAN and LAN interfaces.
- Use VirtualBox NAT for upstream WAN connectivity.
- Use an isolated VirtualBox Internal Network for the enterprise LAN.
- Configure the LAN as `10.10.10.0/24`.
- Validate DHCP assignment to a Windows 11 client.
- Validate Internet and DNS access through pfSense.
- Complete the pfSense WebGUI setup wizard.
- Replace the default admin password.
- Capture screenshots, validation results, and VirtualBox snapshots as evidence.

## Lab Architecture

![pfSense Enterprise Firewall Lab Architecture](Images/pfSense-Lab-Architecture.svg)

```text
                    Internet
                        |
                 Home / Host Network
                        |
                 VirtualBox NAT
                        |
                WAN - em0 - 10.0.2.15/24
                +----------------------+
                |     PFSENSE-FW01     |
                | pfSense CE 2.8.1     |
                +----------------------+
                LAN - em1 - 10.10.10.1/24
                        |
              VirtualBox Internal Network
                      LAB-LAN
                        |
              +----------------------+
              | KAO-Tech-Windows11   |
              | 10.10.10.100/24      |
              +----------------------+
```

## Systems Built

| System | Role | Network | IP Address |
| --- | --- | --- | --- |
| `PFSENSE-FW01` | Firewall / gateway | WAN | `10.0.2.15/24` |
| `PFSENSE-FW01` | Firewall / gateway | LAN | `10.10.10.1/24` |
| `KAO-Tech-Windows11-Lab` | Internal client | LAB-LAN | `10.10.10.100/24` |

## VirtualBox Configuration

### pfSense VM

| Setting | Value |
| --- | --- |
| VM name | `PFSENSE-FW01` |
| OS type | FreeBSD 64-bit |
| Memory | 2048 MB |
| CPUs | 2 |
| Disk | 20 GB dynamic VDI |
| Adapter 1 | NAT |
| Adapter 2 | Internal Network: `LAB-LAN` |

### Windows 11 Client VM

| Setting | Value |
| --- | --- |
| VM name | `KAO-Tech-Windows11-Lab` |
| Adapter 1 | Internal Network: `LAB-LAN` |
| DHCP address | `10.10.10.100/24` |
| Default gateway | `10.10.10.1` |

## pfSense Configuration Summary

| Area | Configuration |
| --- | --- |
| Version | pfSense CE `2.8.1-RELEASE` |
| Hostname | `pfSense` |
| Domain | `home.arpa` |
| Timezone | `US/Central` |
| WAN | DHCP via VirtualBox NAT |
| WAN RFC1918 blocking | Disabled for VirtualBox NAT lab design |
| WAN bogon blocking | Enabled |
| LAN | `10.10.10.1/24` |
| DHCP scope | `10.10.10.100 - 10.10.10.199` |
| Admin password | Changed from default; not stored in repository |

## Evidence

Key screenshots are stored in:

```text
Evidence/Screenshots/
```

Important evidence files:

| Evidence | Purpose |
| --- | --- |
| [002-pfSense-Adapter1-WAN-NAT.png](Evidence/Screenshots/002-pfSense-Adapter1-WAN-NAT.png) | WAN adapter configured as NAT |
| [003-pfSense-Adapter2-LAN-LAB-LAN.png](Evidence/Screenshots/003-pfSense-Adapter2-LAN-LAB-LAN.png) | LAN adapter configured as Internal Network |
| [013-pfSense-LAN-Configured-10-10-10.png](Evidence/Screenshots/013-pfSense-LAN-Configured-10-10-10.png) | LAN configured as `10.10.10.1/24` |
| [025-pfSense-First-Boot-Console.png](Evidence/Screenshots/025-pfSense-First-Boot-Console.png) | First successful pfSense boot |
| [026-pfSense-WAN-Ping-8-8-8-8.png](Evidence/Screenshots/026-pfSense-WAN-Ping-8-8-8-8.png) | WAN Internet connectivity test |
| [027-pfSense-DNS-Ping-google-com.png](Evidence/Screenshots/027-pfSense-DNS-Ping-google-com.png) | DNS resolution test |
| [031-Windows11-DHCP-Address.png](Evidence/Screenshots/031-Windows11-DHCP-Address.png) | Windows client DHCP validation |
| [032-Windows11-Internet-DNS-Ping.png](Evidence/Screenshots/032-Windows11-Internet-DNS-Ping.png) | Windows client Internet and DNS validation |
| [052-pfSense-Dashboard-After-Wizard.png](Evidence/Screenshots/052-pfSense-Dashboard-After-Wizard.png) | Dashboard after setup wizard |
| [053-pfSense-New-Password-Login-Validated.png](Evidence/Screenshots/053-pfSense-New-Password-Login-Validated.png) | New admin password login validation |
| [054-pfSense-Snapshot-WebGUIWizardComplete.png](Evidence/Screenshots/054-pfSense-Snapshot-WebGUIWizardComplete.png) | Final post-wizard snapshot |

## Validation Results

| Test | Expected Result | Actual Result | Status |
| --- | --- | --- | --- |
| pfSense WAN ping to `8.8.8.8` | Firewall reaches Internet by IP | 3 sent, 3 received, 0% loss | Pass |
| pfSense DNS ping to `google.com` | Firewall resolves DNS and receives replies | Resolved and replied with 0% loss | Pass |
| Windows DHCP | Client receives `10.10.10.x` address | Client received `10.10.10.100/24` | Pass |
| Windows default gateway | Client uses pfSense LAN as gateway | Gateway `10.10.10.1` assigned | Pass |
| Windows Internet ping | Client reaches Internet through pfSense | Ping to `8.8.8.8` passed | Pass |
| Windows DNS ping | Client resolves Internet DNS through pfSense | Ping to `google.com` passed | Pass |
| pfSense WebGUI | Client reaches `https://10.10.10.1` | Login page loaded | Pass |
| Setup wizard | Initial pfSense setup completes | Wizard completed successfully | Pass |
| Admin password | Default password replaced | New password login validated | Pass |

Full validation notes are documented in [Validation.md](Validation.md).

## Snapshots

| Snapshot | Purpose |
| --- | --- |
| `PFSENSE-FW01-001-NetworkAdaptersConfigured` | Baseline before OS installation |
| `PFSENSE-FW01-002-BaseInstallComplete` | pfSense installed, first boot and connectivity validated |
| `PFSENSE-FW01-003-WebGUIWizardComplete` | WebGUI wizard complete, admin password changed, dashboard validated |
| `KAO-W11-LAB01-001-BaseInstall-DHCPValidated` | Windows 11 client installed and network validation complete |

## Troubleshooting Performed

### LAN Interface Was Not Assigned

During installation, pfSense initially detected WAN as `em0`, but LAN was not assigned.

Resolution:

- Used the installer interface assignment option.
- Assigned WAN to `em0`.
- Assigned LAN to `em1`.
- Confirmed both interfaces were active before continuing.

Evidence:

- [011-pfSense-Interface-Assignment-LAN-Not-Assigned.png](Evidence/Screenshots/011-pfSense-Interface-Assignment-LAN-Not-Assigned.png)
- [014-pfSense-Interface-Assignment-Corrected.png](Evidence/Screenshots/014-pfSense-Interface-Assignment-Corrected.png)

### VM Rebooted Back Into Installer

After installation, the VM rebooted into the Netgate installer because the ISO was still attached.

Resolution:

- Powered off the VM.
- Removed the installer ISO from the virtual optical drive.
- Booted from the installed virtual hard disk.

Evidence:

- [024-pfSense-ISO-Detached.png](Evidence/Screenshots/024-pfSense-ISO-Detached.png)

### WAN RFC1918 Blocking Adjustment

pfSense WAN received a private `10.0.2.15/24` address from VirtualBox NAT. Because this is an RFC1918 address, RFC1918 blocking on WAN was disabled for the lab design while bogon blocking remained enabled.

Evidence:

- [047-pfSense-WAN-RFC1918-Unchecked-Bogon-Checked.png](Evidence/Screenshots/047-pfSense-WAN-RFC1918-Unchecked-Bogon-Checked.png)

## Security Considerations

- Default `admin` password was changed during the setup wizard.
- New admin password was not stored in screenshots, documentation, Git history, or repository files.
- WebGUI is reachable only from the internal `LAB-LAN` side in this lab design.
- WAN uses DHCP through VirtualBox NAT for controlled lab Internet access.
- Bogon blocking remained enabled on WAN.
- VirtualBox snapshots were created at stable milestones for recovery.

## Skills Demonstrated

### Network Administration

- LAN/WAN interface planning
- IP addressing
- DHCP validation
- Default gateway validation
- DNS testing

### Firewall Administration

- pfSense installation
- Interface assignment
- WebGUI setup
- WAN/LAN configuration
- Initial firewall hardening

### Systems Administration

- VirtualBox VM provisioning
- Virtual network design
- Snapshot management
- Windows client network validation

### Security Operations

- Secure credential handling
- Evidence collection
- Connectivity validation
- Troubleshooting documentation
- Change documentation

## Business Value

This lab establishes a controlled network perimeter for a larger enterprise cybersecurity environment. pfSense provides routing, segmentation, DHCP, management access, and a firewall foundation that future systems can build on, including Active Directory, Windows clients, Kali Linux, Splunk, and Microsoft Sentinel.

## Resume Bullet

Designed and deployed a pfSense-based enterprise firewall lab in VirtualBox, implementing WAN/LAN segmentation, DHCP services, client routing, DNS validation, WebGUI hardening, snapshot recovery points, and GitHub-ready documentation with evidence-based validation.

## Interview Talking Points

- Explain the difference between WAN and LAN interfaces.
- Explain why pfSense needs at least two network adapters.
- Explain why the lab uses `10.10.10.0/24` instead of the home router subnet.
- Explain how DHCP was validated from a Windows 11 client.
- Explain why RFC1918 blocking was disabled on WAN for VirtualBox NAT.
- Explain why the default pfSense password must be changed immediately.
- Explain how snapshots support change control and recovery.

## Next Steps

- Create a polished network diagram.
- Export pfSense configuration backup.
- Build Windows Server VM.
- Promote Windows Server to Active Directory Domain Controller.
- Update DHCP/DNS design for Active Directory integration.
- Join the Windows 11 client to the domain.
- Add Sysmon and centralized logging.
