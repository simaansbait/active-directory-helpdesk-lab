# Lab Topology – Active Directory Help Desk Lab

This diagram shows the virtual lab environment used for the Active Directory Help Desk project.


VirtualBox Lab Environment
Network: AD-LAB Internal Network

+---------------------------------------------------+
|                   DC01                            |
|---------------------------------------------------|
| OS: Windows Server 2022                           |
| Role: Domain Controller                           |
| Role: DNS Server                                  |
| Domain: simaanlab.local                           |
| IP Address: 192.168.10.10                         |
|                                                   |
| Services:                                         |
| - Active Directory Domain Services                |
| - DNS                                             |
| - Group Policy                                    |
| - File Shares                                     |
|                                                   |
| Shared Folders:                                   |
| - \\DC01\HR                                        |
| - \\DC01\Finance                                   |
+--------------------------+------------------------+
                           |
                           |
                           | Internal Network: AD-LAB
                           |
                           |
+--------------------------+------------------------+
|                   CLIENT01                        |
|---------------------------------------------------|
| OS: Windows 10                                    |
| Role: Domain-Joined Workstation                   |
| Domain: simaanlab.local                           |
| IP Address: 192.168.10.20                         |
| DNS Server: 192.168.10.10                         |
|                                                   |
| Used for:                                         |
| - Domain user login testing                       |
| - RSAT administration                             |
| - Mapped drive testing                            |
| - Access denied testing                           |
| - Group Policy validation                         |
+---------------------------------------------------+


Active Directory Structure
simaanlab.local
└── SimaanLab
    ├── Users
    │   ├── IT
    │   │   └── helpdesk.user
    │   ├── HR
    │   │   ├── david.hr
    │   │   └── maria.finance
    │   ├── Finance
    │   │   └── sarah.finance
    │   └── Sales
    │
    ├── Computers
    │   └── Workstations
    │       └── CLIENT01
    │
    ├── Groups
    │   ├── HR_Users
    │   ├── Finance_Users
    │   ├── Sales_Users
    │   ├── IT_Users
    │   ├── HelpDesk_Tier1
    │   ├── Shared_HR_RW
    │   ├── Shared_Finance_RW
    │   └── VPN_Users
    │
    ├── Servers
    │
    └── Disabled Users
        └── john.sales
