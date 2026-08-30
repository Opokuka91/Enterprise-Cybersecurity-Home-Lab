# Validation - Lab 002 Windows Server and Active Directory

## Planned Validation Checks

- [x] DC01 boots successfully.
- [x] DC01 network adapter is connected to LAB-LAN.
- [x] DC01 uses static IPv4 address 10.10.10.10/24.
- [x] DC01 can ping pfSense at 10.10.10.1.
- [x] DC01 can reach the Internet through pfSense.
- [x] DC01 can resolve DNS.
- [ ] Active Directory Domain Services installs successfully.
- [ ] Domain controller promotion completes successfully.
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
