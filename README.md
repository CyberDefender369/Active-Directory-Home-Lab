# Active Directory Home Lab

## Description

This endeavor concentrated on establishing fundamental configurations within Active Directory (AD). The scope of the project included the creation of an Organizational Unit (OU), the deployment of a Domain Controller (DC), and the configuration of a Dynamic Host Configuration Protocol (DHCP) server, among other elements. Basic networking configurations were executed to establish system integration. 

## Languages and Utilities Used

- PowerShell
- VirtualBox

## Environments Used

- Windows 10 
- Windows Server 2019

## Notes

Windows 11 machine randomly appears halfway through the lab because I realized it would be more of a real world situation. That is, IT support/Helpdesk would not normally have direct access to the Domain Controller but instead access Active Directory via their work device. 

## Project Walk-Through:

- Configure internal facing NIC of Windows Server 2022 with a static IP address:
  - Open Network & Internet Settings
  - Change adapter options
  - Properties
  - Double click IPv4
  - IP address: 192.168.0.1/24
  - DNS: 127.0.0.1 (loopback address)

![internal_nic_config](https://github.com/CyberDefender369/Active-Directory-Home-Lab/assets/96165986/2e3fe872-0965-4a68-9aca-bca1446f35f6)


- Install Active Directory Domain Services:
  - Add roles and features
  - Role-based or feature-based installation
  - Select correct server
  - Active Directory Domain Services
  - Confirm installation selections
  - Install

![ad_domain_services](https://github.com/CyberDefender369/Active-Directory-Home-Lab/assets/96165986/192dc1cf-a88b-417b-88f7-f0187bd20bc7)


- Promote server to a domain controller:
  - Add a new forest
  - Root domain name: exampledomain.com
  - DSRM password
  - Install

![promote_server](https://github.com/CyberDefender369/Active-Directory-Home-Lab/assets/96165986/f57c391e-d281-4fd4-a8c5-7c23c03d9e3e)


- After reboot, domain will appear. 

![domain](https://github.com/CyberDefender369/Active-Directory-Home-Lab/assets/96165986/9404ce63-6084-40cc-9515-3aff97721908)


- Create an Admins Organizational Unit:
  - Active Directory Users and Computers
  - Right click domain
  - New
  - Organizational Unit
  - OU name: Admins

![admin_OU](https://github.com/CyberDefender369/Active-Directory-Home-Lab/assets/96165986/2a9ab315-200d-45a2-a07c-303d354ead06)


- Add new user to Admins (this user will be the helpesk technician):
  - Right click Admins
  - New
  - User
  - Fill out information
  - Password never expires (not recommended)
  - Finish

![admin_user](https://github.com/CyberDefender369/Active-Directory-Home-Lab/assets/96165986/cc353d06-f651-4e87-9c58-aea2ddd94d29)


- Give helpdesk technician admin rights:
  - Right click John Doe
  - Properties
  - Member of
  - Add
  - Domain Admins
  - Apply
  - Ok
 
![domain_admin](https://github.com/CyberDefender369/Active-Directory-Home-Lab/assets/96165986/837e898a-d530-43f2-91cd-3fcb577265b9)


- Sign out, then sign in as helpdesk technician.

![dedicated_domain_admin](https://github.com/CyberDefender369/Active-Directory-Home-Lab/assets/96165986/7d4fc74d-1d03-4108-8c46-7df55d3fd7e1)


- Install Network Address Translation:
  - Add roles and features
  - Role-based or feature-based installation
  - Select correct server
  - Remote Access
  - Routing
  - Install

![install_nat](https://github.com/CyberDefender369/Active-Directory-Home-Lab/assets/96165986/635e6993-fc9b-4a41-a7ed-8d4e328cc8ab)


- Configure Routing and Remote Access Server:
  - Tools
  - Routing and Remote Access
  - Configure and Enable Routing and Remote Access
  - NAT
  - External NIC
  - Finish
  - Green arrow signifies that NAT is now operational

![routing_remote_access_config](https://github.com/CyberDefender369/Active-Directory-Home-Lab/assets/96165986/a3998a92-a948-47f6-af95-2b64b763740e)


- Install DHCP Server:
  - Add roles and feautures
  - Select correct server 
  - DHCP Server
  - Install

![dhcp_server](https://github.com/CyberDefender369/Active-Directory-Home-Lab/assets/96165986/a42f6bfe-7f9a-4f29-8cdd-287edeecc82b)


- Configure DHCP scope:
  - Tools
  - DHCP
  - Right click IPv4
  - New scope
  - Name scope
  - Default gateway
  - Finish
  - Authorize
  - Refresh
 
![dhcp_config](https://github.com/CyberDefender369/Active-Directory-Home-Lab/assets/96165986/129a3d55-818a-45ae-944a-959b25d050be)


- Ran a PowerShell script that created an OU named Users01 and a 1,000 new users.

![powershell_script](https://github.com/CyberDefender369/Active-Directory-Home-Lab/assets/96165986/31816c61-57ca-4a83-b508-4a42997fcca0)


- Confirm network configuration of Windows 10 client (employee computer):
  - Command Prompt
  - Enter ipconfig 
  - Ping Google.com
    
![network_config](https://github.com/CyberDefender369/Active-Directory-Home-Lab/assets/96165986/8b5c63e0-567c-4a0b-9f90-eb38036b8f69)


- Join the domain:
  - Right click start menu
  - System
  - Rename this PC (advanced)
  - Change
  - Domain
  - Enter exampledomain.com
  - Enter admin credentials
  - Restart

![join_domain](https://github.com/CyberDefender369/Active-Directory-Home-Lab/assets/96165986/3efc5863-4c59-4e9f-bd88-3ee6e3bb217d)


- Confirm DHCP server is leasing IP addresses properly:
  - Tools
  - DHCP
  - IPv4
  - Scope
  - Address leases

![dhcp_proper](https://github.com/CyberDefender369/Active-Directory-Home-Lab/assets/96165986/5b39ded2-953b-4532-bc39-4bc33ed01875)


- Confirm employee computer joined domain:
  - Windows Adminstrative Tools
  - Active Directory Users and Computers
  - Computers

![domain_joined](https://github.com/CyberDefender369/Active-Directory-Home-Lab/assets/96165986/d0a74baf-8162-4f18-9522-0ef1aacc2765)


- Login in as another user (new employee).

![other_user](https://github.com/CyberDefender369/Active-Directory-Home-Lab/assets/96165986/bb86efea-3e9b-44ba-9057-4be2084db477)

