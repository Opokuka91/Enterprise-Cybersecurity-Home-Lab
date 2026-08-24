# Validation - Lab 002 Windows Server and Active Directory

## Planned Validation Checks

- [x] DC01 boots successfully.
- [x] DC01 network adapter is connected to LAB-LAN.
- [ ] DC01 uses static IPv4 address 10.10.10.10/24.
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
