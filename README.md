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
<p></p>
For the Write-Access folder we will set the Permission Level to "Read/Write"
<p>
<img src="https://imgur.com/4s0jQVq.png">
<p></p>
Finally, for the No-Access folder we will set the Permission Level to "Read/Write" for the Domain Admins group. This will allow the Admins to access this folder while keeping the Domain Users out of it.
<p>
<img src="https://imgur.com/Cm6sSXs.png">
<p>
We will come back to the Accounting folder later on.

<p></p>
<h2>Accessing Files as a Normal User</h2>
<p></p>
Log in to Client-1 as one of the Domain Users created in the Active Directory from before, I chose the user (mat.don).
<p>
Once logged into Client-1 (mat.don) we will navigate to the root of DC-1 where the Shared Files are located (Right-click Start>Run>\\DC-1)
<p>
<img src="https://imgur.com/laIe17a.png">
<p></p>
Open the "Read-Access" folder and attempt to create a new file (Right-click in folder>New>Folder). We will receive an error message because while we do have permission to open the "Read-Access" folder, we do not have permission to edit it.
<p>
<img src="https://imgur.com/PCWIg4S.png">
<p></p>
Next, open the "Write-Access" folder and attempt to create a new file. We see that because the Domain Users permissions include both Read/Write for this folder, we can add a new folder to it.
<p>
<img src="https://imgur.com/iB0XjAq.png">
<p></p>
Finally we will open the "No-Access" folder and attempt to create a new file. We will not be able to even open this folder because the Permissions only allow Domain Admins access to it.
<p>
<img src="https://imgur.com/KW05Txv.png">
  
<p></p>
<h2>Creating a Security Group, Assigning Permissions, and Testing Access</h2>
<p>
In this section, we will create a Security Group and give that group Read/Write permissions to the "Accounting" folder created earlier. Go back to DC-1 and open Active Directory Users and Computers. Right-click on "mydomain.com" and select New>Organizational Unit, name this Security_Groups. Right-click on "Security_Groups" and select New>Group. In the pop-up window name the group "Accountants". 
<p>
<img src="https://imgur.com/djj4YSq.png">
<p></p>
Next, we will open File Explorer to the (C:) drive, right-click on "Accounting" and select Properties>Sharing tab>"Share...". Type in "Accountants" and set the Permission Level to "Read/Write"
<p>
<img src="https://imgur.com/91wz77l.png">
<p></p>
Minimize DC-1 and open Client-1 again. Attempt to open the "Accounting" folder. Since the normal Domain User (mat.don) is not currently part of the "Accountants" Security Group created in Active Directory, access to this folder is denied.
<p>
<img src="https://imgur.com/fdOg3co.png">
<p></p>
Sign out of Client-1 and reopen DC-1. In Active Directory, open the "Accountants" group. In the pop-up window select the "Members" tab and click "Add...". Type in a Domain User (mat.don) and select OK>Apply>OK to save these changes. Now Domain User (mat.don) is in the Accountants Security Group.
<p>
<img src="https://imgur.com/vqnCfvm.png">
<img src="https://imgur.com/BTxhhLa.png">
