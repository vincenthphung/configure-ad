# 🌐 On-premises Active Directory Deployment in Azure Virtual Machines

![Active Directory Logo](https://i.imgur.com/pU5A58S.png)

Dive into the seamless deployment of an on-premises Active Directory within Azure Virtual Machines. This streamlined guide will help you set up Active Directory Domain Services (AD DS) on Windows Server 2022 and connect a Windows 10 client. Let's embark on this journey with step-by-step instructions, enriched with illustrative visuals.

---

## 🛠 **Tools & Systems**

- **Platforms**: 
  - 🌩 Microsoft Azure (Virtual Machines)
  - 🖥 Remote Desktop
  
- **Technologies**: 
  - 📂 Active Directory Domain Services
  - 💻 PowerShell
  
- **Operating Systems**: 
  - 🖥 Windows Server 2022
  - 💼 Windows 10 (21H2)

---

## 🚀 **Setup Steps**:

1. **Azure Resource Setup**
   - 📁 Establish a Resource Group and Virtual Network in Azure.
   - 🖥 Deploy a Windows Server 2022 VM named "DC-1" and a Windows 10 VM named "Client-1".
   - 🌐 Assign DC-1 VM's NIC Private IP to static.
   
   ![Azure Resources](https://github.com/JasonDelahoussaye/Configuring_On-premises_Active_Directory_within_Azure_VMs/assets/106440235/144ab003-2e2f-4fa7-8ebf-9b666b48df62)

2. **Client-Domain Controller Connectivity**
   - 📡 Test connectivity from Client-1 to DC-1's private IP.
   - 🛠 If unsuccessful, activate ICMPv4 in DC-1's Windows Firewall.
   - ✅ Ensure a successful connection.
   
   ![Connectivity Check](https://github.com/JasonDelahoussaye/Configuring_On-premises_Active_Directory_within_Azure_VMs/assets/106440235/d809e457-52fb-4f89-8488-5d358cdd7456)

3. **Active Directory Installation**
   - 🖥 Access DC-1 and kickstart the Active Directory Domain Services installation.
   - 🌍 Elevate DC-1 to a domain controller role and establish a new domain.
   
   ![AD Installation](https://github.com/JasonDelahoussaye/Configuring_On-premises_Active_Directory_within_Azure_VMs/assets/106440235/1c2424f1-6368-42ae-a6db-de3e15387d8f)

4. **User Account Creation in AD**
   - 📂 Navigate to Active Directory Users and Computers on DC-1.
   - 🚀 Construct Organizational Units: "_EMPLOYEES" and "_ADMINS".
   - 🙍‍♀️ Generate a user account for "Jane Doe" and integrate her into the "Domain Admins" group.
   
   ![User Creation](https://github.com/JasonDelahoussaye/Configuring_On-premises_Active_Directory_within_Azure_VMs/assets/106440235/2e4f6f3f-f53f-4712-8fa3-6e2a5cd5adbc)

5. **Integrate Client-1 with the Domain**
   - 🌐 Configure Client-1's DNS to mirror DC-1's private IP.
   - 🔄 Reboot Client-1, sign in, and integrate with the domain.
   
   ![Client Domain Integration](https://github.com/JasonDelahoussaye/Configuring_On-premises_Active_Directory_within_Azure_VMs/assets/106440235/a915e2b9-bc20-4684-af8e-43358e8c2828)

6. **Enable Remote Desktop for Non-Admin Users**
   - 🖥 On Client-1, configure Remote Desktop for "domain users".
   
   ![Remote Desktop Configuration](https://github.com/JasonDelahoussaye/Configuring_On-premises_Active_Directory_within_Azure_VMs/assets/106440235/886be92c-556d-4fb8-99da-f3b37e908b3a)

7. **Generate More User Accounts & Test**
   - 🚀 On DC-1, execute the PowerShell script to produce additional user accounts.
   - ✅ Confirm the creation and test the new accounts.
   
   ![User Test](https://github.com/JasonDelahoussaye/Configuring_On-premises_Active_Directory_within_Azure_VMs/assets/106440235/11e109b3-50d0-4e26-8c6e-b1b99215eb62)

---

By adhering to this guide, you'll be equipped with a robust on-premises Active Directory on Azure VMs, primed for efficient user and resource management.

## 🌟 **In Summary**

This guide illuminated the steps for deploying an on-premises Active Directory on Azure VMs. From VM creation, network configuration, to Active Directory installation and user management, we've got you covered.
