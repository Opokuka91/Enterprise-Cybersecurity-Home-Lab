# Troubleshooting - Lab 002 Windows Server and Active Directory

## 2026-08-30 - DCDIAG Connectivity Failed After Domain Controller Promotion

Issue:
After promoting DC01 to a domain controller, `dcdiag /test:Connectivity` failed.

Observed Error:
`dcdiag` reported that an `_msdcs.kaotech.home.arpa` DNS record could not be resolved and that DC01 failed the Connectivity test.

Likely Cause:
Active Directory DNS service records had not fully registered after the first domain controller promotion and reboot.

Resolution:
Ran the following commands on DC01 from an elevated Command Prompt:

```cmd
ipconfig /flushdns
ipconfig /registerdns
net stop netlogon
net start netlogon
nltest /dsregdns
```

Validation:
- `_ldap._tcp.dc._msdcs.kaotech.home.arpa` resolved successfully.
- SRV record pointed to `dc01.kaotech.home.arpa`.
- `dc01.kaotech.home.arpa` resolved to 10.10.10.10.
- `dcdiag /test:Connectivity` passed.

Evidence:
- Evidence/Screenshots/049B-ADDS-DCDIAG-Connectivity-Failed.png
- Evidence/Screenshots/049C-ADDS-DCDIAG-Connectivity-Failure-Details.png
- Evidence/Screenshots/050A-ADDS-DNS-Flush-Register-Netlogon-Stop.png
- Evidence/Screenshots/050B-ADDS-Netlogon-Started-NLTest-DSRegDNS-Success.png
- Evidence/Screenshots/051A-ADDS-SRV-Record-Validation-Passed.png
- Evidence/Screenshots/051B-ADDS-DCDIAG-Connectivity-Passed.png

Lesson:
Domain controllers rely heavily on DNS. If AD DS promotion succeeds but `dcdiag` fails, verify DNS SRV records before assuming the domain controller is broken.
