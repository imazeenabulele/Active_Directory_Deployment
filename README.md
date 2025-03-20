# Active_Directory_Deployment

<p align="center">
<img src="https://i.imgur.com/dD3HdHo.jpeg" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Install Active Directory services on DC-1
- Create a Domain Admin user
- Join Client-1 VM to the domain

<h2>Deployment and Configuration Steps</h2>

<p>
To start this off, login to the DC-1 via remote desktop connection (this was shown in the previous section). <br /> 
Once logged in, navigate to the start tab and click on "Server Manager". Once the dialog box opens up, click on "ADD ROLES AND FEATURES" as seen below
</p>

<p>
<img src="https://i.imgur.com/LFjPhpU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Click on Next until the page below comes up. We need to add "Active Directory Domain Services" so click on it and "Add features". Click on "Next" until the Install page is reached. Install and close afterwards
</p>

<p>
<img src="https://i.imgur.com/YDaszj6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br /> 

<p>
Now, we are going to promote DC-1 as an actual domain controller. This means it would be configured to become the domain controller. <br /> 
Go back to the "Service Manager Dashboard" and navigate to a "flag" at the top right corner of the page and click "promote this server as a domain controller" </p>

<p>
<img src="https://i.imgur.com/Csg1tWF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Select "Add a new forest" > use "mydomain.com as Root domain name > input a password and confirm > uncheck "create DNS delegation > click "Next" until the Install page is reached and Install.
Once installation is complete, DC-1 would restart itself and require you to re-login 
</p>

<p>
<img src="https://i.imgur.com/99qYPR8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Now that DC-1 is a domain controller, in order to login to it, we have to specify the context to which we want to log into it as. 
This means every user in the domain that needs to login to DC-1 would need to specify the domain name(context) and the user's name. In this case "mydomain.com" is the domain and "labuser" is the user's name. See image below
</p>

<p>
<img src="https://i.imgur.com/9K5lkVR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br /> 
<br /> 

<p>
Once logged in, navigate to "Start" > "Windows Administrative tools" > "Active Directory Users and Computers"
</p>

<p>
<img src="https://i.imgur.com/YI9yZcl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br /> <br /> 

<p>
We will go on to create an "Organizational Unit (OU) called "_EMPLOYEES".
An Organizational Unit (OU) in Active Directory (AD) is a container used to group users, computers, groups, and other OUs within a domain. It helps administrators organize and manage resources efficiently by applying Group Policies and delegating administrative control<br /><br />
Once in the Active Directory Users and Computers page, right-click on "mydomain.com" > Select "New"  > "Organizational Unit" > type in the name as seen below
</p>

<p>
<img src="https://i.imgur.com/UNTnnO0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br /> <br /> 

<p>
Add another organizational unit called "_ADMINS"
</p>

<p>
<img src="https://i.imgur.com/TwM2hKT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br /> <br /> 

<p>
A new employee will be created named "Jane Doe" and her password login enabled. To create a user, right-click on _ADMINS > "New" > "User"
</p>

<p>
<img src="https://i.imgur.com/vcsXj8T.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br /> <br /> 

<p>
Jane's account is not an admin yet even though we put it in the admin folder. What makes the account an administrator over the domain is actually adding the account to the built-in domain admins security group <br />
To add the account, right click on "Jane Doe" > "Properties" > "Member of" > "Add" > type in domain admins as seen in image below and click "Check Names". Once it finds it, click Apply and Ok. Now the account is an actual DOmain Admin so creating users and performing other tasks can be carried out 
</p>

<p>
<img src="https://i.imgur.com/dbQ1EXC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br /> <br /> 

<p>
Now, we'll log out of labuser account and login as the new domain admin which is Jane doe
</p>

<p>
<img src="https://i.imgur.com/6yy48RJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br /> <br /> 

<p>
Next, we'll log into client-1 as t he original local admin (labuser) and join it to the domain. To do this, get the ipaddress for client-1 and set up a remote desktop connection into client-1 VM <br />
Once login is successful, navigate to the start menu and right click > slect "system" > "rename this PC (advanced) > click "change" > select "Domain" and type "domain.com". Click Ok
</p>

<p>
<img src="https://i.imgur.com/pnQCWV3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br /> <br /> 

<p>
In the previous section, we set client-1's DNS settings to use DC-1's private ip address. By doing this, the domain controller (current DNS server) can be located which is in the "mydomain.com" domain <br /> 
Here we'll use the jane_admin details to login because the accont is a domain admin and has permissions to join the domain. Once this is done, client-1 would retart 
</p>

<p>
<img src="https://i.imgur.com/fVKeWlg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br /> <br /> 

<p>
Log into the domain controller (DC-1) via remote desktop conncection and verify that client-1 shows up in Active Directory Users and Computers (ADUC). Navigate to the ADCU as before, expand mydomain.com drop down > click on "computers" and we can see client-1 present
</p>

<p>
<img src="https://i.imgur.com/p1Qv5jP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br /> <br /> 


