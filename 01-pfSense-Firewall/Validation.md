## 2026-07-27 - WAN Connectivity Validation

Test:
Pinged 8.8.8.8 from the pfSense console using option 7) Ping host.

Expected Result:
pfSense should receive replies from 8.8.8.8 through the WAN interface.

Actual Result:
3 packets transmitted, 3 packets received, 0.0% packet loss.

Status:
Pass

Evidence:
- Evidence/Screenshots/026-pfSense-WAN-Ping-8-8-8-8.png

## 2026-07-27 - DNS Resolution Validation

Test:
Pinged google.com from the pfSense console using option 7) Ping host.

Expected Result:
pfSense should resolve google.com to an IP address and receive ping replies.

Actual Result:
google.com resolved to 173.194.208.100. 3 packets transmitted, 3 packets received, 0.0% packet loss.

Status:
Pass

Evidence:
- Evidence/Screenshots/027-pfSense-DNS-Ping-google-com.png

## 2026-07-27 - Base Install Snapshot Validation

Test:
Verified that a VirtualBox snapshot exists after successful pfSense installation and connectivity validation.

Expected Result:
Snapshot PFSENSE-FW01-002-BaseInstallComplete should exist after first boot, WAN ping validation, and DNS validation.

Actual Result:
Snapshot PFSENSE-FW01-002-BaseInstallComplete exists in VirtualBox.

Status:
Pass

Evidence:
- Evidence/Screenshots/028-pfSense-Snapshot-BaseInstallComplete.png
