<h1>Active Directory, Domain users and client PC in Domain network </h1>

 ### [Step-by-step tutorial](https://medium.com/@okeyopaul/step-by-step-creating-of-active-directory-and-adding-users-adf18611f0da)

<h2>Description</h2>
This lab demonstrates creation of users in Active Directory using a powershell script. Clients PC will be addressed in the domain network using DHCP server and routed to the internet using NAT setup in the Domain controller.
<br />


<h2>Lab setup</h2>
<p align="center">
Launch the utility: <br/>
<img src="https://github.com/paulokeyo/AD-DS/blob/main/assets/Lab%20Topology.png?raw=true" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<h2>Prerequisites </h2>
A Computer running two VMs, Windows server 2019(Domain controller) and Windows 10(Client) 
 
- [Windows 10](https://www.microsoft.com/en-us/software-download/windows10ISO)
- [Windows server 2019](https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019)
- [VirtualBox](https://www.virtualbox.org/wiki/Downloads)

### Configure the Network adapters of the Domain Controller
1. In VirtualBox Network settings of the VM attach Adapter 1 to NAT and Adapter 2 to Internal network
2. Run the Domain Controller VM and rename the 2 network connections to Internal network and Internet
3. Configure the Internal network connection
<img src="https://github.com/paulokeyo/AD-DS/blob/main/assets/7.png?raw=true" />

### Install Active Directory and Domain Services in the Domain Controller
<img src="https://github.com/paulokeyo/AD-DS/blob/main/assets/9.png?raw=true"/>
1. In Service manager dashboard, click Add roles and features then add the AD DM feature
2. Add a new forest and give the Root domain name the name of your choice then deploy

### Set up NAT(Network Address Translation)
1. In Service manager dashboard, click Add roles and features then add Remote Access
   
