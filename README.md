# Windows Active Directory Security Home Lab

## 📊 Lab Architecture Overview
This lab features an isolated corporate environment designed to mimic standard enterprise directory services and client systems. 

| Machine Name | Operating System | IP Address | Network Role |
| :--- | :--- | :--- | :--- |
| **DC-01** | Windows Server 2022 | `192.168.10.10` | Domain Controller & DNS Server |
| **Workstation-01** | Windows 11 Enterprise | `192.168.10.20` | Domain Joined Employee Desktop |

## 🛠️ Step-by-Step Implementation Details

### 1. Network & Domain Controller Provisioning
- Deployed a virtualized environment using **VMware Workstation Pro** configured with an isolated **Host-Only** network adapter.
- Configured a static IP framework on `DC-01` pointing to the local loopback address (`127.0.0.1`) for primary naming services.
- Installed **Active Directory Domain Services (AD DS)** and promoted the host to a root forest node named `cyberlab.local`.
- Created an Organizational Unit (OU) named `Employees` and provisioned a standard user profile (`jdoe`).

### 2. Client Workstation Integration
- Deployed **Windows 11 Enterprise** onto an independent virtual asset.
- Tailored network configurations to target `192.168.10.10` as the Preferred DNS handler.
- Authorized and completed a secure domain merge process using primary network administrative credentials.

## 🖼️ Verification of Target Domain Integration
Below is confirmation of the successful registration and integration of `Workstation-01` into the target `cyberlab.local` naming infrastructure:

![Domain Join Success](./screenshots/domain_join.png)