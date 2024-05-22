<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Active Directory Network File Sharing and Permissions</h1>
This tutorial briefly details how to assign specific file permissions to network folders.<br />



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
<img src="https://github.com/chrisrraP/Network-File-Sharing-and-Permissions/blob/main/Sharing%20Permissions.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


</p>
<p>
Create a group resource and virtual machines within Microsoft Azure. Reference https://github.com/chrisrraP/configure-ad to learn how to create virtual machines. Log into server (DC-1) and create 3 folders titled after their permission settings (read-access, write-access, and no access). Create a fourth folder called "accountants".
<br />

<p>
<img src="https://github.com/chrisrraP/Network-File-Sharing-and-Permissions/blob/main/DC-1%20Firewall%20Setup.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://github.com/chrisrraP/Network-File-Sharing-and-Permissions/blob/main/DC-1%20Add%20OU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://github.com/chrisrraP/Network-File-Sharing-and-Permissions/blob/main/Admin%20User.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
Log into the domain server and enable ICMPv4 TCP Protocols on Windows Firewall. Once connectivity is established between both machines, Install Active Directory and add a domain. The machine restarts by default and log back in with the new domain created and the pre-existing username. Create three Organizational Units (OU). Name them "Admins", "Employees" "Security_Group". Right-click into each of these folders an add a couple users. Give the user in the Admins folder administrator properties by adding them to the "Domain Admins" group.
</p>
<br />

<p>
<img src="https://github.com/chrisrraP/Network-File-Sharing-and-Permissions/blob/main/User%20Added%20to%20NSG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://github.com/chrisrraP/Network-File-Sharing-and-Permissions/blob/main/Accounting%20Permissions.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Add a user you've created without administrator properties as a member of the "Accounting" group. Log into client and open file manager. Type "\\dc-1" into the search bar. Confirm the properties are correct by attempting to open and write in the folders. You should be able to open every folder except for the one titled "no access". Experiment further by adding more users with different permissions and see which folders they are able to access.
</p>
<br />
