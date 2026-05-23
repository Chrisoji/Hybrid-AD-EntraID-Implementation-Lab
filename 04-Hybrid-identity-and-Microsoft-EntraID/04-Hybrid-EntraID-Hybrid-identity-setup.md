# Phase 4: Hybrid Identity with Microsoft Entra ID

## Objective
To implement a complete **Hybrid Identity** solution by connecting on-premises Active Directory with Microsoft Entra ID. This phase demonstrates real enterprise skills in identity synchronization, device management, troubleshooting, and access control.

## Lab Context
This setup simulates a modern corporate environment where an organization runs traditional on-premises Active Directory while leveraging Microsoft cloud services for productivity and security.

## Environment Details
- **On-Premises Domain**: `chrisadmin.lab`
- **Domain Controller**: DC01 (Windows Server 2022, dynamic IP)
- **Client Machines**: Client01 & Client02 (Windows 10 Pro)
- **Microsoft Entra ID Tenant**: `CoporateITsolutions.onmicrosoft.com`
- **Global Admin**: `chrisadmin@CoporateITsolutions.onmicrosoft.com`

## Steps Performed

### 1. Microsoft 365 Tenant Creation
- Created a Microsoft 365 E5 Trial tenant after the Developer Program was unavailable.
- Configured the tenant and noted Global Administrator credentials.

### 2. Microsoft Entra Connect Installation
- Downloaded and installed Microsoft Entra Connect on DC01.
- Chose **Custom** installation path (not Express Settings).
- Installed necessary prerequisites and modules.

### 3. Entra Connect Configuration
- Configured **Password Hash Synchronization (PHS)** as the primary sign-in method.
- Performed detailed **Domain and OU Filtering**:
  - Initially synced only custom OUs (IT, Operations, Drivers, Finance, Sales).
  - Later added the **Computers** container after troubleshooting.
- Configured device options for **Hybrid Azure AD Join**.
- Attempted to enable Seamless Single Sign-On.

### 4. Synchronization & Troubleshooting
- Performed initial user synchronization.
- Encountered and resolved `error_missing_device` during Hybrid Join.
- Added the **Computers** container into the list of OUs and domains filtered to be synced with EntraID.
- Reconfigured Entra Connect synchronization scope and ran full initial sync (`Start-ADSyncSyncCycle -PolicyType Initial`).

### 5. Hybrid Azure AD Join
- Successfully joined Client01 to Hybrid Azure AD.
- Verified using `dsregcmd /status`:
  - `AzureAdJoined: YES`
  - `DomainJoined: YES`

### 6. Single Sign-On (SSO) Testing & Validation
- Configured Single Sign-On in Entra Connect.
- Tested access using multiple domain users (`john`, `sarah`).
- **Achieved**: Regular SSO — users can log in once and access Microsoft 365 services.
- **Not Achieved**: Seamless SSO (`AzureAdPrt` remained `NO`). This limitation is common in lab environments using non-routable domains and dynamic IPs.
- Successfully logged into Microsoft 365 as `sarah` from Client01 (on-premises domain-joined machine).
- Verified sign-in events in Microsoft Entra ID audit logs.

## Challenges Encountered & Resolutions
- **Hybrid Join failure (`error_missing_device`)**: Resolved by moving computer objects into a managed OU and re-synchronizing.
- **Seamless SSO not functioning**: Regular SSO works reliably. Full Seamless SSO will be revisited during the Intune phase.
- Dynamic IP on Domain Controller caused occasional sync instability.
- Non-verified internal domain (`chrisadmin.lab`) limited some cloud features.

## Lessons Learned
- Careful OU design and object placement is critical for successful synchronization.
- Computer objects must be synchronized for Hybrid Azure AD Join.
- Troubleshooting hybrid identity issues requires patience and systematic testing.
- Regular SSO already provides major productivity benefits in corporate environments.

## Verification Commands
```powershell
# On DC01
Get-ADSyncScheduler
Start-ADSyncSyncCycle -PolicyType Initial

# On Client machines
dsregcmd /status
gpresult /r /scope user
