# Phase 5: Microsoft 365 Administration

## Objective
Configure and manage core Microsoft 365 services (Exchange Online, Teams, SharePoint, and Shared Mailboxes) to simulate enterprise-level productivity and collaboration administration. This phase demonstrates strong Microsoft 365 administration skills required for Technical Implementation Specialist and IT Support roles.

## Environment Details
- **Microsoft 365 Tenant**: CoporateITsolutions.onmicrosoft.com (E5 Trial)
- **Global Administrator**: chrisadmin@CoporateITsolutions.onmicrosoft.com
- **On-Premises Integration**: Users synced from chrisadmin.lab via Entra Connect

## Steps Performed

### 1. Microsoft 365 Admin Center Overview
- Accessed Microsoft 365 Admin Center (admin.microsoft.com)
- Explored service health, user management, and licensing
- Navigated through various admin centers (Exchange, Teams, SharePoint, Intune)

### 2. User Licensing
- Assigned Microsoft 365 E5 licenses to synced domain users
- Verified users received proper licenses for Exchange, Teams, SharePoint, and Intune

### 3. Exchange Online Administration
- Created a Shared Mailbox: `mailbox@CoporateITsolutions.onmicrosoft.com`
- Configured mailbox delegation:
  - Granted **Full Access** and **Send As** permissions to users (`john`, `sarah`)
- Tested sending and receiving emails using the shared mailbox

### 4. Teams Administration
- Accessed Teams Admin Center
- Created a new Team: "Drivers Team"
- Configured basic messaging and meeting policies
- Simulated team collaboration environment

### 5. SharePoint Administration
- Accessed SharePoint Admin Center
- Created a new SharePoint Site: "Drivers"
- Configured external sharing settings
- Simulated document collaboration setup

### 6. Shared Mailbox Simulation (Real-World Usage)
- Added users to the shared mailbox via Exchange Admin Center
- Successfully opened the shared mailbox from Client01 virtual machine using Sarah's domain user account chrisadmin/sarah on Outlook 
- Simulated real business scenarios:
  - Sending emails as the shared mailbox
  - Receiving and organizing emails
  - Creating folders for better email management

## Challenges & Lessons Learned
- Understanding the difference between Full Access and Send As permissions
- Proper configuration of shared mailboxes is critical for team collaboration in corporate environments
- Microsoft 365 services are tightly integrated — changes in one area (e.g., licensing) affect others

## Key Skills Demonstrated
- Microsoft 365 tenant and service administration
- Exchange Online mailbox management and delegation
- Teams and SharePoint site configuration
- Shared resource management for business operations
- Practical IT Support knowledge for user productivity tools

## Verification
- Users can access licensed services
- Shared mailbox working correctly for multiple users
- Teams and SharePoint sites successfully created and accessible
