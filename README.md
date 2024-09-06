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
- Set up remote Desktop for non-administrative users on Client-1
- Create additional users

<h2>Setting Up Resources in Azure</h2>

![Creating VM for Domain Controller ](https://github.com/user-attachments/assets/ef876fa8-202a-40ea-86f2-d00ae63faf2e)
- Created Domain Controller (Windows Server 2022). Took note of virtual network and resource group. This is so I could put the the Client in the same resource group and virtual network.

![Making DC-1 private IP static](https://github.com/user-attachments/assets/b1ddd5e2-7b6c-414a-9e61-820ce2883f7f)

- Changed Domain Controller's private Ip to static because it will act as a DNS server. This will be make it easier to find for clients. Also security. Network firewalls often have rules based on IP addresses.A static IP for a domain controller allows for more precise and secure firewall configurations.   
 

![Creating Client-1 VM](https://github.com/user-attachments/assets/0f701fa3-903b-4d8a-852e-e143c81ab196)



<p>

![Correct VN for Client-1](https://github.com/user-attachments/assets/6e90f803-968c-4b83-af03-b512681f57e8)


- Created the Client VM and used the same Virtual Network and Resource Group used for the Domain Controller.

<h2>Ensuring Connectivity Between the client and Domain Controller</h2>

![RDP Client 1 from my computer](https://github.com/user-attachments/assets/2079f459-fbde-4bdd-97eb-88aae5303530)

![Client 1 login that was created](https://github.com/user-attachments/assets/d2da2cf7-95aa-487c-bd09-17246eabc1a2)

![RDP in DC-1](https://github.com/user-attachments/assets/df181e03-3c9c-4851-9d09-b77a3c82b3c7)

![enabling ICMPv4](https://github.com/user-attachments/assets/2d7c67eb-2bfb-4169-856c-d8ce8123c431)


![pinging DC-1 to check for connectivity](https://github.com/user-attachments/assets/f5ee1a96-6734-4182-b09f-5082eb59bb8d)


![After Enabling ICMPv4 Traffic replies](https://github.com/user-attachments/assets/1c33c7ed-03de-4b1e-b227-c60e02b0ca24)




- Logged into client 1 with the credentials I created earlier in Azure.

- Logged into Domain Controller with the credentials I created earlier in Azure.

- I navigated to Windows Defender Firewall in the Domain Controller. Windows Defender -> Advanced Settings -> Inbound rules -> Enable ICMP4

- Used ping command to check for connectivity in Domain Controller 1.

- Connectivity Confirmed.


<h2>Installation of Active Directory Steps</h2>

![Installing AD](https://github.com/user-attachments/assets/007b2a18-3e5a-48c6-b18a-54bd8c97529d)

![AD Domain Services](https://github.com/user-attachments/assets/4f891db4-e91a-475d-b264-c68ce883e4fc)

![add new forest](https://github.com/user-attachments/assets/ca2ecabf-b96a-4a38-a4d2-d770b0e8877d)


![promote DC-1 to domAin controller](https://github.com/user-attachments/assets/da56f563-0b8d-49f1-94e7-3248fb5fe738)

- Installed Active Directory on Windows server.  Add Roles and Features -> Select Active Directory Domain Services.

- Select Server Roles -> Check Active Directory Domain Services.

- Added new forest (domain) jonathanwcislo.com

- Clicked little yellow triangle to promote server to Domain Controller.


<h2>Creating Admin and Normal User</h2>

![Created ADMINS adn EMPLOYEE OU's](https://github.com/user-attachments/assets/9318220c-5e2b-4d0a-b52f-2c1b80526375)


![Created Jonny login](https://github.com/user-attachments/assets/3779cde0-aeb2-4320-b762-695bc69955bc)


![Logging in with Jonny admin](https://github.com/user-attachments/assets/49e12d15-80b1-424b-9b60-20ab55052596)


![Jane Doe Created](https://github.com/user-attachments/assets/2b725ac0-ad7f-4a24-b75f-5089780422c0)

![Password for Jane Doe](https://github.com/user-attachments/assets/5de5ff34-14db-4d25-8bad-d00dcb26f018)

![Logging in with Jonny admin](https://github.com/user-attachments/assets/46cca603-5f1a-43ef-8e42-264dde9380e7)




- Created Admins and Employee Organizational Units.
- Created Jonny_admin account.
- Create Jane Doe user account.
- Logging back in after making server a Domain Controller.



  <h2>Joining Client 1 to domain</h2>

![DNS server Client 1](https://github.com/user-attachments/assets/a4b64f1b-a370-4b56-af88-3d3597afa93b)

![Setting Client 1 DNS settings](https://github.com/user-attachments/assets/a2fc735d-b6e9-497c-a63e-93ae379b5a2f)

![using ipconfig  to see if DNS server has changed](https://github.com/user-attachments/assets/90cd278d-d4ed-48c9-a542-572e84831a1d)

![adding client 1 to domain](https://github.com/user-attachments/assets/0f4e3bf3-e9eb-4b53-b702-5a59c0778b28)

![Adding Cl1 domain 2](https://github.com/user-attachments/assets/e5f36d25-68e0-448c-a961-9dcd725f9aa7)

![Successfully joined client 1 to domain](https://github.com/user-attachments/assets/9a609d1f-f0e1-44eb-9053-ec7ebd25d481)



-From the Azure Portal I set Client 1's DNS settings to the Domain Controller's Private IP and restarted the Client 1 form Azure.

-Logged into Client 1 to check if DNS server had changed to Domain Controller IP using Ipconfig.

- Added Client 1 to Domain jonathanwcislo.com  Start -> System -> Rename this PC

- Successfully added Client-1 to the Domain.


  


<h2>Setup Remote Desktop for non-administrative users on Client 1</h2>

- Logged into Client 1 as jonathnwcislo.com\jonny_admin
- Clicked on Remote Desktop System Properties -> Allow Domain Users access to remote desktop.
- This would normally been done with Group Policy to configure many machines





</p>
<p>

</p>
<br />



</p>
<p>

</p>
<br />

<p>

</p>
<p>

<br />
