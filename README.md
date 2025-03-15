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
<br />

<p>
<img src="https://i.imgur.com/LFjPhpU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Click on Next until the page below comes up. We need to add "Active Directory Domain Services" so click on it and "Add features". Click on "Next" until the Install page is reached. Install a=nd close afterwards
</p>

<p>
<img src="https://i.imgur.com/YDaszj6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
Now, we are going to promote DC-1 as an actual domain controller. This means it would be configured to become the domain controller. <br /> 
Go back to the "Service Manager Dashboard" and navigate to a "flag" at the top right corner of the page. Click and follow the prompts
</p>
<br />

<p>
<img src="https://i.imgur.com/Csg1tWF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
