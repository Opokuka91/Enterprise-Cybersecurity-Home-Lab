# Lab 002 - Windows Server and Active Directory

## Objective

Deploy a Windows Server virtual machine that will become the first domain controller for the enterprise home lab.

## Business Value

Active Directory centralizes identity, authentication, computer management, and policy enforcement. This lab demonstrates foundational system administration skills used in help desk, desktop support, SOC, and security engineering roles.

## Planned Server

- VM name: DC01
- Operating system: Windows Server
- Network: LAB-LAN
- Planned IPv4 address: 10.10.10.10/24
- Gateway: 10.10.10.1
- DNS role: Active Directory integrated DNS
- Domain name: kaotech.local

## Acceptance Criteria

This lab is complete when:

- DC01 is created in VirtualBox.
- Windows Server is installed.
- DC01 has a static IP address on LAB-LAN.
- Active Directory Domain Services is installed.
- A new forest/domain is created.
- DNS is functional.
- The Windows 11 client can join the domain.
- Evidence screenshots are captured.
- VirtualBox snapshots are created at stable milestones.
- Documentation is committed to GitHub.

## Evidence Standard

Every major milestone must include:

- Screenshot
- Build log entry
- Validation result
- Snapshot decision
- Git timing

## Security Notes

- Do not publish passwords, recovery keys, product keys, or private credentials.
- Use lab-only passwords and store them outside the public GitHub repository.
- Document configuration decisions without exposing secrets.
