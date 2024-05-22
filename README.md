<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Active Directory Network File Sharing and Permissions</h1>
This tutorial briefly details how to assign specific file permissions to network folders.
<p>
File Shares refers to the ability to share files or directories over a network, allowing multiple users or groups to access them with varying degrees of abilities (read-only, read & write, no access).
<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- Windows Defense Firewall

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Creating Network Folders and Setting Permissions
- Adding Groups within organizational units
- Confirming group permissions


<h2>Creating Sample File Shares with Various Permissions</h2>
</p>
<p>
For this exercise, we will continue to use the Domain Controller (DC-1) and Domain Users (Client-1) VM's we created in the Active Directory Repository (https://github.com/jordanconnelly/configure-ad).
<p>
First log in to DC-1 using the domain admin account (mydomain.com\jordan_admin). Open File Explorer and navigate to the (C:) drive. We will create four new folders: “Read-Access”, “Write-Access”, “No-Access”, and “Accounting”.
<p>
<img src="https://imgur.com/HlxpLKw.png">
<p></p>
We can now set Permissions on these folders for the Domain Users. Right-click on the folder and choose Properties>Sharing tab>Share...>type in Domain Users>Add>Select Permission Level>Share
<p>
For the Read-Access folder we will set the Permission Level to "Read"
<p>
<img src="https://imgur.com/oQURdoq.png">
