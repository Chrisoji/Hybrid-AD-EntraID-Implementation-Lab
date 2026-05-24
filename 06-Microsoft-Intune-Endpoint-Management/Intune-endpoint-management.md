# Phase 6: Microsoft Intune & Endpoint Management

## Objective
To demonstrate a strong understanding of Microsoft Intune as a modern endpoint management platform and explain how it is administered in a hybrid Active Directory environment.

## What is Microsoft Intune?

Microsoft Intune is a cloud-based service within the Microsoft Endpoint Manager suite. It provides centralized management of devices (Windows, macOS, iOS, Android), application deployment, security policy enforcement, and compliance monitoring.

In a **hybrid environment** (on-premises Active Directory + Microsoft Entra ID), Intune works alongside Hybrid Azure AD Join to allow organizations to manage devices using both traditional Group Policy and modern cloud-based policies.

## Lab Environment Used for Explanation
- **On-Premises Domain**: chrisadmin.lab (Windows Server 2022)
- **Domain Controller**: DC01
- **Client Devices**: Client01 & Client02 (Windows 10 Pro, Hybrid Azure AD Joined)
- **Identity**: Users synchronized from on-premises AD using Microsoft Entra Connect
- **Microsoft 365 Tenant**: CoporateITsolutions.onmicrosoft.com with E5 licensing

## How to Administer Microsoft Intune in a Hybrid Environment

### 1. Initial Setup and Integration
- Access the Intune portal at [https://intune.microsoft.com](https://intune.microsoft.com)
- Verify integration with Microsoft Entra ID
- Ensure devices are Hybrid Azure AD Joined before attempting MDM enrollment
- Assign Microsoft 365 E5 licenses (which include Intune) to users

### 2. Device Enrollment
In a hybrid setup, devices are typically enrolled using one of these methods:
- Automatic enrollment via Group Policy (for Windows 10/11)
- Manual enrollment using the Company Portal app
- Settings → Accounts → Access work or school → Enroll in MDM only

Once enrolled, devices appear in Intune as **Hybrid Azure AD joined** and **MDM enrolled**.

### 3. Configuration Profiles
Configuration Profiles are used to manage device settings at scale. Common examples include:

- **Device Restrictions**: Control password requirements, camera usage, Microsoft Edge settings, etc.
- **Administrative Templates**: Deploy registry-based settings (similar to Group Policy)
- **Endpoint Protection**: Configure Microsoft Defender Antivirus, firewall, and attack surface reduction rules
- **Custom Profiles**: Deploy PowerShell scripts or OMA-URI settings

These profiles are assigned to user groups or device groups and take precedence over traditional Group Policy in many modern scenarios.

### 4. Compliance Policies
Compliance policies define the minimum security standards a device must meet. Examples include:
- Require BitLocker encryption
- Minimum OS version
- Microsoft Defender real-time protection enabled
- Device must not be jailbroken/rooted

Non-compliant devices can be blocked from accessing corporate resources using Conditional Access.

### 5. Application Management
Intune allows administrators to:
- Deploy Microsoft 365 Apps (Outlook, Teams, Office suite)
- Deploy Win32 applications using IntuneWin format
- Configure App Protection Policies to protect corporate data on managed devices
- Use Required or Available deployment types

### 6. Security & Conditional Access Integration
Intune integrates with Microsoft Entra ID Conditional Access to enforce rules such as:
- Block access from non-compliant devices
- Require MFA for high-risk sign-ins
- Enforce app-based Conditional Access

## Best Practices in Hybrid Environments
- Use co-management with Configuration Manager (if present) or Group Policy + Intune
- Start with pilot groups before broad deployment
- Monitor compliance reports regularly
- Combine Intune policies with on-premises Group Policy during transition

## Real-World Value
In a corporate environment, Intune enables:
- Consistent security posture across on-premises and remote devices
- Faster application deployment and updates
- Reduced management overhead compared to traditional tools
- Better support for hybrid work models

This lab demonstrates the foundational knowledge required to successfully implement and administer Intune in production hybrid environments.
