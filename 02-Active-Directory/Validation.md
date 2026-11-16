# Validation - Lab 002 Windows Server and Active Directory

## Planned Validation Checks

- [x] DC01 boots successfully.
- [x] DC01 network adapter is connected to LAB-LAN.
- [x] DC01 uses static IPv4 address 10.10.10.10/24.
- [x] DC01 can ping pfSense at 10.10.10.1.
- [x] DC01 can reach the Internet through pfSense.
- [x] DC01 can resolve DNS.
- [x] Active Directory Domain Services installs successfully.
- [x] Domain controller promotion completes successfully.
- [x] AD DNS SRV records resolve successfully.
- [x] `dcdiag /test:Connectivity` passes.
- [ ] Windows 11 client can join the domain.

## 2026-08-23 - Initial Network Validation

Results:
- DHCP assigned DC01 IPv4 address 10.10.10.101/24.
- Default gateway is 10.10.10.1.
- Ping to 10.10.10.1 succeeded with 0 percent packet loss.
- Ping to 8.8.8.8 succeeded with 0 percent packet loss.
- Ping to google.com succeeded with 0 percent packet loss.

Evidence:
- Evidence/Screenshots/017-DC01-Initial-IPConfig-DHCP.png
- Evidence/Screenshots/018-DC01-Internet-DNS-Ping-Validation.png
- Evidence/Screenshots/019-DC01-Gateway-Ping-Validation.png

## 2026-08-30 - Static IP Configuration Validation

Results:
- DC01 was changed from DHCP to static IPv4 addressing.
- IPv4 address is 10.10.10.10/24.
- Default gateway is 10.10.10.1.
- Temporary DNS server is 10.10.10.1 until Active Directory DNS is installed.
- DHCP is disabled on the DC01 Ethernet adapter.
- Current Windows hostname is WIN-SV3LHDQESMT and must be renamed to DC01 before domain controller promotion.

Evidence:
- Evidence/Screenshots/025-DC01-IPv4-Static-IP-Entered-Before-Apply.png
- Evidence/Screenshots/026-DC01-Static-IPConfig-Verified.png
- Evidence/Screenshots/026C-DC01-Static-IPConfig-All-DNS-Verified.png
- Evidence/Screenshots/027A-DC01-Static-IP-Ping-Gateway-Internet-Partial.png
- Evidence/Screenshots/027-DC01-Static-IP-Ping-Validation.png

Connectivity Validation:
- Ping 10.10.10.1 from DC01 passed.
- Ping 8.8.8.8 from DC01 passed.
- Ping google.com from DC01 passed.

Next Required Step:
- Recovery snapshot `DC01-003-StaticIPValidated` created after static IP validation.
- Rename the Windows hostname from WIN-SV3LHDQESMT to DC01 before installing Active Directory Domain Services.

## 2026-08-30 - Hostname Rename Validation

Results:
- Windows Server hostname was renamed from WIN-SV3LHDQESMT to DC01.
- DC01 rebooted successfully after the rename.
- Static IP configuration remained in place after reboot.
- Gateway, Internet, and DNS validation passed after the rename.
- Snapshot `DC01-004-Renamed-StaticIPValidated` was created before Active Directory installation.

Evidence:
- Evidence/Screenshots/029-DC01-Computer-Name-Changed-Before-Restart.png
- Evidence/Screenshots/030-DC01-Hostname-Rename-Validated.png
- Evidence/Screenshots/030A-DC01-Rename-Ping-Gateway-Internet-Partial.png
- Evidence/Screenshots/030B-DC01-Rename-DNS-Ping-Validated.png
- Evidence/Screenshots/031-DC01-Snapshot-Renamed-StaticIPValidated.png

Next Required Step:
- Install the Active Directory Domain Services role on DC01.
- Promote DC01 to the first domain controller for the lab domain.

## 2026-08-30 - Active Directory Promotion and DNS Validation

Results:
- Active Directory Domain Services installed successfully on DC01.
- DC01 was promoted as the first domain controller for kaotech.home.arpa.
- NetBIOS domain name is KAOTECH.
- DC01 login context changed to `kaotech\administrator`.
- DC01 retained static IPv4 address 10.10.10.10/24.
- Default gateway remained 10.10.10.1.
- DNS is now handled locally by the domain controller.

Evidence:
- Evidence/Screenshots/038-ADDS-Role-Installation-Succeeded.png
- Evidence/Screenshots/046-ADDS-Prerequisites-Check-Passed.png
- Evidence/Screenshots/047-ADDS-Domain-Controller-Promotion-Complete.png
- Evidence/Screenshots/048A-ADDS-Post-Promotion-Whoami-Validation.png
- Evidence/Screenshots/048-ADDS-Post-Promotion-Identity-Network-Validation.png

Post-Promotion DNS Validation:
- Initial `dcdiag /test:Connectivity` failed because an `_msdcs.kaotech.home.arpa` DNS record could not be resolved.
- DNS registration was refreshed using `ipconfig /registerdns`, Netlogon restart, and `nltest /dsregdns`.
- `_ldap._tcp.dc._msdcs.kaotech.home.arpa` resolved to `dc01.kaotech.home.arpa`.
- `dcdiag /test:Connectivity` passed after DNS registration.

Evidence:
- Evidence/Screenshots/049B-ADDS-DCDIAG-Connectivity-Failed.png
- Evidence/Screenshots/050B-ADDS-Netlogon-Started-NLTest-DSRegDNS-Success.png
- Evidence/Screenshots/051A-ADDS-SRV-Record-Validation-Passed.png
- Evidence/Screenshots/051B-ADDS-DCDIAG-Connectivity-Passed.png
- Evidence/Screenshots/052-DC01-Snapshot-ADDS-Promoted-DNSValidated.png

## Windows 11 domain membership | 2026-11-15

| Check on KAO-W11-LAB01 | Observed result |
| --- | --- |
| `whoami` | `kaotech\administrator` |
| `Get-CimInstance Win32_ComputerSystem` | Domain `kaotech.home.arpa`, PartOfDomain `True` |
| `Test-ComputerSecureChannel -Verbose` | `True` |
| `Resolve-DnsName dc01.kaotech.home.arpa -Type A` | `10.10.10.10` |
| `Test-Connection 10.10.10.1,10.10.10.10 -Count 1` | Both hosts replied |

[Client DNS before the join](Evidence/Screenshots/056-Windows11-AD-DNS-and-Connectivity.png) · [Join result before restart](Evidence/Screenshots/057-Windows11-Domain-Join-Result.png) · [Post-restart validation](Evidence/Screenshots/058-Windows11-Domain-Identity-and-Trust.png)

## Helpdesk group membership | 2026-11-15

On DC01, the Lab Users and Lab Groups OUs were siblings under KAO Lab. Lab Users held the enabled lab.support01 user. Lab Groups held GG-Helpdesk, a global security group.

Running `Get-ADGroupMember GG-Helpdesk -Server DC01` returned Lab Support 01 (lab.support01) as a direct user member. This check covers directory membership. Resource permissions were outside this checkpoint.

[User attributes](Evidence/Screenshots/064-Lab-Support01-Account-Verified.png) | [Membership result](Evidence/Screenshots/065-GG-Helpdesk-Direct-Membership.png)
