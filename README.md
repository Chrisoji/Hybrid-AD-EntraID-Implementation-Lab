# Hybrid Active Directory + Entra ID Enterprise Lab

**Professional Lab Project**  
Demonstrating hands-on expertise in Corporate Network Administration, Identity Management, Microsoft 365 Administration, and Modern Endpoint Management.

---

## Project Overview

This repository documents the complete build of a **hybrid enterprise IT environment**, simulating a real-world corporate infrastructure. The lab combines traditional on-premises Active Directory with Microsoft cloud technologies to showcase strong technical skills relevant to Network Administration, IT Support Specialist, and Technical Implementation roles.

### Key Technologies Used
- **On-Premises**: Windows Server 2022, Active Directory Domain Services, Group Policy
- **Hybrid Identity**: Microsoft Entra ID, Entra Connect, Hybrid Azure AD Join
- **Productivity Suite**: Microsoft 365 (Exchange Online, Teams, SharePoint)
- **Endpoint Management**: Microsoft Intune
- **Virtualization**: VMware Workstation (NAT)

### Lab Architecture
- **DC01**: Windows Server 2022 Domain Controller (`chrisadmin.lab`)
- **Client01 & Client02**: Windows 10 Pro (domain-joined and Hybrid Azure AD joined)
- **Microsoft 365 Tenant**: CoporateITsolutions.onmicrosoft.com (E5 licensing)

---

## What Was Built & Configured

### Phase 1: VMware Environment Setup
- Configured stable NAT networking with consistent IP assignment
- Created and prepared Windows Server 2022 and Windows 10 virtual machines

### Phase 2: Active Directory Domain Setup
- Deployed a new Active Directory forest (`chrisadmin.lab`)
- Configured DNS, Organizational Units, and security groups

### Phase 3: On-Premises AD Administration
- Created and organized users into departmental OUs
- Implemented Group Policy Objects (GPOs) linked to OUs
- Deployed and troubleshot a shared network printer (`Corporate-Printer`)
- Joined client machines to the domain

### Phase 4: Hybrid Identity with Microsoft Entra ID
- Configured Microsoft Entra Connect with Password Hash Synchronization
- Performed OU filtering and computer object synchronization
- Successfully implemented **Hybrid Azure AD Join**
- Configured and tested Single Sign-On (Regular SSO)

### Phase 5: Microsoft 365 Administration
- Assigned E5 licenses to users
- Created and configured a **Shared Mailbox** with delegation (Full Access & Send As)
- Set up Teams (team creation and policies)
- Configured SharePoint sites and sharing settings
- Simulated real business collaboration scenarios

### Phase 6: Microsoft Intune & Endpoint Management
- Explored Intune administration in a hybrid environment
- Configured Configuration Profiles, Compliance Policies, and Application Management
- Demonstrated understanding of modern endpoint management concepts

---

## Skills Demonstrated

- Enterprise Active Directory design and administration
- Hybrid identity and cloud synchronization (Entra Connect)
- Microsoft 365 tenant and service administration
- Group Policy and Intune policy management
- Shared resource configuration and troubleshooting
- IT Support best practices and documentation
- Problem-solving in hybrid environments

---

## Repository Structure

- `/01-Setup` → VMware and base environment
- `/02-ActiveDirectory` → AD DS deployment
- `/03-OnPrem-AD-Administration` → Users, GPOs, Printer
- `/04-Hybrid-EntraID` → Entra Connect and Hybrid Join
- `/05-M365-Administration` → Exchange, Teams, SharePoint, Shared Mailbox
- `/06-Intune-Endpoint-Management` → Intune configuration and concepts

Each phase contains detailed documentation and screenshots.

---

**Built & Documented by Christopher Oji**  
Network Administrator | IT Support Specialist | CCNA  
Toronto, Ontario

- LinkedIn: [linkedin.com/in/chrisoji](https://linkedin.com/in/chrisoji)
- GitHub: [github.com/Chrisoji](https://github.com/Chrisoji)

---

This lab was built to demonstrate practical, production-level knowledge in hybrid IT environments and modern workplace technologies.

Feel free to explore the detailed phase documentation. All configurations are clearly explained with screenshots and verification steps.

---
