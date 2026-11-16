# Lessons Learned - Lab 002 Windows Server and Active Directory

## Active Directory Depends on DNS

Active Directory Domain Services relies on DNS service records so clients and domain controllers can locate authentication, LDAP, Kerberos, and Global Catalog services. A domain controller can appear to install correctly while still failing health checks if its DNS records have not registered.

## Validate Before Moving Forward

The lab did not move directly from promotion to client domain join. Running `nslookup` and `dcdiag` first confirmed whether the domain controller was healthy enough to support clients.

## Troubleshooting Is Portfolio Evidence

The initial `dcdiag` failure was documented instead of hidden. Capturing the issue, root cause, commands used, and final successful validation demonstrates real operational troubleshooting.

## Snapshots Support Change Control

The `DC01-005-ADDS-Promoted-DNSValidated` snapshot creates a rollback point before the next major change: joining the Windows 11 client to the domain.

## Validate from the joined workstation

The join command succeeded before restart. After restart, choosing Other user allowed sign-in with the domain account. Checking whoami confirmed the session identity, while Test-ComputerSecureChannel independently confirmed the workstation trust relationship.
