# Active-Directory
<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Deploying Active Directory in the Cloud (Azure)</h1>
This is a project that I did outlining the implementation of Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>Deployment and Configuration Steps</h2>

- Set up Resources in Azure.
- Ensure Connectivity between client and Domain Controller.
- Install Active Directory.
- Create an Admin and Normal User Account in Active Directory.
- Add Client-1 to the created Domain
- Set up remote Desktop for non-adminstrative users on Client-1
- Create additional users

<h2>Setting Up Resources in Azure</h2>

![Creating VM for Domain Controller ](https://github.com/user-attachments/assets/ef876fa8-202a-40ea-86f2-d00ae63faf2e)
Created Domain Controller (Windows Server 2022). Took note of virtual network and resource group. This is so I could put the the Client in the same reosurce group and virtual network.

![Making DC-1 private IP static](https://github.com/user-attachments/assets/b1ddd5e2-7b6c-414a-9e61-820ce2883f7f)

Changed Domain Controller's private Ip to static because it will act as a DNS server. This will be make it easire to find for clients. Also security. Network firewalls often have rules based on IP addresses.A static IP for a domain controller allows for more precise and secure firewall configurations.   
 

![Creating Client-1 VM](https://github.com/user-attachments/assets/0f701fa3-903b-4d8a-852e-e143c81ab196)



<p>

![Correct VN for Client-1](https://github.com/user-attachments/assets/6e90f803-968c-4b83-af03-b512681f57e8)


Created the Client VM and used the same Virtual Network and Resource Group used for the Domain Controller.

<h2>Ensuring Connectivity Betwen the client and Domain Controller</h2>

![RDP Client 1 from my computer](https://github.com/user-attachments/assets/2079f459-fbde-4bdd-97eb-88aae5303530)

![Client 1 login that was created](https://github.com/user-attachments/assets/d2da2cf7-95aa-487c-bd09-17246eabc1a2)

![RDP in DC-1](https://github.com/user-attachments/assets/df181e03-3c9c-4851-9d09-b77a3c82b3c7)

![enabling ICMPv4](https://github.com/user-attachments/assets/2d7c67eb-2bfb-4169-856c-d8ce8123c431)


Logged into client 1 with the credentials I created earlier in Azure.
Logged into Domain Controller with the credentials I created earlier in Azure.
I navigated to Windows Defender Firewall in the Domain Controller. Windows Defender -> Advanced Settings -> Inbound rules -> Enable ICMP4




</p>
<p>

</p>
<br />



</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
