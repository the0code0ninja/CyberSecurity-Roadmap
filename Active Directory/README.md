# Active Directory Basics 🛡️💻

A comprehensive reference guide covering fundamental concepts of **Windows Domains**, **Active Directory Domain Services (AD DS)**, **Authentication Mechanisms** (Kerberos & NTLM), **Group Policies**, **Domain Hierarchies**, and **Azure Active Directory**.

---

## 📌 Table of Contents
1. [Introduction to Windows Domains](#1-introduction-to-windows-domains)
2. [Active Directory Domain Services (AD DS)](#2-active-directory-domain-services-ad-ds)
3. [Security Principals](#3-security-principals)
   - [Users](#users)
   - [Machines / Computers](#machines--computers)
   - [Security Groups](#security-groups)
4. [Organizational Units (OUs)](#4-organizational-units-ous)
   - [Security Groups vs. OUs](#security-groups-vs-ous)
   - [Managing OUs & Accidental Deletion Protection](#managing-ous--accidental-deletion-protection)
   - [Delegation of Control](#delegation-of-control)
   - [Managing Computers in AD](#managing-computers-in-ad)
5. [Domain Policies & Group Policy Objects (GPOs)](#5-domain-policies--group-policy-objects-gpos)
   - [GPO Architecture & Linking](#gpo-architecture--linking)
   - [Configuring GPOs](#configuring-gpos)
   - [SYSVOL Share & Distribution](#sysvol-share--distribution)
6. [Core Domain Services](#6-core-domain-services)
7. [Authentication Methods](#7-authentication-methods)
   - [Kerberos Authentication](#kerberos-authentication)
   - [NetNTLM Authentication](#netntlm-authentication)
8. [Active Directory Hierarchy](#8-active-directory-hierarchy)
   - [Trees](#trees)
   - [Forests](#forests)
   - [Trust Relationships](#trust-relationships)
9. [AD DS Data Store & Default Groups](#9-ad-ds-data-store--default-groups)
   - [NTDS.dit](#ntdsdit)
   - [Default Security Groups Overview](#default-security-groups-overview)
10. [Azure Active Directory & Cloud Security](#10-azure-active-directory--cloud-security)

---

## 1. Introduction to Windows Domains

A **Windows Domain** is a network architecture where a centralized group of users, computers, and resources fall under the administration of a single organizational entity.

### Key Advantages:
- **Centralized Identity Management:** All user accounts across the network can be configured, updated, and managed from a single central repository.
- **Unified Security Policies:** Administrators can enforce consistent security policies across all machines and users in the network simultaneously.

---

## 2. Active Directory Domain Services (AD DS)

The core component of any Windows Domain is **Active Directory Domain Services (AD DS)**. 
- **Domain Controller (DC):** The server running AD DS is called a Domain Controller. It acts as the central brain of the entire domain.
- **Catalogue / Directory:** AD DS acts as a centralized catalog holding information about all objects on the network (users, groups, workstations, servers, printers, shares, etc.).

---

## 3. Security Principals

A **Security Principal** is any entity that can be authenticated by the system and assigned permissions to network resources.

### Users
Represent two primary types of entities:
- **People:** Employees/persons requiring network access.
- **Services:** Special accounts used to run services like IIS, MSSQL, etc. Service accounts operate with least-privilege principles required for their specific function.

### Machines / Computers
- Every computer joined to an Active Directory domain gets a **Machine Account**.
- Machine accounts are also security principals.
- **Naming Convention:** Machine account names end with a trailing `$` sign (e.g., computer `DC01` has machine account `DC01$`).
- Machine accounts are local administrators on their respective machines and have limited domain rights.

### Security Groups
- Used to assign resource access rights to multiple users/machines at once rather than configuring individual permissions.
- Can contain users, machines, and other nested groups.

#### Important Built-in Domain Groups:
| Security Group | Description |
| :--- | :--- |
| **Domain Admins** | Full administrative rights across the entire domain, including all Domain Controllers and machines. |
| **Domain Controllers** | Contains all Domain Controllers in the domain. |
| **Server Operators** | Can administer Domain Controllers (cannot modify administrative group memberships). |
| **Domain Users** | Contains all existing user accounts in the domain. |
| **Domain Computers** | Contains all workstations and servers joined to the domain. |
| **Backup Operators** | Can access and back up any file on computers regardless of explicit NTFS permissions. |
| **Account Operators** | Allowed to create, modify, and manage user accounts in the domain. |

---

## 4. Organizational Units (OUs)

**Organizational Units (OUs)** are logical container objects used to organize and classify users and machines.

<img width="751" height="535" alt="image" src="https://github.com/user-attachments/assets/6ae7a232-f026-4bc3-9867-c7f38b91e7c6" />


### Built-in Default Containers:
- **Builtin:** Default groups available to any Windows host.
- **Computers:** Default container for newly joined workstations/servers.
- **Domain Controllers:** Default OU containing domain controllers.
- **Managed Service Accounts:** Holds accounts used by domain services.
- **Users:** Default user accounts and domain-wide groups.

### Security Groups vs. OUs
- **OUs:** Used to structure objects and apply **Group Policy Objects (GPOs)**. A user/computer can belong to **only one OU at a time**.
- **Security Groups:** Used to grant **resource permissions** (e.g., share access, NTFS rights). A user/computer can be a member of **multiple Security Groups**.

### Managing OUs & Accidental Deletion Protection
By default, OUs are protected from accidental deletion in Active Directory.

<img width="289" height="113" alt="image" src="https://github.com/user-attachments/assets/ccc6fc80-493a-4f47-ac8f-5a10d6de4a44" />

#### To Delete an OU:
1. Open **Active Directory Users and Computers (ADUC)**.
2. Go to **View** -> Enable **Advanced Features**.
   
<img width="477" height="264" alt="image" src="https://github.com/user-attachments/assets/11b4ed54-266d-4f62-b870-8ddea59b10c7" />

3. Right-click the OU -> Select **Properties** -> Open the **Object** tab.
4. Uncheck **Protect object from accidental deletion** -> Click **OK** / **Apply**.

<img width="276" height="314" alt="image" src="https://github.com/user-attachments/assets/aac8b36d-7f5a-465d-a8d6-b20c20620489" />

### Delegation of Control
Delegation allows Domain Admins to grant specific permissions to non-admin users or helpdesk teams over specific OUs without elevating them to full Domain Admins.

<img width="201" height="247" alt="image" src="https://github.com/user-attachments/assets/07a96267-7b8b-4124-844a-8c6ef743546a" />
<img width="388" height="378" alt="image" src="https://github.com/user-attachments/assets/d4b6617d-10fc-4822-8f47-a6bc6e81dbb0" />
<img width="407" height="320" alt="image" src="https://github.com/user-attachments/assets/9c55b506-45b5-4c92-824a-8a0ecea70250" />




### Managing Computers in AD
Computers can be categorized into sub-OUs (e.g., `Workstations` and `Servers`) to enforce distinct group policies.

<img width="544" height="267" alt="image" src="https://github.com/user-attachments/assets/3b1f8340-1d31-4c32-9f2b-e7b7a124ea09" />

---

## 5. Domain Policies & Group Policy Objects (GPOs)

Domain Policies are set of centralized rules configured by administrators using **Group Policy Objects (GPOs)**.

### Examples of GPOs:
- Enforcing password length/complexity across the domain.
- Enabling/Disabling Windows Defender on workstations.
- Setting SMB Signing policy (`Digitally Sign Communication`).

### GPO Architecture & Linking
- GPOs are created inside **Group Policy Objects** container.
- GPOs are **linked** to domains or OUs.
- Settings apply to the linked OU and **all nested sub-OUs**.
- **Security Filtering:** Can scope GPOs to specific users/groups (default applies to `Authenticated Users`).

<img width="600" height="361" alt="image" src="https://github.com/user-attachments/assets/3b91ba2c-fa93-4640-a7f8-23f39ce1a4ff" />


### Configuring GPOs
View settings via the **Settings** tab or right-click to **Edit** in the Group Policy Management Editor.

<img width="603" height="378" alt="image" src="https://github.com/user-attachments/assets/3c2d7130-f5c6-44c8-a896-fb728688817e" />


<img width="419" height="378" alt="image" src="https://github.com/user-attachments/assets/88717d5c-1d1d-4f1b-9495-dc7b02f47554" />

<img width="572" height="413" alt="image" src="https://github.com/user-attachments/assets/185d5f98-f689-4a14-b699-2e873b2a5903" />

### SYSVOL Share & Distribution
GPOs are synchronized across domain machines via the **SYSVOL** share:
- Path: `C:\Windows\SYSVOL\sysvol\`
- Accessible by all domain users to pull policy updates.

---

## 6. Core Domain Services

Default services provided by Domain Controllers:
- **LDAP (Lightweight Directory Access Protocol):** Facilitates directory querying and updates.
- **Active Directory Certificate Services (AD CS):** Issues, validates, and revokes digital certificates.
- **DNS / LLMNR / NBT-NS:** Handles domain name resolution and local hostname discovery.

---

## 7. Authentication Methods

Domain credentials are stored centrally on Domain Controllers.

<img width="544" height="342" alt="image" src="https://github.com/user-attachments/assets/1c8f1934-229e-4899-8b3d-1a91aef5a750" />

### Kerberos Authentication
The default authentication protocol in modern Active Directory environments.

#### Core Terms:
- **KDC (Key Distribution Center):** Runs on DC; contains Authentication Service (AS) and Ticket Granting Service (TGS).
- **TGT (Ticket Granting Ticket):** Ticket used to request service tickets without re-entering password. Encrypted with `krbtgt` password hash.
- **TGS (Ticket Granting Service / Service Ticket):** Ticket used to access a specific service (e.g., MSSQL, SMB). Encrypted with Service Owner's hash.
- **SPN (Service Principal Name):** Unique identifier for a service instance.
- **Session Key:** Symmetric key generated for secure communication sessions.

#### Kerberos 6-Step Workflow:

<img width="598" height="248" alt="image" src="https://github.com/user-attachments/assets/e582d383-319e-4036-881c-67b05b816f26" />


1. **AS-REQ:** Client sends encrypted timestamp (using user's password hash) to KDC (AS).
2. **AS-REP:** KDC returns **TGT** (encrypted with `krbtgt` hash) and a **Session Key**.

<img width="584" height="268" alt="image" src="https://github.com/user-attachments/assets/68f92d9d-a911-4f49-9dc3-e95f140ab7a9" />

3. **TGS-REQ:** Client sends TGT + requested **SPN** + encrypted timestamp (using Session Key) to KDC (TGS).
4. **TGS-REP:** KDC returns **TGS Ticket** (encrypted with Service Owner Hash) and **Service Session Key**.

<img width="621" height="232" alt="image" src="https://github.com/user-attachments/assets/b03b3050-6d0a-4f15-ba75-1adf69785451" />

5. **AP-REQ:** Client sends TGS Ticket to target Service Server.
6. **AP-REP / Authentication:** Target service decrypts TGS using its account hash and validates access.

---

### NetNTLM Authentication
Legacy challenge-response authentication protocol kept for backward compatibility.

<img width="620" height="349" alt="image" src="https://github.com/user-attachments/assets/2d174af8-f25c-4ca3-a9d4-5461095647c7" />

#### Workflow:
1. **Auth Request:** Client sends authentication request to target server.
2. **Challenge:** Server responds with a random 8-byte **Challenge**.
3. **Response:** Client encrypts challenge using user's **NTLM Hash** and sends **Response**.
4. **Validation:** Server forwards Challenge + Response to DC.
5. **Result:** DC recalculates response using stored NTLM hash and sends Allow/Deny status back to server.

---

## 8. Active Directory Hierarchy

### Trees
A collection of domains forming a contiguous namespace under a Parent-Child domain structure (e.g., `thm.local` -> `uk.thm.local`).

<img width="671" height="504" alt="image" src="https://github.com/user-attachments/assets/3dacba56-3a80-468c-8910-443ba5057557" />

### Forests
A collection of one or more AD trees sharing a common Schema, Global Catalog, and Domain Services. Forms the top-level security boundary.

<img width="622" height="249" alt="image" src="https://github.com/user-attachments/assets/a8ea87a3-e973-4b56-b821-44441b6ee966" />

### Trust Relationships
Allows users in one domain/forest to access resources in another.

<img width="665" height="287" alt="image" src="https://github.com/user-attachments/assets/75890740-08a8-4330-805b-fe52a0dd75d2" />

- **One-Way Trust:** Domain A trusts Domain B (Users in B can access resources in A).
- **Two-Way Trust:** Mutual trust between domains.
- **Transitive Trust:** Trust extends beyond two domains (`A -> B` and `B -> C` implies `A -> C`).

---

## 9. AD DS Data Store & Default Groups

### NTDS.dit
- Main database file containing all AD objects, schemas, and **user password hashes**.
- Default Location: `%SystemRoot%\NTDS\NTDS.dit`
- Accessible only by `NT AUTHORITY\SYSTEM` on Domain Controllers.

### Default Security Groups Overview
- **Enterprise Admins:** Full control across all domains in a forest.
- **Schema Admins:** Allowed to modify Active Directory database schema.
- **DNS Admins:** Manages DNS service configuration.
- **Protected Users:** Enhanced protection against credential caching and weak encryption.
- **Group Policy Creator Owners:** Can create and edit GPOs.

---

## 10. Azure Active Directory & Cloud Security

**Azure AD (Entra ID)** serves as Microsoft's cloud identity solution, bridging physical on-premise AD with cloud services via **Azure AD Connect**.

<img width="618" height="324" alt="image" src="https://github.com/user-attachments/assets/8f096a79-3159-485b-8382-d6db8301f12a" />

### On-Premise AD vs. Azure AD Comparison
| Feature / Service | On-Premise Windows Server AD | Azure Active Directory (Cloud) |
| :--- | :--- | :--- |
| **Protocol** | LDAP / Kerberos / NTLM | REST APIs / OAuth / SAML / OpenID |
| **Structure** | OU Tree & Hierarchy | Flat Structure |
| **Scope** | Domains & Forests | Tenants |
| **Cross-Access** | Trust Relationships | Guest Users |

---
*Created for Active Directory Learning & GitHub Repository Documentation.*
