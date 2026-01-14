# Active-Directory

<h2>Project Overview</h2>
<p>This project documents the end-to-end deployment of a simulated corporate network environment using Oracle VirtualBox. I architected a secure internal network featuring a Windows Server 2019 Domain Controller and a Windows 10 Enterprise Client. The lab focuses on the implementation of core identity management and network infrastructure services, including AD DS, DHCP, DNS, and RAS/NAT, providing a foundation for enterprise-level system administration and security testing.</p> </br>

<h2>Technical Skills Demonstrated</h2>
<p>
<b>Hypervisor Mastery:</b> VirtualBox VM configuration and Multi-NIC networking.

<b>Identity & Access Management (IAM):</b> Active Directory Domain Services (AD DS) forest creation and OU management.

<b>Network Infrastructure:</b> Configuration of DHCP Scopes, DNS resolution, and Routing/Remote Access (RAS) for NAT-based internet gateways.

<b>Automation & Scripting:</b> Utilizing PowerShell to automate the bulk provisioning of 1,000+ user objects.

<b>Security Configuration:</b> Implementing Network Address Translation (NAT) to isolate client workstations from the public internet.

 </p> </br>

<h2>Investigation Walktrough</h2>
<p>
  <h3>Identifying the Attack Source</h3>
  
After downloading oracle vm, click on “new”, we will create the Server 2019 iso first. For this project, 2 NICs will be used. One dedicated to the internet which will run as NAT and the other  will be solely internal network. 

<img src="https://i.imgur.com/JTGCAjO.png" height="80%" width="80%" alt="Investigation Walkthrough"/>

Next, the IP addresses for the internal network interface are set up. In Network Settings, “Change Adapter Options” is selected, and the properties of the available adapters are checked. By default, the IP is assigned automatically and should not start with 10.x.x.x. To assign a custom IP, the adapter is right-clicked, Properties is selected, Internet Protocol Version 4 (IPv4) is double-clicked, “Use the following IP address” is chosen, and the preferred IP configuration is entered.

<img src="https://i.imgur.com/momhf9B.png" height="80%" width="80%" alt="Investigation Walkthrough"/>

Active Directory Domain Services is installed.

<img src="https://i.imgur.com/5NlDUdO.png" height="80%" width="80%" alt="Investigation Walkthrough"/>

 A domain is created via Server Manager

<img src="https://i.imgur.com/TLAfpUn.png" height="80%" width="80%" alt="Investigation Walkthrough"/>

Created a dedicated domain admin account.

<img src="https://i.imgur.com/XqkeAHQ.png" height="80%" width="80%" alt="Investigation Walkthrough"/>

RAS/NAT (Remote Access Service/Network Address Translation) is installed on the domain controller. This allows clients on the private virtual network to access the internet through the domain controller.

<img src="https://i.imgur.com/jT33yoo.png" height="80%" width="80%" alt="Investigation Walkthrough"/>

A DHCP server is configured to automatically assign IP addresses to clients when they connect to the network.

<img src="https://i.imgur.com/q8ISRP6.png" height="80%" width="80%" alt="Investigation Walkthrough"/>

Configure the domain controller to enable internet access for clients on the network.

<img src="https://i.imgur.com/XvCGe4O.png" height="80%" width="80%" alt="Investigation Walkthrough"/>

I create sample users in Active Directory using PowerShell. I open PowerShell ISE as an administrator, enable script execution with Set-ExecutionPolicy Unrestricted, and run a pre-prepared script to automatically create the user accounts.

<img src="https://i.imgur.com/LxCSeTq.png" height="80%" width="80%" alt="Investigation Walkthrough"/>



