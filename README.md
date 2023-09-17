# On-premises Active Directory Deployment in Azure Virtual Machines

![Active Directory Logo](https://i.imgur.com/pU5A58S.png)

This guide will walk you through the deployment of an on-premises Active Directory within Azure Virtual Machines. We'll simplify the setup of Active Directory Domain Services (AD DS) on a Windows Server 2022 and demonstrate how to connect a Windows 10 client. Follow the step-by-step instructions, complemented by illustrative images.

## Tools & Systems

- **Platforms**: Microsoft Azure (Virtual Machines), Remote Desktop
- **Technologies**: Active Directory Domain Services, PowerShell
- **Operating Systems**: Windows Server 2022, Windows 10 (21H2)

## Setup Steps:

1. **Azure Resource Setup**
   - Establish a Resource Group and Virtual Network in Azure.
   - Deploy a Windows Server 2022 VM named "DC-1" and a Windows 10 VM named "Client-1" within the same group and network.
   - Assign DC-1 VM's NIC Private IP to static.
   
   ![Azure Resources](https://github.com/JasonDelahoussaye/Configuring_On-premises_Active_Directory_within_Azure_VMs/assets/106440235/144ab003-2e2f-4fa7-8ebf-9b666b48df62)

2. **Client-Domain Controller Connectivity**
   - From Client-1, attempt to ping DC-1's private IP.
   - If the ping is unsuccessful, activate ICMPv4 in DC-1's Windows Firewall.
   - Ensure a successful ping from Client-1 to DC-1.
   
   ![Connectivity Check](https://github.com/JasonDelahoussaye/Configuring_On-premises_Active_Directory_within_Azure_VMs/assets/106440235/d809e457-52fb-4f89-8488-5d358cdd7456)

3. **Active Directory Installation**
   - Access DC-1 and initiate the installation of Active Directory Domain Services.
   - Elevate DC-1 to the role of a domain controller and establish a new domain (e.g., mydomain.com).
   
   ![AD Installation](https://github.com/JasonDelahoussaye/Configuring_On-premises_Active_Directory_within_Azure_VMs/assets/106440235/1c2424f1-6368-42ae-a6db-de3e15387d8f)

4. **User Account Creation in AD**
   - On DC-1, launch Active Directory Users and Computers.
   - Construct "_EMPLOYEES" and "_ADMINS" Organizational Units.
   - Generate a user account for "Jane Doe" with the username "jane_admin" and incorporate her into the "Domain Admins" group.
   - Sign out and re-access DC-1 as "mydomain.com\jane_admin".
   
   ![User Creation](https://github.com/JasonDelahoussaye/Configuring_On-premises_Active_Directory_within_Azure_VMs/assets/106440235/2e4f6f3f-f53f-4712-8fa3-6e2a5cd5adbc)

5. **Integrate Client-1 with the Domain**
   - Configure Client-1's DNS to mirror DC-1's private IP.
   - Reboot Client-1, sign in as the local admin, and integrate it with the domain.
   - On DC-1, verify Client-1's presence in ADUC under the "Computers" section and transition it to a new "_CLIENTS" OU.
   
   ![Client Domain Integration](https://github.com/JasonDelahoussaye/Configuring_On-premises_Active_Directory_within_Azure_VMs/assets/106440235/a915e2b9-bc20-4684-af8e-43358e8c2828)

6. **Enable Remote Desktop for Non-Admin Users**
   - On Client-1, signed in as "mydomain.com\jane_admin", configure Remote Desktop for "domain users".
   
   ![Remote Desktop Configuration](https://github.com/JasonDelahoussaye/Configuring_On-premises_Active_Directory_within_Azure_VMs/assets/106440235/886be92c-556d-4fb8-99da-f3b37e908b3a)

7. **Generate More User Accounts & Test**
   - On DC-1, as "mydomain.com\jane_admin", execute the provided PowerShell script to produce additional user accounts.
   - Confirm the creation of these accounts in ADUC.
   - Attempt to sign into Client-1 using one of the newly minted user accounts.
   
   ![User Test](https://github.com/JasonDelahoussaye/Configuring_On-premises_Active_Directory_within_Azure_VMs/assets/106440235/11e109b3-50d0-4e26-8c6e-b1b99215eb62)

By adhering to this guide, you'll successfully deploy an on-premises Active Directory on Azure VMs, primed for user and resource management.

## In Summary

This guide detailed the procedure for deploying an on-premises Active Directory on Azure VMs. The steps encompassed VM creation, network configuration, Active Directory installation, user account generation, and testing the entire setup.
