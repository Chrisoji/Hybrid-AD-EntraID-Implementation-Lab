# Phase 1: VMware Environment Setup

## Objective
Build a stable virtualized lab environment to simulate a corporate enterprise IT infrastructure for testing Active Directory, Group Policy, and IT support scenarios.

## Lab Architecture
- **Hypervisor**: VMware Workstation (NAT Network)
- **Domain Controller**: Windows Server 2022 (`DC01`)
- **Client Machines**: Windows 10 Pro (`Client01`, `Client02`)
- **Networking**: NAT (VMnet8) with DHCP

## Steps Performed

### 1. VMware Network Configuration
- Configured VMnet8 as NAT
- Subnet: `192.168.100.0/24`
- Enabled VMware DHCP service

### 2. Virtual Machine Creation
- **DC01**: Windows Server 2022 Datacenter Evaluation, 4 GB RAM, 2 vCPU, 60 GB disk (with second 20 GB disk for AD logs)
- **Client01 & Client02**: Windows 10 Pro, 4 GB RAM each, 60 GB disk

### 3. Network Configuration
- All VMs used dynamic IPs assigned by VMware DHCP:
  - DC01: `192.168.100.128`
  - Client01: `192.168.100.129`
  - Client02: `192.168.100.130`

**Important Decision & Best Practice**:
Even though it is a **Microsoft best practice** to use a static IP address for Domain Controllers, I intentionally kept dynamic addressing for this lab. To maintain stability:
- I limited the DHCP pool in VMware Virtual Network Editor to a small range.
- This ensures each VM consistently receives the same IP address after reboots.
- This approach provided a good balance between lab convenience and maintaining AD stability.

## Challenges & Solutions
- Initial ping worked but no internet in browser → Resolved by configuring DNS forwarders on the Domain Controller (`8.8.8.8` and `1.1.1.1`).

## Verification
```powershell
ipconfig /all
ping 8.8.8.8
ping google.com
ping DC01
