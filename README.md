# Windows Active Directory Security Home Lab

## Lab Architecture Overview
This lab features an isolated corporate environment designed to mimic standard enterprise directory services and client systems. 

| Machine Name | Operating System | IP Address | Network Role |
| :--- | :--- | :--- | :--- |
| **DC-01** | Windows Server 2022 | `192.168.10.10` | Domain Controller & DNS Server |
| **Workstation-01** | Windows 11 Enterprise | `192.168.10.20` | Domain Joined Employee Desktop |

## Step-by-Step Implementation Details

### 1. Network & Domain Controller Provisioning
- Deployed a virtualized environment using **VMware Workstation Pro** configured with an isolated **Host-Only** network adapter.
- Configured a static IP framework on `DC-01` pointing to the local loopback address (`127.0.0.1`) for primary naming services.
- Installed **Active Directory Domain Services (AD DS)** and promoted the host to a root forest node named `cyberlab.local`.
- Created an Organizational Unit (OU) named `Employees` and provisioned a standard user profile (`jdoe`).

### 2. Client Workstation Integration
- Deployed **Windows 11 Enterprise** onto an independent virtual asset.
- Tailored network configurations to target `192.168.10.10` as the Preferred DNS handler.
- Authorized and completed a secure domain merge process using primary network administrative credentials.

## Verification of Target Domain Integration
Below is confirmation of the successful registration and integration of `Workstation-01` into the target `cyberlab.local` naming infrastructure:

![Domain Join Success](./screenshots/domain_join.png)






## Active Directory Group Policy Enforcements & Threat Simulations
- **Security Hardening:** Provisioned custom Domain Group Policies (GPOs) modifying default account security registers to actively limit maximum unauthenticated logon threshold cycles to **5 invalid attempts**.
- **Brute-Force Execution:** Simulated an automated credential stuffing scenario on endpoint nodes targeting standard organizational user containers.
- **Incident Response Artifacts:** Successfully caught and investigated **Event ID 4740 (Account Lockout)** entries across domain system controllers, tracking execution chains back to source identifiers (`Workstation-01`) and target victims (`CYBERLAB\jdoe`).

### Threat Simulation Forensic Artifacts

**Figure 4.1: Domain Group Policy Hardening Rules**
![Active Directory Account Lockout Policy Settings](gpo-policy.png)

**Figure 4.2: Event ID 4740 Forensic Discovery - Target Account Identified**
![Windows Event ID 4740 Target Account Log](event-4740-account.png)

**Figure 4.3: Event ID 4740 Forensic Discovery - Attack Source Tracked**
![Windows Event ID 4740 Source Workstation Log](event-4740-source.png)

