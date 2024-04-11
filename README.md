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


- Create dedicated domain admin account:
  - Active Directory Users and Computers
  - Right click domain
  - New
  - Organizational Unit
  - OU name: Admins

![admin_OU](https://github.com/CyberDefender369/Active-Directory-Home-Lab/assets/96165986/2a9ab315-200d-45a2-a07c-303d354ead06)


- Add  new user to Admins:
  - Right click Admins
  - New
  - User
  - Fill out information
  - Password never expires (not recommended)
  - Finish

![admin_user](https://github.com/CyberDefender369/Active-Directory-Home-Lab/assets/96165986/cc353d06-f651-4e87-9c58-aea2ddd94d29)


- Make user a domain admin:
  - Right click John Doe
  - Properties
  - Member of
  - Add
  - Domain Admins
  - Apply
  - Ok
 
![domain_admin](https://github.com/CyberDefender369/Active-Directory-Home-Lab/assets/96165986/837e898a-d530-43f2-91cd-3fcb577265b9)


- Sign out and sign in as the dedicated domain admin.

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


- Windows 10 client. Make sure to change network adapter to internal network. Enter ipconfig in command prompt and ensure the DHCP server is working properly. 

- Ping a website. I chose to ping Amazon and Google. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129297&authkey=%21AHsMc1efyIjxyG4&width=1000&height=1000" width="80%" height="80%" />

- Rename Windows client and join domain. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129306&authkey=%21AKLfMgCF5-skV3w&width=1000&height=1000" width="80%" height="80%" />

- Enter proper credentials and windows client should be able to join domain. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129314&authkey=%21AG5SA_kKKZch9VU&width=1000&height=1000" width="80%" height="80%" />

- Confirm that the windows client got its IP address from DHCP server by checking Address Leases on the DHCP Server.   
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129316&authkey=%21AHjM7ccDgAPhPXE&width=1000&height=1000" width="80%" height="80%" />

- Confirm that the windows client joined the domain by checking Computers under Active Directory Users and Computers. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129318&authkey=%21ADQhobhygoIcTeo&width=1000&height=1000" width="80%" height="80%" />

- Login in as another user created earlier. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129322&authkey=%21ALfAmwn0GgiI8DA&width=1000&height=1000" width="80%" height="80%" />
