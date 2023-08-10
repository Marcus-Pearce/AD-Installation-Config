# Active Directory Installation Configuration
<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Create 2 Virtural Machines
- Check Connectivity between VM's
- Configure Active Directory
- Provisioning

<h2>Deployment and Configuration Steps</h2>

<p>
Create a Virtual Machine inside of a Resource Group called RG-AD. Select the Windows Server 2022 for this machine naming it DC-1 for Domain Controller.
</p>

![image](https://github.com/Marcus-Pearce/AD-Installation-Config/assets/140969692/05c8b083-c177-4de2-8004-48987f1b66cb)


</p>

<br />

<p>
Create a second virtual machine as the client and name it Client-1. Select Windows 10 for this virtual machine.

![image](https://github.com/Marcus-Pearce/AD-Installation-Config/assets/140969692/436a174f-b9b3-41fb-9852-4d5defc961b1)


</p>
<p>
Change the IP Address of DC-1 to static.

![image](https://github.com/Marcus-Pearce/AD-Installation-Config/assets/140969692/8afb951d-83a1-45f1-991e-77446983ce54)

</p>
<br />

<p>
Go to Remote Desktop and log in to Client-1's Public IP Address using the credentials used when creating the VM.
  
![image](https://github.com/Marcus-Pearce/AD-Installation-Config/assets/140969692/1ee0ae44-d3af-467c-bcb1-2ba2d5a5e9b4)


</p>
<p>
Open the command line.Use command ping -t to ping the Private IP Address of DC-1 perpetually. This is used to check connectivity between DC-1 and Client-1. DC-1 is currently not receiving the ping due to the firewall. Open a new Remote Desktop on your main computer and log in to DC-1 using the Public IP Address. 
  
![image](https://github.com/Marcus-Pearce/AD-Installation-Config/assets/140969692/0c5ad400-6a2d-4a11-b8fa-e4864edf3883)

</p>
<br />
<p>
Go to Windows FireWall Settings Advanced on DC-1 and then Inbound Rules. Sort by protocol and find ICMPv4 and enable it. Switch back to CLient-1 and watch the ping succeed. Hit Control+C on the Command Line to stop the ping,

![image](https://github.com/Marcus-Pearce/AD-Installation-Config/assets/140969692/a5f55615-f8e4-402e-9788-84dcedb8446b)

</p>
<br />

<p>
In DC-1 go to the Server Manager and click Add roles and features. Continue steps and make sure to select Active Directory Domain Servies box.

![image](https://github.com/Marcus-Pearce/AD-Installation-Config/assets/140969692/384e7296-2141-488d-ab68-ca3c909b072d)

</p>
<br />

<p>
Promote the server to a domain controller by going to the caution notification at the top right .
  
![image](https://github.com/Marcus-Pearce/AD-Installation-Config/assets/140969692/419629bd-ae98-42d4-84e6-8bd58c194a8f)

</p>
<br />

Create a new forest named mydomain.com

![image](https://github.com/Marcus-Pearce/AD-Installation-Config/assets/140969692/791da845-c786-4271-ac20-9144b257797a)

<p>

The VM will close due to restart needed after Active Directory is installed. Log back into DC-1 with mydomain.com/labuser.

![image](https://github.com/Marcus-Pearce/AD-Installation-Config/assets/140969692/a68788fc-be76-4588-8e60-56883d97c654)

</p>
<br />
Go to Active Directory Users and Computers on the Tools drop down.
![image](https://github.com/Marcus-Pearce/AD-Installation-Config/assets/140969692/80820c53-999d-4439-bb05-491319d7afab)

<p>
Create a new Organizational Unit named _EMPLOYEES and one named _ADMINS.
  
![image](https://github.com/Marcus-Pearce/AD-Installation-Config/assets/140969692/a8525e70-a694-4389-9ab4-6500d00f8051)

</p>
<br />

<p>
Create a new users named Jane and John Doe. Add Jane to the Domain Admins security group.
 
![image](https://github.com/Marcus-Pearce/AD-Installation-Config/assets/140969692/99a377e8-b453-4b86-a908-b60de25c0efb)

</p>
<br />

<p>
Log out of the Virtual Machine and log back into using Remote Desktop using jane_admin this time.

![image](https://github.com/Marcus-Pearce/AD-Installation-Config/assets/140969692/ca33d9a7-9c5d-481c-af8e-042b566595fc)

</p>
<br />

Set Client-1's DNS settings to DC-1's Private IP Address.

<p>
In CLient-1 right click the start menu and go to System settings. CLick on Rename PC (Advanced) and change the domain name to mydomain.com. Use mydomain.com\jane_admin and hit Ok. It will shut down your VM for a restart.
  
![image](https://github.com/Marcus-Pearce/AD-Installation-Config/assets/140969692/33c39294-4aa8-4aee-b8d8-1c8a98559c3e)

</p>
<br />

<p>

On DC-1 you can see Client-1 show up under the Computers container. Create a Organizational Unit called _CLIENTS and put Client-1 in it.

![image](https://github.com/Marcus-Pearce/AD-Installation-Config/assets/140969692/c4331c09-8112-46cc-a39b-1bbd93ba5342)

</p>
<br />

<p>
Log back into CLient-1 and go to System Settings and go to Remote Desktop and add Domain Names so that non-administrative users can remotely log on.

![image](https://github.com/Marcus-Pearce/AD-Installation-Config/assets/140969692/4cc2ffbe-7a6f-44c2-94ff-460585335118)

</p>

