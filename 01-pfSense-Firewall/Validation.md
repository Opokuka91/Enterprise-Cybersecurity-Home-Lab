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

## 2026-08-09 - Windows 11 Client DHCP Validation

Test:
Ran ipconfig inside KAO-Tech-Windows11-Lab after connecting Adapter 1 to the LAB-LAN internal network.

Expected Result:
The Windows 11 lab client should receive a 10.10.10.x IPv4 address from pfSense with default gateway 10.10.10.1.

Actual Result:
The client received IPv4 address 10.10.10.100/24 with default gateway 10.10.10.1 and DNS suffix home.arpa.

Status:
Pass

Evidence:
- Evidence/Screenshots/031-Windows11-DHCP-Address.png

## 2026-08-09 - Windows 11 Client Internet and DNS Validation

Test:
Ran ping 8.8.8.8 and ping google.com inside KAO-Tech-Windows11-Lab.

Expected Result:
The Windows 11 lab client should reach the internet through pfSense and resolve external DNS names.

Actual Result:
Ping to 8.8.8.8 returned 4 sent, 4 received, 0 lost. Ping to google.com resolved to 142.250.138.113 and returned 4 sent, 4 received, 0 lost.

Status:
Pass

Evidence:
- Evidence/Screenshots/032-Windows11-Internet-DNS-Ping.png

## 2026-08-09 - Windows 11 Base Snapshot Validation

Test:
Verified that a VirtualBox snapshot exists after successful Windows 11 installation, DHCP validation, and internet/DNS validation.

Expected Result:
Snapshot KAO-W11-LAB01-001-BaseInstall-DHCPValidated should exist after client network validation.

Actual Result:
Snapshot KAO-W11-LAB01-001-BaseInstall-DHCPValidated exists in VirtualBox.

Status:
Pass

Evidence:
- Evidence/Screenshots/033-Windows11-Snapshot-BaseInstall-DHCPValidated.png

## 2026-08-20 - pfSense WebGUI Access Validation

Test:
Opened https://10.10.10.1 from Microsoft Edge inside KAO-Tech-Windows11-Lab.

Expected Result:
The pfSense login page should load from the firewall LAN interface.

Actual Result:
The pfSense login page loaded successfully.

Status:
Pass

Evidence:
- Evidence/Screenshots/035-pfSense-WebGUI-Login-Page.png

## 2026-08-20 - pfSense Setup Wizard Completion Validation

Test:
Completed the pfSense setup wizard from the Windows 11 client WebGUI session.

Expected Result:
The setup wizard should complete after applying initial settings and changing the default admin password.

Actual Result:
The wizard displayed the "Congratulations! pfSense is now configured." completion message.

Status:
Pass

Evidence:
- Evidence/Screenshots/051-pfSense-Wizard-Complete.png

## 2026-08-20 - pfSense Dashboard Validation

Test:
Clicked Finish after the setup wizard and verified that the pfSense dashboard loaded.

Expected Result:
The pfSense dashboard should load and show expected WAN and LAN interface information.

Actual Result:
Dashboard loaded successfully. WAN displayed 10.0.2.15 and LAN displayed 10.10.10.1.

Status:
Pass

Evidence:
- Evidence/Screenshots/052-pfSense-Dashboard-After-Wizard.png

## 2026-08-20 - Updated Admin Password Login Validation

Test:
Logged out of pfSense and logged back in with the updated admin password from the Windows 11 client.

Expected Result:
The pfSense dashboard should load after authenticating with the updated password.

Actual Result:
The pfSense dashboard loaded successfully after logging back in.

Status:
Pass

Evidence:
- Evidence/Screenshots/053-pfSense-New-Password-Login-Validated.png

## 2026-08-20 - WebGUI Wizard Snapshot Validation

Test:
Verified that a VirtualBox snapshot exists after successful pfSense WebGUI setup wizard completion and new password login validation.

Expected Result:
Snapshot PFSENSE-FW01-003-WebGUIWizardComplete should exist after the wizard is complete and dashboard access is validated.

Actual Result:
Snapshot PFSENSE-FW01-003-WebGUIWizardComplete exists in the PFSENSE-FW01 snapshot chain.

Status:
Pass

Evidence:
- Evidence/Screenshots/054-pfSense-Snapshot-WebGUIWizardComplete.png
