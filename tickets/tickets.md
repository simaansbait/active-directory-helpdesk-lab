# Help Desk Tickets – Active Directory Lab

This document includes the main Help Desk scenarios practiced in the Active Directory Help Desk Lab.

---

# Ticket 001 – Password Reset

## User
maria.finance

## Issue
The user forgot the password and could not log in.

## Troubleshooting
Verified the user account in Active Directory Users and Computers.

## Action Taken
Reset the user password and enabled "User must change password at next logon".

## Validation
Confirmed the password reset completed successfully.

## Tool Used
Active Directory Users and Computers

## Result
The user password was reset successfully.

---

# Ticket 002 – Disable and Enable User Account

## User
john.sales

## Issue
The user account needed to be temporarily disabled.

## Troubleshooting
Located the user account in Active Directory Users and Computers.

## Action Taken
Disabled the user account and then re-enabled it for validation.

## Validation
Confirmed the account status changed successfully in Active Directory.

## Tool Used
Active Directory Users and Computers

## Result
The account was disabled and enabled successfully.

---

# Ticket 003 – Group Membership Change

## User
david.hr

## Issue
The user required temporary VPN access.

## Troubleshooting
Checked the user's current group membership in Active Directory.

## Action Taken
Added david.hr to the VPN_Users security group.

Later, removed the user from VPN_Users after access was no longer required.

## Validation
Confirmed the group membership was updated successfully.

## Tool Used
Active Directory Users and Computers

## Result
User group membership was updated according to the access request.

---

# Ticket 004 – User Offboarding

## User
john.sales

## Issue
The employee left the company and access needed to be removed.

## Troubleshooting
Verified the user account location and status in Active Directory.

## Action Taken
Disabled the user account and moved it to the Disabled Users OU.

## Validation
Attempted to log in from CLIENT01 and received the following message:

"Your account has been disabled. Please see your system administrator."

## Tool Used
Active Directory Users and Computers
Windows 10 domain login

## Result
The user could no longer log in to the domain.

---

# Ticket 005 – Department Transfer

## User
maria.finance

## Issue
The user was transferred from the Finance department to the HR department.

## Troubleshooting
Checked the user's current OU location and group membership in Active Directory.

## Action Taken
Moved the user from the Finance OU to the HR OU.

Removed the user from:
- Finance_Users

Added the user to:
- HR_Users

## Validation
Confirmed that the user account was moved to the HR OU and that group membership was updated correctly.

## Tool Used
Active Directory Users and Computers

## Result
The user account now reflects the new department and no longer has Finance group access.

---

# Ticket 006 – Account Lockout and Unlock

## User
david.hr

## Issue
The user account was locked after multiple failed logon attempts.

## Troubleshooting
Checked the user account status in Active Directory Users and Computers.

## Action Taken
Configured Account Lockout Policy through Group Policy.

Configured:
- Account lockout threshold
- Account lockout duration
- Reset account lockout counter

Unlocked the user account from the Account tab in Active Directory.

## Validation
The user successfully logged into CLIENT01 after the account was unlocked.

## Tool Used
Group Policy Management
Active Directory Users and Computers
Windows 10 domain login

## Result
The account lockout and unlock process was tested successfully.

---

# Ticket 007 – HR Shared Folder Access

## User
david.hr

## Issue
The HR user required access to the HR shared folder.

## Troubleshooting
Verified that david.hr was a member of HR_Users.

Verified the access path:

\\DC01\HR

## Action Taken
Created the shared folder:

\\DC01\HR

Configured Share and NTFS permissions using the Shared_HR_RW security group.

Added HR_Users as a member of Shared_HR_RW.

## Validation
Logged into CLIENT01 as david.hr and accessed:

\\DC01\HR

Successfully created a test TXT file inside the folder.

## Tool Used
Active Directory Users and Computers
Windows File Sharing
NTFS Permissions

## Result
The HR user successfully accessed and wrote to the HR shared folder.

---

# Ticket 008 – Access Denied to HR Share

## User
Non-HR domain user

## Issue
A user who was not a member of the HR group attempted to access the HR shared folder.

## Troubleshooting
Verified that the user was not a member of HR_Users or Shared_HR_RW.

## Action Taken
Attempted to access the HR shared folder from CLIENT01:

\\DC01\HR

## Validation
Received Access Denied.

## Tool Used
Windows File Explorer
Active Directory Users and Computers

## Result
Access was correctly denied because the user did not have HR permissions.

---

# Ticket 009 – Finance Shared Folder Access

## User
sarah.finance

## Issue
The Finance user required access to the Finance shared folder.

## Troubleshooting
Verified that sarah.finance was a member of Finance_Users.

Verified the access path:

\\DC01\Finance

## Action Taken
Created the shared folder:

\\DC01\Finance

Configured Share and NTFS permissions using the Shared_Finance_RW security group.

Added Finance_Users as a member of Shared_Finance_RW.

## Validation
Logged into CLIENT01 as sarah.finance and accessed:

\\DC01\Finance

Successfully created a test TXT file inside the folder.

