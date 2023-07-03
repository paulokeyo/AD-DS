<h1>Active Directory, Domain users and client PC in Domain network </h1>

 ### [Step-by-step tutorial article](https://medium.com/@okeyopaul/step-by-step-creating-of-active-directory-and-adding-users-adf18611f0da)

<h2>Description</h2>
This lab demonstrates creation of users in Active Directory using a powershell script. Clients PC will be addressed in the domain network using DHCP server and routed to the internet using NAT and DNS setup in the Domain controller.
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
1. In VirtualBox Network settings of the VM attach "Adapter 1" to "NAT" and "Adapter 2" to "Internal network"
2. Run the Domain Controller VM and rename the 2 network connections to "Internal network" and "Internet"
3. Configure the Internal network connection
<img src="https://github.com/paulokeyo/AD-DS/blob/main/assets/7.png?raw=true" />

### Install Active Directory and Domain Services in the Domain Controller
<img src="https://github.com/paulokeyo/AD-DS/blob/main/assets/9.png?raw=true"/>
1. In Service manager dashboard, click "Add roles and features" then add "Active Directory Domain Service" role
2. Add a new forest and give the "Root domain name" the name of your choice then deploy

### Setup NAT(Network Address Translation)
1. In Service manager dashboard, click "Add roles and features" then add "Remote Access" role and install
2. Select "Tools" on the Service Manager Dashboard and Click on "Routing and Remote Access"
3. Right click on the "domain name" in "Routing and Remote Access" and select "Configure and Enable Routing and Remote Access"
4. Under "Configuratation" select "NAT" and use the Internet connections we renamed earlier.

<img src="https://github.com/paulokeyo/AD-DS/blob/main/assets/21.png?raw=true"/>  

### Setup DHCP Server
1. In Service manager dashboard, click "Add roles and features" then add "DHCP" role and install
2. Select "Tools" on the Service Manager Dashboard and Click on "DHCP"
3. Under the Domain name, right click on "IPv4" to setup the DHCP
4. Give the scope a name, the range of addresses to be used.
5. In the Router(Default Gateway), Add the ip address we assigned to the Internal network(172.16.0.1) then finish the setup
6. Right click on "Authorize" to start the server
<img src="https://github.com/paulokeyo/AD-DS/blob/main/assets/25.png?raw=true"/>

### Create Domain Users
You can create users manually as shown in [Step-by-step Tutorial](https://medium.com/@okeyopaul/step-by-step-creating-of-active-directory-and-adding-users-adf18611f0da#38cb) or use a script in powershell. 
The script will create a username and default password(Password1)
The username will be made by concatinating the firstname with the lastname e.g username for "Paul Davids" is "pdavids"
1. Download "Create_users.ps1" script and "names.txt" files and save on the domain controller desktop
2. Modify the "names.txt" according to the number of users you need
3. Run the script as administrator in your Domain Controller
<img src="https://github.com/paulokeyo/AD-DS/blob/main/assets/31.jpg?raw=true"/>
Use the credential created to log into the domain using a client VM
   
