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

## Windows 11 domain join credential rejection

Add-Computer reported an incorrect username or password and HasSucceeded=False. The client had already resolved the domain LDAP SRV record. Repeating the join with the domain administrator credentials returned HasSucceeded=True and a restart prompt. The error did not identify which credential field caused the rejection.

Evidence: [Failed attempt and successful retry](Evidence/Screenshots/057-Windows11-Domain-Join-Result.png)

### Black screen during the post-join restart

Windows displayed an update message and then a black screen. VirtualBox still reported the client running. The virtual disk counters stayed unchanged across repeated checks, and a normal power-button request did not shut down the guest. After an authorized VirtualBox reset of the Windows 11 client, the Windows sign-in screen appeared with the Other user option. The cause of the black screen was not established.
