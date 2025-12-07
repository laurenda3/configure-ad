# On-Premises Active Directory Deployed in Azure

![Active Directory](https://img.shields.io/badge/Active_Directory-0078D4?style=flat&logo=microsoft&logoColor=white)
![Windows Server](https://img.shields.io/badge/Windows_Server_2022-0078D4?style=flat&logo=windows&logoColor=white)
![Azure](https://img.shields.io/badge/Azure-0078D4?style=flat&logo=microsoft-azure&logoColor=white)

## 📖 Overview

This project demonstrates the deployment and configuration of **Active Directory Domain Services (AD DS)** on a Windows Server 2022 virtual machine in Microsoft Azure. It showcases core IT infrastructure skills including domain controller setup, organizational unit management, user account creation, and group policy administration.

**Skills Demonstrated:**
- Windows Server administration
- Active Directory Domain Services configuration
- User and computer management
- Organizational Unit (OU) design
- Security group administration
- Azure cloud infrastructure

---

## 🏗️ Lab Architecture

**Environment:**
- **Cloud Platform**: Microsoft Azure
- **Domain Controller**: Windows Server 2022 (VM: DC-1)
- **Domain**: homelab.local
- **DNS/DHCP**: Configured on Domain Controller
- **Network**: Azure Virtual Network with Network Security Groups

**Components:**
- 1x Windows Server 2022 VM (Domain Controller)
- Active Directory Domain Services role
- DNS Server role
- Custom Organizational Units
- Multiple user accounts across different OUs

---

## 🚀 Implementation Steps

### Part 1: Deploy Windows Server in Azure

**1. Create Azure Resources**
- Resource Group: `AD-Lab-RG`
- Region: Central US
- Virtual Network: Auto-created

**2. Create Windows Server 2022 VM**
- VM Name: `DC-1`
- Size: Standard_D2s_v3 (2 vCPU, 8 GB RAM)
- OS: Windows Server 2022 Datacenter
- Authentication: Password (labuser)
- Networking: RDP (3389) enabled

![Server Manager Dashboard](assets/Screenshot%202025-12-06%20175438.png)

---

### Part 2: Install and Configure Active Directory

**3. Install AD DS Role**
1. Open **Server Manager**
2. Click **Add roles and features**
3. Select **Active Directory Domain Services**
4. Add required features
5. Complete installation

![Installing AD DS](assets/Screenshot%202025-12-06%20175859.png)

**4. Promote to Domain Controller**
1. Click post-deployment notification
2. Select **Promote this server to a domain controller**
3. Choose **Add a new forest**
4. Root domain name: `homelab.local`
5. Set DSRM password
6. Configure DNS automatically
7. Complete promotion (server restarts)

![Domain Controller Promotion](assets/Screenshot%202025-12-06%20175944.png)

![DC Configuration](assets/Screenshot%202025-12-06%20180323.png)

---

### Part 3: Create Organizational Structure

**5. Open Active Directory Users and Computers**
- Server Manager → **Tools** → **Active Directory Users and Computers**

**6. Create Organizational Units**

Created the following OUs to organize users and resources:
- **_ADMINS** - For domain administrator accounts
- **_EMPLOYEES** - For standard user accounts
- **_COMPUTERS** - For computer objects
- **_SYSADMINS** - For system administrator accounts

![OU Structure](assets/Screenshot%202025-12-06%20182812.png)

---

### Part 4: User Account Management

**7. Create Administrative User**

Created domain admin account:
- **Name**: Jane Admin
- **Username**: jane.admin
- **Location**: _SYSADMINS OU
- **Group Membership**: Domain Admins

![Jane Admin User](assets/Screenshot%202025-12-06%20182839.png)

**8. Verify Admin Privileges**

Confirmed Jane Admin is member of Domain Admins group:

![Domain Admin Membership](assets/Screenshot%202025-12-06%20183046.png)

**9. Create Standard Users**

Created multiple employee accounts:
- Bob Martinez
- John Smith
- Lisa Davis  
- Mike Jones
- Sarah Johnson

All users placed in **_EMPLOYEES** OU with appropriate permissions.

![Employee Users](assets/Screenshot%202025-12-06%20183015.png)

---

## 🎓 What I Learned

Through this project, I gained hands-on experience with:

- ✅ **Windows Server 2022** installation and configuration
- ✅ **Active Directory Domain Services** deployment
- ✅ **Domain Controller** promotion and management
- ✅ **DNS Server** automatic configuration
- ✅ **Organizational Unit** design and best practices
- ✅ **User account creation** and management
- ✅ **Security group** administration (Domain Admins)
- ✅ **Azure Virtual Machine** deployment and management
- ✅ **Remote Desktop** connectivity and administration
- ✅ **Enterprise-level identity management** concepts

---

## 🛠️ Technologies Used

- **Cloud Platform**: Microsoft Azure
- **Operating System**: Windows Server 2022 Datacenter
- **Directory Services**: Active Directory Domain Services (AD DS)
- **DNS**: Microsoft DNS Server
- **Tools**: Server Manager, Active Directory Users and Computers
- **Remote Access**: Remote Desktop Protocol (RDP)

---

## 📝 Key Takeaways

**Active Directory Best Practices:**
- Use Organizational Units to logically group users and resources
- Separate admin accounts from standard user accounts
- Follow naming conventions (e.g., `_ADMINS`, `_EMPLOYEES`)
- Implement principle of least privilege
- Document your OU structure and naming scheme

**Azure Deployment:**
- Windows Server VMs in Azure provide full on-premises AD functionality
- Network Security Groups control access (RDP, etc.)
- Proper VM sizing is important (D-series for Windows Server)
- Stop/deallocate VMs when not in use to save costs

**Real-World Applications:**
- Centralized user authentication and authorization
- Single sign-on (SSO) across enterprise resources
- Group Policy management for security and configuration
- Scalable identity management for organizations
- Foundation for Microsoft 365/Azure AD integration

---

## 🧹 Cleanup

To avoid ongoing Azure charges, resources were stopped/deleted:

**Option 1: Stop VM** (preserves configuration)
```
Azure Portal → Virtual Machines → DC-1 → Stop
```

**Option 2: Delete Resources** (removes everything)
```powershell
Remove-AzResourceGroup -Name "AD-Lab-RG" -Force
```

---

## 📚 Relevant Job Skills

This project directly demonstrates skills required for:
- **Desktop/Server Support Technician** roles
- **Systems Administrator** positions
- **IT Support Specialist** roles
- **Junior Network Administrator** positions

**Specific competencies shown:**
- Understanding of Active Directory, DHCP, and DNS
- Windows Server installation and configuration
- User account creation and management
- Cloud infrastructure (Azure) experience
- Remote server administration
- IT security best practices

---

## 📝 License

This is a learning project for IT portfolio demonstration purposes.
