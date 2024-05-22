<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Active Directory Network File Sharing and Permissions</h1>
This tutorial briefly details how to assign specific file permissions to network folders.
<p>
File Shares is the ability to share files or directories over a network, allowing multiple users or groups to access them with varying degrees of abilities (read-only, read & write, no access).
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


<h2>Deployment and Configuration Steps</h2>

<p>
<img src=".png" height="80%" width="80%">
</p>
<p>
For this exercise we will continue to use the Domain Controller (DC-1) and VM (Client-1) we created in the Active Directory Repository (https://github.com/jordanconnelly/configure-ad).
<p>
First log in to DC-1 using the domain admin account (mydomain.com\jordan_admin). Open File Explorer and navigate to the (C:) drive. 
<br />
