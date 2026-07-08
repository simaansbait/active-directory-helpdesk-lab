\# Active Directory Help Desk Lab



\## Project Overview



This project is a hands-on Active Directory Help Desk lab built to simulate a small Windows domain environment and practice real IT Support tasks.



The lab focuses on user management, group membership, password resets, account lockouts, shared folder permissions, mapped network drives, Group Policy, RSAT administration, and least-privilege delegation.



\## Lab Environment



\- Windows Server 2022 – Domain Controller

\- Windows 10 – Domain-joined client

\- Domain: simaanlab.local

\- Domain Controller: DC01

\- Client Machine: CLIENT01

\- Network: Internal VirtualBox lab network



\## Active Directory Structure



The lab includes a structured AD environment:



\- Users

&#x20; - IT

&#x20; - HR

&#x20; - Finance

&#x20; - Sales

\- Computers

&#x20; - Workstations

\- Groups

\- Servers

\- Disabled Users



\## Users and Groups



Example users:



\- helpdesk.user

\- david.hr

\- sarah.finance

\- john.sales

\- maria.finance



Example groups:



\- HR\_Users

\- Finance\_Users

\- Sales\_Users

\- IT\_Users

\- HelpDesk\_Tier1

\- Shared\_HR\_RW

\- Shared\_Finance\_RW

\- VPN\_Users



\## Completed Help Desk Scenarios



\- Password reset

\- Disable and enable user account

\- User offboarding

\- Department transfer

\- Add and remove user from security groups

\- Account lockout and unlock

\- Shared folder access

\- Access denied troubleshooting

\- Mapped network drives with Group Policy

\- GPO troubleshooting with gpupdate and gpresult

\- RSAT administration from CLIENT01

\- Help Desk delegation using least privilege



\## Shared Folders



Created and tested shared folders:



\- \\\\\\\\DC01\\\\HR

\- \\\\\\\\DC01\\\\Finance



Access was controlled using AD security groups and NTFS/Share permissions.



\## Group Policy



Configured mapped network drives:



\- HR\_Users → H: drive → \\\\\\\\DC01\\\\HR

\- Finance\_Users → F: drive → \\\\\\\\DC01\\\\Finance



Used item-level targeting to apply drive mappings only to the correct security groups.



\## Help Desk Delegation



Configured delegation for the HelpDesk\_Tier1 group.



The delegated helpdesk.user account was able to reset user passwords through RSAT, but was not allowed to create new users, confirming least-privilege access.



\## Tools Used



\- Active Directory Users and Computers

\- Group Policy Management

\- RSAT

\- Windows File Sharing

\- NTFS Permissions

\- CMD

\- gpupdate

\- gpresult

\- whoami



\## Key Learning Outcomes



This project improved my practical understanding of:



\- Active Directory administration

\- User and group management

\- Help Desk troubleshooting workflows

\- Group Policy application

\- Shared folder permissions

\- Least privilege delegation

\- Domain-joined Windows client behavior

