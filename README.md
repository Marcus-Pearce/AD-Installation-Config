# configure-ad-
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

- Create a 2 Virtural Machines
- Check Connectivity
- Configure Active Directory
- Provision and De Provision

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


![image](https://github.com/Mrpearce92/configure-ad-/assets/140969692/97ef0020-e0e2-4434-b6d0-f7390c96607b)

</p>
<p>

</p>
<br />
<p>

</p>
<br />

<p>

</p>
<br />
