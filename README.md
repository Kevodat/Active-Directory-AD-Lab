# Enterprise Active Directory & Group Policy Deployment Lab

## Executive Summary
Designed, deployed, and configured a functional Active Directory Domain Services (AD DS) environment in Oracle VirtualBox. Implemented core network infrastructure services (DNS routing, static IP configuration), established an enterprise Organizational Unit (OU) structure, joined a Windows 11 endpoint, and enforced baseline security policies via Group Policy Objects (GPOs).

---

## Technical Environment & Architecture
- **Hypervisor:** Oracle VM VirtualBox
- **Virtual Network:** `AD-Lab-Network` (10.0.2.0/24 NAT Network)
- **Domain Controller (`DC-01`):** Windows Server 2022 | IP: `10.0.2.10` | Domain: `ad-lab.local`
- **Client Workstation (`Sales-Client`):** Windows 11 Enterprise | Joined to `ad-lab.local`

---

## Core Implementation Highlights

### 1. Domain Controller Provisioning & Network Configuration
- Configured static IPv4 settings (`10.0.2.10/24`) and assigned `127.0.0.1` local loopback for internal DNS resolution.
- Promoted the server to Root Domain Controller for `ad-lab.local`.
- Established custom Organizational Units (OUs): `_ADMINS`, `_EMPLOYEES`, and `_WORKSTATIONS`.

### 2. Network Troubleshooting & Domain Integration
- Identified and resolved dynamic IP assignment conflicts (`10.2.0.10` mismatch vs. `10.0.2.10` subnet) to restore network reachability.
- Validated cross-system connectivity and hostname resolution using `ping` and `nslookup ad-lab.local`.
- Successfully joined `Sales-Client` (Windows 11) to the domain and re-housed the object into the `_WORKSTATIONS` OU.

### 3. Group Policy Management (GPO)
- Authored and linked `Workstation_Security` to the `_WORKSTATIONS` OU in `gpmc.msc`.
- Configured interactive logon security notices (`AD-LAB AUTHORIZED ACCESS ONLY`) demanding authorization acknowledgement prior to authentication.
- Forced domain policy updates using `gpupdate /force` and verified lock-screen enforcement.

---

## Project Verification & Visual Documentation

### Phase 1: Domain Controller & Network Setup

#### Network Setup
![Network Setup](images/AD%20Project/01-network-setup.png)

#### Server Installation
![Server Installed](images/AD%20Project/02-windows-server-installed.png)

#### Static IP Configuration
![Static IP & Renamed](images/AD%20Project/03-dc01-static-ip-renamed.png)

#### AD DS Domain Promotion
![Domain Promoted](images/AD%20Project/04-ad-ds-domain-promoted.png)

#### OU & Admin Account Creation
![OUs & Admin Created](images/AD%20Project/05-ou-and-admin-created.png)

---

### Phase 2: Workstation Integration & Security Enforcement

#### Client DNS Resolution
![Client DNS Configured](images/AD%20Project/06-client-dns-configured.png)

#### Domain Join Success
![Domain Join Success](images/AD%20Project/07-domain-join-success.png)

#### ADUC Workstation Placement
![Workstation in ADUC](images/AD%20Project/08-client-in-aduc.png)

#### Active Domain User Session
![Domain User Login](images/AD%20Project/09-domain-user-login.png)

#### Interactive Logon GPO Enforced
![GPO Enforced](images/AD%20Project/10-gpo-enforced.png)
