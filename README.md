<h1>Active Directory Home Lab</h1>

<h2>Description</h2>
This project focuses on basic Active Directory (AD) configurations. I setup an Organizational Unit (OU), a Domain Controller (DC), and a Dynamic Host Configuration Protocol (DHCP) server to name a few. Simple networking configurations were implemented as well. Additionally, a RHEL client was added to the AD domain. 

<h2>Languages and Utilities Used</h2>

- PowerShell
- VirtualBox

<h2>Environments Used </h2>

- Windows 10 (21H2)
- Windows Server 2019
- RHEL 9.2

<h2>Notes</h2>
This simple lab was designed to demonstrate basic AD configurations and does not go over everything AD has to offer. 
<h2>Project Walk-Through:</h2>

<p align="left">
Configure IP address on the the second internal NIC (Ethernet 2) of the Windows machine that will act as the Domain Controller, DNS Server, and Default Gateway. Used the static IP address of 172.16.0.1/24 for the internal NIC and loopback address for the DNS. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129157&authkey=%21AKzDkgA2AGd9SSY&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Install Active Directory Domain Services. Add roles and features -> Role-based or feature-based installation -> select correct server -> Active Directory Domain Services -> next.          
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129165&authkey=%21AKHqQ914Ve_YRVw&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Confirm all services are correct and install.
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129169&authkey=%21AO__hkW4A_44CeY&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Promote this server to a domain controller. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129178&authkey=%21AJtX4P4j5S_1Z-E&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Add a new forest and name the domain. Domain name conventions should be determined by organization. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129183&authkey=%21ADirqcSlaoKpv-8&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Keep all default configurations and install. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129188&authkey=%21AJBnqHKiY9vS2k0&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Computer will restart and domain has been created. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129193&authkey=%21AMm09ogxJI7iugA&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Create dedicated domain administrative account. Active Directory Users and Computers -> right click domain -> new -> Organizational Unit -> name the OU -> I named the OU ADMINS. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129197&authkey=%21ANc-lEHCI1UQYUI&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Add a new user, which will be the dedicated admin account. Naming convention will depend on the organization.  
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129203&authkey=%21AG5axzeAqAEE_cI&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Make the account a domain admin. Right click ADMINS -> properties -> member of -> domain admins -> OK -> apply. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129211&authkey=%21ANPjzHPqE5OczAI&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Logout of the domain conroller -> Ctrl+Alt+Delete -> sign in as domain admin. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129214&authkey=%21AINzjE54vsOsq8Q&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Time to install Network Address Translation for the internal Windows client. Add roles and features -> Role-based or feature-based installation -> select correct server -> Remote Access -> next. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129217&authkey=%21AI2qbnsmprdECWM&width=1000height=1000" width="80%" height="80%" />
<br />
<br />
Routing -> leave everything else default -> install.  
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129223&authkey=%21AGZ2cqSVcg8GlvA&width=1000height=1000" width="80%" height="80%" />
<br />
<br />
Configure Routing and Remote Access Server. Tools -> Routing and Remote Access -> Configure an Enable Routing and Remote Access-> select NAT -> select outward facing NIC -> finish.
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129232&authkey=%21ACgn2tjlAs1jZVE&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Green arrow next to DC (local) signifies that NAT is now operational. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129236&authkey=%21ADA2t-wfryVo9VU&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Install DHCP Server. Add roles and feautures -> select correct server -> select DHCP Server -> leave everything else default -> install. 
  
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129238&authkey=%21AK0iQ1-sHxkGK8U&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Configure scope. Tools -> DHCP -> right click IPv4 -> New Scope... -> name scope -> add description. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129243&authkey=%21AOgZqGuYDSzWfrY&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Enter IP range and subnet mask. Next page will ask about lease duration which I left as default but will depend on the policies of each organization. Next, it will ask you if you want to configure DHCP options. Select yes and click next. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129245&authkey=%21AGfvbzeHjNWsULw&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Add the IP address of the internal facing NIC, which will serve as the default gateway for the internal network. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129253&authkey=%21ANEagreAZZEovAs&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
DC will act as DNS server. Enter domain that was previously created. Skip WINS Server. Active scope and finish. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129255&authkey=%21AKCAkKTL1RJtnpE&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
May have to right click DHCP server and then refresh to ensure the server is up and running. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129263&authkey=%21AJ5z-aPA19g3tG0&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
This PowerShell script creates an OU named _USERS and a 1,000 new users. Credit goes to Josh Madakor for the script.
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129281&authkey=%21ABsmvLlzbaZTc44&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Get a free Windows 10 ISO from Microsoft and create virtual client. Make sure to change network adapter to internal network. Enter ipconfig in command prompt and ensure the DHCP server is working properly. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129295&authkey=%21AAgxCoAn5sP9LaI&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Ping a website. I chose to ping Amazon and Google. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129297&authkey=%21AHsMc1efyIjxyG4&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Rename Windows client and join domain. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129306&authkey=%21AKLfMgCF5-skV3w&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Enter proper credentials and windows client should be able to join domain. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129314&authkey=%21AG5SA_kKKZch9VU&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Confirm that the windows client got its IP address from DHCP server by checking Address Leases on the DHCP Server.   
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129316&authkey=%21AHjM7ccDgAPhPXE&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Confirm that the windows client joined the domain by checking Computers under Active Directory Users and Computers. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129318&authkey=%21ADQhobhygoIcTeo&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Login in as another user created earlier. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129322&authkey=%21ALfAmwn0GgiI8DA&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Get a free RHEL ISO from Red Hat and create virtual client. Make sure to change network adapter to internal network. Enter ip a at the terminal and ensure the DHCP server is working properly. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129336&authkey=%21AISRd75uk7SwRtU&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Enabling RC4 support by entering update-crypto-policies --set DEFAULT:AD-SUPPORT. AD supports RC4 encryption for authentication and may not support AES encryption types. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129347&authkey=%21ADSYllnoHwQIv0s&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Installing packages that allows the RHEL client to discover and join AD domain by running the following command: yum install samba-common-tools realmd oddjob oddjob-mkhomedir sssd adcli krb5-workstation. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129349&authkey=%21APXaO_wbZhTE1Ws&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Run the realm discover command to discover AD domain. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129355&authkey=%21AO6nG1cJ3PHXLIE&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Run the realm join command to join AD domain. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129357&authkey=%21AOuAc-xBPwgO7DU&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Run the realm list command to list all configured AD domains.  
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129361&authkey=%21ACUkUdf7RS4LBdY&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Confirm that the RHEL client joined the domain by checking Computers under Active Directory Users and Computers. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129359&authkey=%21AE1WF_8UtbHtx7k&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Select a random user from the _USERS OU. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129365&authkey=%21AJ5yvkcVl-Bajz4&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Run the realm permit command to enable specific access for the previously selected user. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129367&authkey=%21APidCJoy2TxQxnM&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Run the id command to view GID and UID
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129369&authkey=%21AOlH2ItHNmG_O_0&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
