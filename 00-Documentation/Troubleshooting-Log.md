# Troubleshooting Log

## 2026-08-23 - Windows 11 Client DHCP Failure After VirtualBox Upgrade

Issue:
The Windows 11 lab client could not reach pfSense or the Internet after VirtualBox maintenance.

Symptoms:
- `ipconfig` showed an Automatic Private IP Address: 169.254.156.214
- Subnet mask was 255.255.0.0
- Default gateway was blank
- `ping 10.10.10.1` failed with General failure
- `ping 8.8.8.8` failed with General failure

Likely Cause:
The Windows 11 VM is not receiving DHCP from the pfSense LAN network. This usually means the client is not connected to the correct VirtualBox internal network, the virtual cable is disconnected, or pfSense LAN/DHCP is not currently reachable.

Evidence:
- Evidence/Screenshots/008-Windows11-DHCP-Failure-APIPA-Troubleshooting.png
- Evidence/Screenshots/009-Windows11-Adapter-LAB-LAN-Check.png
- Evidence/Screenshots/010-Windows11-Adapter-Cable-Connected-Check.png
- Evidence/Screenshots/011-pfSense-Restarted-During-Windows-DHCP-Troubleshooting.png
- Evidence/Screenshots/012-Windows11-DHCP-and-Ping-Validation-After-pfSense-Restart.png

Next Diagnostic Steps:
1. Verify PFSENSE-FW01 is running and LAN is 10.10.10.1/24.
2. Verify Windows 11 VM Adapter 1 is attached to Internal Network named LAB-LAN.
3. Verify the virtual cable is connected.
4. Renew the Windows DHCP lease with `ipconfig /release` and `ipconfig /renew`.

Resolution:
Resolved.

The Windows 11 adapter was correctly attached to the `LAB-LAN` internal network and the virtual cable was connected. PFSENSE-FW01 was restarted and confirmed to be running with LAN address 10.10.10.1/24. After pfSense was online, the Windows 11 client successfully renewed network connectivity and validated Internet access.

Validation:
- Ping to 8.8.8.8 succeeded with 0 percent packet loss.
- Ping to google.com succeeded with 0 percent packet loss.
- DNS resolution succeeded because google.com resolved to a public IPv4 address.