## Tool Used
Active Directory Users and Computers
Windows File Sharing
NTFS Permissions

## Result
The Finance user successfully accessed and wrote to the Finance shared folder.

---

# Ticket 010 – Access Denied to Finance Share

## User
david.hr

## Issue
An HR user attempted to access the Finance shared folder.

## Troubleshooting
Verified that david.hr was not a member of Finance_Users or Shared_Finance_RW.

## Action Taken
Attempted to access the Finance shared folder from CLIENT01:

\\DC01\Finance

## Validation
Received Access Denied.

## Tool Used
Windows File Explorer
Active Directory Users and Computers

## Result
Access was correctly denied because the user did not have Finance permissions.

---

# Ticket 011 – HR Drive Mapping with Group Policy

## User
david.hr

## Issue
HR users should receive the HR shared drive automatically after logging into the domain-joined workstation.

## Troubleshooting
Verified that david.hr was a member of HR_Users.

Verified that the HR shared folder was accessible:

\\DC01\HR

## Action Taken
Created a Group Policy Object to map the HR shared folder.

Configured:
- Drive Letter: H:
- Location: \\DC01\HR
- Label: HR Drive
- Item-level targeting: HR_Users

## Validation
Logged into CLIENT01 as david.hr and confirmed that HR Drive H: appeared in This PC.

Ran:

gpupdate /force

Ran:

gpresult /r

Confirmed that GPO_Map_HR_Drive appeared under Applied Group Policy Objects.

## Tool Used
Group Policy Management
Group Policy Preferences
gpupdate
gpresult

## Result
The HR drive was mapped successfully only for HR users.

---

# Ticket 012 – Finance Drive Mapping with Group Policy

## User
sarah.finance

## Issue
Finance users should receive the Finance shared drive automatically after logging into the domain-joined workstation.

## Troubleshooting
Verified that sarah.finance was a member of Finance_Users.

Verified that the Finance shared folder was accessible:

\\DC01\Finance

## Action Taken
Created a Group Policy Object to map the Finance shared folder.

Configured:
- Drive Letter: F:
- Location: \\DC01\Finance
- Label: Finance Drive
- Item-level targeting: Finance_Users

## Validation
Logged into CLIENT01 as sarah.finance and confirmed that Finance Drive F: appeared in This PC.

Confirmed that david.hr did not receive the Finance drive.

## Tool Used
Group Policy Management
Group Policy Preferences
gpupdate
gpresult

## Result
The Finance drive was mapped successfully only for Finance users.

---

# Ticket 013 – GPO Troubleshooting

## User
david.hr

## Issue
The user reported that the HR network drive was missing.

## Troubleshooting
Ran the following command on CLIENT01:

gpupdate /force

Then ran:

gpresult /r

Checked the Applied Group Policy Objects section.

## Action Taken
Verified that GPO_Map_HR_Drive was applied to the user.

Checked:
- User group membership
- GPO link location
- Item-level targeting
- User OU location
- Network connectivity to DC01

## Validation
Confirmed that GPO_Map_HR_Drive appeared in gpresult /r.

## Tool Used
CMD
gpupdate
gpresult
Group Policy Management

## Result
The GPO was applying correctly to the user.

---

# Ticket 014 – Help Desk Delegation

## User
helpdesk.user

## Group
HelpDesk_Tier1

## Issue
Help Desk Tier 1 required limited permissions to support users without receiving full administrative rights.

## Troubleshooting
Verified that helpdesk.user was a member of HelpDesk_Tier1.

Verified that HelpDesk_Tier1 was delegated permissions over the SimaanLab Users OU.

## Action Taken
Delegated control over the SimaanLab Users OU using the Delegate Control Wizard.

Allowed actions:
- Reset user passwords
- Force password change at next logon
- Unlock user accounts
- Read user information

## Validation
Logged into CLIENT01 as helpdesk.user.

Opened Active Directory Users and Computers using RSAT.

Successfully reset a user's password.

## Least Privilege Test
Attempted to create a new user account.

The action was not allowed.

## Tool Used
Active Directory Users and Computers
RSAT
Delegate Control Wizard

## Result
Delegation worked correctly. helpdesk.user could perform limited Help Desk tasks without Domain Admin permissions.

---

# Ticket 015 – RSAT Administration from CLIENT01

## User
helpdesk.user

## Issue
Help Desk should manage Active Directory from a workstation instead of logging directly into the Domain Controller.

## Troubleshooting
Attempted to run administrative tools directly on DC01 as helpdesk.user and received a logon type restriction.

Confirmed that Help Desk users should not log directly into Domain Controllers.

## Action Taken
Installed RSAT on CLIENT01.

Logged into CLIENT01 as:

SIMAANLAB\helpdesk.user

Opened Active Directory Users and Computers from CLIENT01.

## Validation
Confirmed that helpdesk.user could access Active Directory Users and Computers from CLIENT01 using delegated permissions.

## Tool Used
RSAT
Active Directory Users and Computers
CLIENT01 domain-joined workstation

## Result
Help Desk administration was performed from a domain-joined client machine using RSAT, following a more realistic and secure workflow.
