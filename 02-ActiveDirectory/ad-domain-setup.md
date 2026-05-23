# Phase 2: Active Directory Domain Setup

## Objective
Deploy a new Active Directory forest to simulate corporate domain infrastructure for user management, Group Policy, and identity services.

## Domain Information
- **Domain Name**: `chrisadmin.lab`
- **Server Name**: `DC01`
- **Operating System**: Windows Server 2022
- **IP Assignment**: Dynamic (VMware DHCP)

## Steps Performed

### 1. Server Preparation
- Renamed server to `DC01`
- Installed required Windows features:
  - Active Directory Domain Services
  - DNS Server
  - Group Policy Management

### 2. Domain Controller Promotion
- Deployment Configuration: **Add a new forest**
- Root domain name: `chrisadmin.lab`
- Forest and Domain Functional Level: **Windows Server 2022**
- DNS Server enabled during promotion
- Set Directory Services Restore Mode (DSRM) password

### 3. Post-Promotion Verification
- Successfully restarted and logged in using `chrisadmin\Administrator`
- Opened **Active Directory Users and Computers** console

**Important Note on IP Configuration**:
Microsoft strongly recommends using a **static IP address** for Domain Controllers in production environments. Although this lab used dynamic IP (assigned via VMware DHCP), I limited the DHCP pool to ensure the Domain Controller consistently receives the same IP address (`192.168.100.128`) on every reboot. This helped maintain AD stability and prevented loss of control of the domain during the lab exercises.

## Verification Commands
```powershell
dcdiag
nltest /dsgetdc:chrisadmin.lab
ipconfig /all
