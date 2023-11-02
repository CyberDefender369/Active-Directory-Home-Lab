<h1>Active Directory Home Lab</h1>

<h2>Description</h2>
This project focuses on basic Active Directory (AD) configurations. In this home lab I configured Organizational Unit (OU), Domain Controller (DC), and Dynamic Host Configuration Protocol (DHCP). Simple networking configurations were implemented as well. Additionally, a RHEL client was added to the AD domain. 

<h2>Languages and Utilities Used</h2>

- PowerShell
- VirtualBox

<h2>Environments Used </h2>

- Windows 10 (21H2)
- Windows Server 2019
- RHEL 9.2

<h2>Note</h2>
For redundancy reasons there are 45 screenshots in the project walk-through. Hopefully, the redundancy leaves minimal confusion for students/beginners wanting to replicate this lab. 

<h2>Project Walk-Through:</h2>

<p align="left">
Configure IP addresses on the the second internal NIC (Ethernet 2) of the Windows machine that will act as the Domain Controller, DNS Server, and Default Gateway. Used the static IP address of 172.16.0.1/24 for the internal NIC and loopback address for the DNS. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129157&authkey=%21AKzDkgA2AGd9SSY&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Install Active Directory Domain Services. 
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
Add a new forest and name the domain.
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
Create dedicated domain administrative account by navigating to AD users and computers, and create a OU first and name it ADMINS. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129197&authkey=%21ANc-lEHCI1UQYUI&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Add a new user, which will be the dedicated admin account. Naming convention will depend on the organization.  
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129203&authkey=%21AG5axzeAqAEE_cI&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Make the account a domain admin by heading over to properties -> member of -> domain admins -> OK -> apply. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129211&authkey=%21ANPjzHPqE5OczAI&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Logout of the domain conroller -> Ctrl+Alt+Delete -> sign in as domain admin. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129214&authkey=%21AINzjE54vsOsq8Q&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Time to install Network Address Translation for internal workstation clients. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129217&authkey=%21AI2qbnsmprdECWM&width=1000height=1000" width="80%" height="80%" />
<br />
<br />
Add roles and feautures -> select correct server -> Remote Access -> Routing -> keep defaults -> install.  
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129223&authkey=%21AGZ2cqSVcg8GlvA&width=1000height=1000" width="80%" height="80%" />
<br />
<br />
Tools -> Routing and Remote Access -> Configure an Enable Routing and Remote Access-> select NAT -> select outward facing NIC -> finish.
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129232&authkey=%21ACgn2tjlAs1jZVE&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Green arrow next to DC (local) signifies that NAT is now operational. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129236&authkey=%21ADA2t-wfryVo9VU&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Add roles and feautures -> select correct server -> select DHCP server -> leave everything else default -> install. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129238&authkey=%21AK0iQ1-sHxkGK8U&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Tools -> DHCP -> right click IPv4 -> New Scope... -> name scope -> add description. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129243&authkey=%21AOgZqGuYDSzWfrY&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Enter IP range and subnet mask. 
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129245&authkey=%21AGfvbzeHjNWsULw&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Step 22: <br/>
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129253&authkey=%21ANEagreAZZEovAs&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Step 23: <br/>
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129255&authkey=%21AKCAkKTL1RJtnpE&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Step 24: <br/>
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129293&authkey=%21AMpI3Sso61VfA30&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Step 25: <br/>
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129263&authkey=%21AJ5z-aPA19g3tG0&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Step 26: <br/>
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129265&authkey=%21AAsAmvFjGuAaLP4&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Step 27: <br/>
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129281&authkey=%21ABsmvLlzbaZTc44&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Step 28: <br/>
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129295&authkey=%21AAgxCoAn5sP9LaI&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Step 29: <br/>
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129297&authkey=%21AHsMc1efyIjxyG4&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Step 30: <br/>
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129306&authkey=%21AKLfMgCF5-skV3w&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Step 31: <br/>
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129314&authkey=%21AG5SA_kKKZch9VU&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Step 32: <br/>
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129316&authkey=%21AHjM7ccDgAPhPXE&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Step 33: <br/>
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129318&authkey=%21ADQhobhygoIcTeo&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Step 34: <br/>
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129322&authkey=%21ALfAmwn0GgiI8DA&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Step 35: <br/>
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129322&authkey=%21ALfAmwn0GgiI8DA&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Step 36: <br/>
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129336&authkey=%21AISRd75uk7SwRtU&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Step 37: <br/>
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129347&authkey=%21ADSYllnoHwQIv0s&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Step 38: <br/>
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129349&authkey=%21APXaO_wbZhTE1Ws&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Step 39: <br/>
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129355&authkey=%21AO6nG1cJ3PHXLIE&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Step 40: <br/>
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129357&authkey=%21AOuAc-xBPwgO7DU&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Step 41: <br/>
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129361&authkey=%21ACUkUdf7RS4LBdY&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Step 42: <br/>
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129359&authkey=%21AE1WF_8UtbHtx7k&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Step 43: <br/>
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129365&authkey=%21AJ5yvkcVl-Bajz4&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Step 44: <br/>
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129367&authkey=%21APidCJoy2TxQxnM&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
Step 45: <br/>
<img src="https://onedrive.live.com/embed?resid=C275DA66CF018782%2129369&authkey=%21AOlH2ItHNmG_O_0&width=1000&height=1000" width="80%" height="80%" />
<br />
<br />
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
