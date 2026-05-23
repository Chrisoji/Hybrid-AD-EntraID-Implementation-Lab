# Phase 3: On-Premises Active Directory Administration

## Objective
Configure a realistic corporate Active Directory environment demonstrating user management, resource sharing, Group Policy application, and IT support troubleshooting skills.

## Topics Covered
- Organizational Units (OU) design
- User and Security Group management
- Shared Printer deployment and troubleshooting
- Group Policy Objects (GPOs) creation and linking
- Client domain joining and policy verification

## Steps Performed

### 1. Organizational Units (OUs) Creation
Created the following OUs under `chrisadmin.lab`:

- IT
- Operations
- Drivers
- Finance
- Sales

**Purpose**: To organize users logically and enable targeted application of Group Policies.

### 2. Security Groups Creation
Created the following Security Groups:
- IT-Admins
- Operations-Team
- Drivers-Team
- Finance-Team

### 3. User Account Creation and Organization
- Created sample users using PowerShell
- Moved users into their respective OUs:
  - **IT OU**: John Doe (`username: john`), Sarah eve (`username: sarah`)
  - **Operations OU**: Michael Smith (`username: michael`)
  - **Drivers OU**: David Lee (`username: david`)
  - **Finance OU**: Emma Wilson (`ewilson`)

### 4. Printer Deployment & Sharing
- Installed **Print and Document Services** role on the domain controller (DC01)
- Created and shared a virtual printer named **`Corporate-Printer`** using Microsoft Print To PDF
- Configured sharing and granted **Print** permissions to `Domain Users`

**Issue Encountered**: Initially, domain users could not access the shared printer from client machines.

**Resolution**:
- Updated printer Security permissions to allow `Domain Users`
- Restarted the Print Spooler service on command line interface
- On Client01, successfully added the Corporate-Printer to the list of printers on the user account john by using the manual method of adding printers:
  - Path: `\\DC01\Corporate-Printer`
- Verified that user `john` (John Doe) could access and print successfully from Client01

**IT Support Skill Demonstrated**: Troubleshooting and resolving shared resource access issues in an Active Directory domain.

### 5. Group Policy Objects (GPOs) Configuration
- Created multiple GPOs and linked them to specific OUs:
  - `IT-Desktop-Policy` → Linked to **IT** OU
  - `Operations-Policy` → Linked to **Operations** OU
  - `Drivers-Policy` → Linked to **Drivers** OU
- Configured sample settings (e.g., desktop restrictions, Control Panel access limitation)

### 6. Client Domain Join
- Joined `Client01` and `Client02` (Windows 10 Pro) to the `chrisadmin.lab` domain
- Successfully logged in using domain accounts from different OUs
- Verified that OU-linked Group Policies were applying correctly

## Verification
```powershell
# On DC01
dcdiag
gpupdate /force

# On Client machines
gpresult /r /scope user
