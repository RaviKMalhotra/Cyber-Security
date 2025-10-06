3
Gaia Administration & Routing
This Chapter discusses the Checkpoint owned & patented Operating System known as Gaia. Gaia Operating System is a successor to previously known Operating System SPLAT, & SPLAT Pro. Gaia is a robust and light weight operating system.
Pre-requisites 
Readers must read previous chapter, ‘Chapter 2 - Installation’, and complete all the labs demonstrated. Complete Topology, Network and VLAN details are also explained in the previous chapter.
Readers must review and understand the network topology explained. Please refer to the Topology Understanding, and the VMware Readiness sections again.
In the last chapter, we have successfully created 2 virtual machines as per following details:
Table: IP addressing details for Quantum Security Management Server.
Site A
Server Role	Hostname	Interface	VMnet	IP Address	Subnet Mask
Quantum Security Management	SMS1	etho	VMnet0	192.168.200.10	255.255.255.0
Quantum Security Management	SMS1	eth1	VMnet2	192.168.70.10	255.255.2550
Default Gateway in Quantum Security Management	192.168.70.11

Table: IP addressing details for Quantum Security Gateway.
Site A
Server Role	Hostname	Interface	VMnet	IP Address	Subnet Mask
Quantum Security Gateway	GW1	etho	VMnet0	192.168.200.11	255.255.255.0
Quantum Security Gateway	GW1	eth1	VMnet1	192.168.137.11	255.255.255.0
Quantum Security Gateway	GW1	eth2	VMnet2	192.168.70.11	255.255.255.0
Quantum Security Gateway	GW1	eth3	VMnet3	192.168.80.11	255.255.255.0
Default Gateway in Quantum Security Gateway 1	192.168.137.1



2.5 Hours with Gaia
Gaia Basic Understanding
Let’s start understanding Gaia. Gaia is a Unified Operating System, owned by Check Point Software Technologies. An Operating System ‘Gaia’ is used to represent a Next Generation Operating System used by Check Point Software Technologies. 
Gaia Operating System is a successor to Check Point SPLAT and SPLAT Pro OS. Gaia combines all the features supported by Check Point original OS known as SPLAT and IPSO, which was an OS used by Nokia security appliances. 
Gaia, now being a unified OS is now available for all Check Point Security Appliances and Open Servers. All software blades offered by Check Point Software such as Security Management & Security Gateways can be installed on top of Gaia OS. 
Gaia OS supports all the following features as provided by any other standard and proprietary Operating System:
 	Full support for both IPv4 and IPv6.
 	Packet routing and forwarding capabilities
 	Web User interface
 	Command Line interface
 	Simple user and role management
 	High Availability and Load Sharing.
 	Support for all management protocols such as DNS, DHCP, NTP, Syslog, SNMP, SMTP….
Gaia CPUSE	
CPUSE stands for ‘Check Point Update Service Engine’, also known as Deployment Agent (DA). CPUSE functionality is used for Software deployment on Gaia platform such as single HotFixes (HF), HotFix Accumulators (Jumbo). CPUSE is used to get updates for all Check Point products.
CPUSE can also be used for deployment of Major versions during upgrade operations. 
With CPUSE you can download and install these updates more quickly and error-free. CPUSE allow you to download and install these updates either instantly, manually or periodically. And, it also supports rollback capabilities also.
Download and Installation of Gaia
As we have just learnt above that Gaia OS can be installed on top of Check Point Security appliances and Open Servers. Check Point Security Appliances comes with pre-loaded Gaia OS with most current and   N-1 major version, and the current version is installed on the security appliance as well. 
In a situation if you do not require the current and N-1 version due to any reason, then you can also download and install any other major or minor version of Gaia. But, in case of Open servers, you don’t have any version of Gaia OS preloaded. you need to download and install the specific Gaia OS version manually. 
Any version of Gaia OS can be downloaded in .ISO format from http://www.checkpoint.com.  Once it is downloaded, then installation is pretty quick and easy. 
Though we have already done the download and installation of Gaia OS, let’s do the same exercise again.
Use Case # 1– Perform the following activities in this download & installation use case
 	Download Gaia .ISO image of version R81.10 
 	Create a new Virtual Machine with RHEL Linux 2.6.x as a base Operating System using VMware editor hypervisor software with 4 Network Adapters.
 	Install the Gaia version R81.10 on this virtual machine.
 	Configure the management interface eth0 
Solution -- Please perform these steps to download the .ISO image for version R81.10 and create a new virtual machine using VMware Workstation:
 	Download the .ISO image for Version R81.10 from https://www.CheckPoint.com 
 	Download and Installing VMware Workstation pro hypervisor software from https://vmware.com in case if you yet have not downloaded & installed. 
 	Set up VMware virtual networks as per topology defined in the previous chapter. Create different VMnet in the Virtual Network Editor of VMware Workstation. Here is a quick snippet of same:
 

 	Launch VMware Workstation Pro
 
 	Make, sure that you have downloaded the Check Point R81.10 .ISO version image from https://www.CheckPoint.com, Also make sure that you have created appropriated folders in your system drive to store virtual machines data files. 
 	Click on File menu New Virtual Machines… New Virtual Machine wizard will start. Select the “Typical(recommended) option, and click on next button.
 
 	Select the option “Installer disk Image file (iso)”, click on “Browse” button and point to the .iso image for version R81.10. Click on next button.
 
 	Select “Linux” as a Guest Operating System. And select “Other Linux 2.6.x kernel” as a version, and click on next button.
 
 	Give appropriate name to the virtual machine, and select the location to store all the files related to this virtual machine, and click on next button.
 
 	Enter 100.0 as a size in the “Maximum disk size (GB):” box. And select the option “Store virtual disk as a single file”, and click on next button.
 
 	Click on Finish button
 	Right click on the GW1 virtual machine, and click on Settings button
 
 	Click on “Add” button at bottom  Select Network Adapter option  and click on Finish button.
 	Repeat same steps to add 2 more NIC Cards, you should now see 4 NIC Cards. Now, you need to assign specific VMnet to each interface. See 2 screenshots below:

 

Site A
Server Role	Hostname	Interface	VMnet	IP Address	Subnet Mask
Quantum Security Gateway	GW1	etho	VMnet0	192.168.200.11	255.255.255.0
Quantum Security Gateway	GW1	eth1	VMnet1	192.168.137.11	255.255.255.0
Quantum Security Gateway	GW1	eth2	VMnet2	192.168.70.11	255.255.255.0
Quantum Security Gateway	GW1	eth3	VMnet3	192.168.80.11	255.255.255.0
Default Gateway in Quantum Security Gateway 1	192.168.137.1
Now, Base Virtual Machine is created with 4 NIC Cards. Please perform these steps listed below to install Check Point Gaia OS version R81.10 on the virtual machine:
 	Right click the virtual machine, click on Power, and then click on “Restart Guest”
 
 	In the next windows, select the option “Install Gaia on this system”, and hit enter.
 
 	Select the OK option and hit enter
 
 	Select the desired language and select the Ok button, and hit enter. Check the partition configuration, and if it meets your expectation, select Ok, and hit enter.
 
 	Choose a password for default “admin” account, and click OK. Please make a note of the password. There is no default password for the admin user account. You need to give this password manually during installation. This set of credentials will help your login into Gaia for the first time, and later you can change the password, or disable this administrator account and create a new administrator account.
 
 	Next, it will detect and display all network adapters with their exact hardware name, such as eth0 and eth1. When you will perform this operating on the GW1 virtual machine, you will see 4 network adapters. We will configure IP addressing on these network adapters later via the serial console session after installation. So, click on OK button and hit enter.
 
 	Click Tab and hit enter on OK button.
 	Do not do any IP addressing configuration here, just select the OK button and hit enter. We will do IP address configuration later in the lab. 
 
 	Next, select the OK button again and hit enter.
 
 	Next, Gaia operating system installation will begin, it takes some time from 10 to 15 minutes. Once, installation is finished, you will see screen similar to as shown below:
 
 	Select the Reboot button and hit enter. 
Now, the GW1 virtual machine has Gaia Operating System installed successfully and ready for you to play around. Next, we should immediately configure the interface eth0 as per the topology table shared above. Eth0 interface should have an IP address – 192.168.200.11 with a subnet mask of 255.255.255.0. We will configure remaining interfaces later in the chapter.
 
 	Login into Clish mode of GW1 virtual machine, and run following commands:
•	Set interface eth0 state on
•	Set interface eth0 ipv4-address 192.168.200.11 mask-length 24
•	Save config
•	Show interface eth0 ipv4-address
•	Ping 192.168.200.1

 
Now, the GW1 virtual machine is ready to be accessed over the browser using management IP address https://192.168.200.11. The moment you access the GW1 virtual machine over the browser, it will start the ‘Check Point First Time Configuration Wizard’, and provide you options to install software blades like Security Management Server and Security Gateways.  
You have 2 options here, either you can continue with installation of either of the Check point components such as security Management Server and the Security Gateway server or you can also quit the First Time Configuration Wizard. If you choose to quit the configuration wizard, it will take you towards the Gaia Web-UI console where you will be able to do lots of operating system related configurations.
 

For all later part of Installation, please refer to previous chapter ‘Chapter 2 – Installation’ for clear step by steps instructions. 
Now, we will explore all different features and options provide by Gaia Operating System. We will do real labs to learn and understand concepts. 
We are going to learn following features and technologies
 	Web-UI Console Navigation
 	Expert Mode
 	Hostname
 	IPV6
 	Management Connectivity
 	Web Daemon
 	Web Port
 	Session Timeout
 	Password Policy
 	Users
 	Roles vs Users
 	Interfaces
 	Dynamic IP Addressing 
 	Bond Interfaces (Link Aggregation)
 	Aliases 
 	System Commands
 	DNS
 	Advance Routing
 	Static Routing
 	RIP












Technologies and Features in Gaia
Web-UI Console Navigation
Gaia Web-UI console is a powerful and rich GUI console. It is light weight also. We will explore many features, commands and functions throughout this chapter. But, in this short topics, I just want to make you familiar with some of the common and well known features. 
The top ribbon on the Gaia Web-UI console provides following switches:
 
1.	Hostname 
2.	Configuration Lock 
3.	Open Terminal
4.	Open Scratchpad
5.	User Identity
6.	Sign Out
7.	Check Point Gaia portal logo
The screen is divided into two main sections. It acts like a windows explorer with left and right sides. The left side displays options and the right side displays configuration details. 
The overall configuration is divided into 6 main sections, and many 50+ subsections. Following are the main 6 configuration sections:
1.	Network Management

2.	System Management

3.	Advanced Routing 

4.	User Management

5.	High Availability

6.	Maintenance

7.	Upgrades (CPUSE)	



Gaia portal provides 2 different types of view modes; Basic & Advanced View Modes. Advanced view mode provides details about Advanced Routing, which is not provided by Basic View Mode.
 
Expert Mode
There are multiple shell environments available in the Gaia Operating System. The default shell environment is ‘Clish shell environment’ which is represented as ‘/bin/cli.sh’. This shell environment is also known as ‘less permissive’ or ‘restricted shell environment’ as it does not provide access to system level or low system specific functions. 
/cli.sh provides access to all Gaia clash commands. But it does not give access to low level system functions. Sometimes administrators also refer it as a non-expert mode. 
Administrator by default lands into clash shell environment, and then from here he/she can enter into bash shell environment or expert mode by entering a command ‘expert’. But before that, he/she must set a password for ‘expert mode’ with the command If an administrator is mapped to ‘bin/bash’ shell environment, then he will by default and automatically land into ‘expert mode’ without entering any password. 
Check the current shell environment for an ‘admin’ administrator account using the Gaia Web-UI console.
 
Login into GW1 virtual machine clash mode and look carefully the prompt.
 

Now, if you want to switch from clash shell environment to bash shell environment, then you need to first setup a password for expert mode.
•	Set expert-password
 
Now, you can use a command ‘expert’ to quickly access the bash shell environment or expert mode. It will ask you for a password before providing you the access.
 
Finally, you are into expert mode, and this is how the expert mode prompt looks like
 
So, if you logout and try to login again using the ‘admin’ administrator account, it will not take you directly into bash shell environment, first you need to login into clash shell environment  enter a ‘expert’ command from the clash shell environment  enter a password for the expert mode  and then you will be given entry into bash shell environment expert mode.
So, you can also change the default shell for an administrator from clash shell to bash shell using the Gaia Web-UI console or the Gaia Clish Mode so that you automatically login into bash shell environment. 
Let’s change the shell environment for an administrator ‘admin’ from ‘/bin/cli.sh’ to /bin/bash’ using the Gaia Web-UI console, and then try to login.
 

 
Now, let’s try to login into clash mode, and you will notice that you directly landed into bash shell environment and in expert mode.
 
Hostname
Let’s setup a hostname of Security Management Server as “SMS-TTA-Delhi”, and Security Gateway as “GW1-TTA-Delhi”.
Use these commands on the Security Management Server: 
•	set hostname SMS-TTA-Delhi
	 
Use these commands on the Security Gateway Server: 
•	set hostname GW1-TTA-Delhi
 
IPV6
Gaia does support IPV6 functionalities. IPv6 is not enabled by default. Hence, we need to enable it first. Enabling IPv6 needs a reboot, so please plan it in advance and get appropriate approvals before enabling and rebooting the virtual appliance. 
Use Case # 2– please check if IPV6 is enabled on Security Gateway via Gaia portal and Gaia Clish mode:
Solution – please perform these steps to check the status, and enable IPv6 functionality using the Gaia portal & Gaia Clish mode:
 	Login into Security Gateway Virtual Machine Web-UI console using https://192.168.200.11 	 
 	Login with right set of credentials.
 	obtain the configuration lock by clicking on the Lock on the top of the screen.
 
 	Go to System Management section  Go to System Configuration tab
 	Here, you will the status of IPv6.
 
 	Click on ‘On’ option, and click on Apply. It was all you for a reboot, so reboot the system.

 
 	Login into GW1 virtual machine after reboot into Gaia clash mode. 
 	Use following command to see the current status of IPv6:
•	Show ipv6-state  
   
 	 Use this command to enable and disable IPv6 using the Gaia Clish Mode
•	Set ipv6-state on
•	Save config
•	Reboot
 
Management Connectivity
Management port is an interface in Gaia OS which is used to accept all connections initiated by administrators from their working station, destined to the Check Point component (either security management server or security gateway). Management connectivity is the first most connectivity to be looked after once Gaia OS is installed. By default, the first Hardware interface as in ‘eth0’ either in the virtual appliance or in the Open Servers is selected to be the management port, but we can also change this behavior. 
We can configure any other hardware interface also as a management port. So, any one hardware interface will be a management interface at a time, we cannot have 2 hardware interfaces as a management port at the same time. 
Use Case # 3 – Perform following labs for the Management Interface:
 	Check the current management interface on the Security Gateway virtual machine using the Gaia portal & the Gaia Clish Mode.
 	Change the management interface to ‘eth2’ using the Gaia portal & the Gaia Clish Mode.
Solution - Please perform these steps to see & change the current Management Interface using the Gaia portal:
 	Login into Security Gateway Virtual Machine Web-UI console using https://192.168.200.11 	 
 	Login with right set of credentials.
 	obtain the configuration lock by clicking on the Lock on the top of the screen.
 
 	Go to Network Interfaces Tab on the right side of the screen,
 	Go to Network Management Section.
 	Here you will see that eth0 is displayed here as a management interface.
 	Click on Set Management Interface under Management Interface section on the right side of the screen.
 	Click on the drop down arrow, and select eth2 from the list, and click on OK.
 
 	Next, you will see a caution message, click OK there as well. 
Solution # 2 – please perform these steps to see & change the current management interface using the Gaia Clish Mode:
 	Login into security management server virtual machine ‘SMS1’ – ‘192.168.200.10’ Clish mode.
 	Login with right set of credentials.
 	Give this command first to see the current management port. We will see that ‘eth0’ is the result of this command
	Show management interface
	 
 	Give this command to first obtain the configuration lock
	Lock database override
	 
 	Give this command to change the management port from eth0 to eth1.
	Set management interface eth1
	Save config
	Show management interface
	 
Web Daemon
Gaia Web-UI console is an easy to use interface to do all operating system related configurations. By default, you can connect to Gaia virtual machine over port 80 and 443. The Web daemon or the HTTP service is up and running by default. In case if you want to restrict administrators to refrain using the web-UI console, then you can also stop the HTTP daemon. 
Use Case # 4 -- check if the Web daemon is up and running using the Gaia Clish Mode.
Solution – please perform these steps to see if the Web daemon is up & running using the Gaia Clish Mode:
 	Login into security Gateway virtual machine ‘GW1’ – ‘192.168.200.11’ Clish mode
 	Login with right set of credentials.
 	Give this command first to see the status of web daemon
•	Lock database override
•	Show web daemon-enable
 

Use Case # 5 -- Stop the Web Daemon on the Security Gateway virtual machine so that nobody can access it over the web browser using the Gaia Clish mode.
Solution – please perform these steps to stop the Web daemon running on the Security Gateway virtual machine using the Gaia Clish Mode:
 	Login into security Gateway virtual machine ‘GW1’ – ‘192.168.200.11’ Clish mode
 	Login with right set of credentials.
 	Give these commands to see the status of web daemon, & stop the web daemon:
•	Lock database override
•	Show web daemon-enable
•	Set web daemon-enable off
•	Save config
•	Show web daemon-enable
 
 	Access the Gaia virtual machine over the browser https://192.168.200.11, it should not be accessible. Now you should see a web page error

 
Web Port
Gaia Web console listens on port TCP 443 by default. Cause 443 is the standard default port for HTTPS protocol. As an administrator, you can also change this default port from 443 to any other port for security reasons. Once you change the port to any other custom port, then you need to append that port to the IP address in the browser address bar. 
As an example, if we change the default SSL port from 443 to 4430 for the security gateway virtual machine, then the complete address will be https://192.168.200.11:4430 
You can use either the CLI mode or the SmartConsole to change the SSL port from default 443 to any other port number. It is recommended to change the port using the SmartConsole. If you try to change it using the CLI mode, Gaia will return you a warning similar to shown below.
 
Use Case # 6 – Let’s change the default HTTPS port from 443 to 4430 of the Security Gateway virtual machine using the SemartConsole
Solution – please use these steps to change the default HTTPS port from 443 to 4430 using the SmartConsole
 	Launch SmartConsole GUI client, and 
 	Login into Security Management Server using admin credentials.
 	Go to Gateways & Servers Tab
 	Double click on Gateway object
 	Go to Platform Portal Tab
 	Type ‘https://192.168.200.11:4430’ as an address in the Main URL field box
 	Click on OK button,
 	Install the policy
 
 	Login into Security Gateway Virtual machine Clish Mode using serial connectivity or putty.exe SSH application. 
 	And give following command to see the current Web Port.
•	Show web ssl-port
 
 	Now, try to connect to the Security Gateway virtual machine using the Gaia Mode with – https://192.168.200.11:4430

 
Use Case # 7 – Let’s change the default HTTPS port from 4430 to 443 of the Security Gateway virtual machine using the Gaia Clish Mode.
Solution – please use these steps to change the default HTTPS port from 4430 to 443 using the Gaia Clish Mode
 	Login into security Gateway virtual machine ‘GW1’ – ‘192.168.200.11’ Clish mode
 	Login with right set of credentials.
 	Give these commands to see and change the HTTPS port from 4430 to 443
•	Lock database override
•	Show web ssl-port 
•	Set web SSL-port 443
•	You will receive a warning message, Press Y and hit enter.
•	Check if the SSL port has been changed or not using show web SSL-port command.
•	Show web ssl-port
 
•	Try to access the Management Server virtual machine over Web Console using https://192.168.200.11:443 
 
Session Timeout
Default inactivity timeout setting for web protocols session is 10 minutes, & Command Line Shell is also 10 minutes. As an administrator, if you do frequent work on Gaia OS such as adding routes or ARP entries, then may need to login several times due to inactivity timeout. 
you can increase the inactivity timeout for WEB-UI as well as Command-Line shell from default 10 minutes to 60 minutes or more to avoid regular login attempts. 
Range allowed is from 1 to 720 minutes. 
Use Case # 8 – check & change the current web session & Command-Line timeout session using the Gaia portal from 10 minutes to 60 minutes
Solution – please perform following steps to see & change the current web & Command-Line timeout session using the Gaia portal:
 	Login into Security Gateway Virtual Machine Web-UI console using https://192.168.200.11 	 
 	Login with right set of credentials.
 	obtain the configuration lock by clicking on the Lock on the top of the screen.
 
 	Go to System Management Tab on the left side of the screen.
 	Go to Session Tab
 	Here you can see the default session timeout for both Web and Command-Line session. Below is a screenshot:
 
 	Change the web session timeout to 60 minutes.
 	Change the Command Line Shell session timeout to 60 minutes.
 	Click on Apply button.
 
Use Case # 9 – Check & Change the current web session & Command-Line timeout session using the Gaia Clish Mode from 10 minutes to 60 minutes.  
Solution – please perform following steps to see & change the current web & Command-Line timeout session using the Gaia Clish Mode:
 	Login into security Gateway virtual machine ‘GW1’ – ‘192.168.200.11’ Clish mode
 	Login with right set of credentials.
 	Give these commands to see & change the Web and Command-Line Shell session timeout setting
•	Lock database override
•	Set web session-timeout 60
•	Save config
•	Show web session-timeout
 



Users, Roles & Passwords 
Password Policy
Personally, I believe that the first most configuration item to look after and fine tune is the password policy. By default, password policy is set with minimum most controls. you must understand password policy.  
Following are some of the default weak controls & settings in the password policy:
 	By default, minimum password length is 6 characters, you should increase it to 10 characters to make sure that passwords are strong enough. 
 	By default, you can use upper case letter, low case letters, digits from 0 to 9, and all other combinations of special characters for your password.
 	By default, password is set to never expire. 
 	By default, password history is enabled, and you cannot reuse last 10 passwords. 
 	By default, password hashing algorithm used is SHA512.
 	By default, admin user account is set to never lockout after password expires. 
 	By default, unlimited failed login attempts are allowed. Security Administrator must change this as per organization password policy.
You can access password policy under User Management section in the Web-UI console. Below is a screenshot:
 
Use Case # 10 - Let’s change the default password policy as per below requirements using the Gaia portal. 
 	Change the Password length to minimum 10 characters.
 	Administrators should not be able to reuse last 20 used passwords.
 	Password should expire every 45 days, and notification should be triggered before 5 days. And if an administrator did not change it in within 10 days, then the account should be locked after 10 days. 
 	Only 5 failed login attempts are allowed.
Solution - Please perform these steps to see & change the default password policy as per requirements set above using Gaia portal:
 	Login into Security Gateway Virtual Machine Web-UI console using https://192.168.200.11 	 
 	Login with right set of credentials.
 	obtain the configuration lock by clicking on the Lock on the top of the screen.
 
 	Go to User Management Tab on the left side of the screen,
 	Go to Password Policy Section.
 	You should see the landing page of the Password Policy section

 
 	First change the Minimum Password length to 10 characters as per shown below:
 
 	Change the History Length field to 20 to prevent reuse of last 20 used passwords in the ‘Password History’ section. 
 
 	Click the option “Passwords expires after” and enter 45 Days in the box. Enter 5 in the field against “warn users before password expiration”, and put 10 days in the field “Lockout user after”. ‘Password never expire’ option is not checked that means the same password will not run till the end of their life  and administrators will be forced and prompted to change the passwords every 45 days. All administrators will be warned and notified 5 days prior to password expiring. In a situation if an administrator has not renewed its password in 45 days, so after 10 days the specific administrator account will be locked out, and will no longer will in service. Refer to the screenshot below:
 
 	By default, firewall administrators can use unlimited attempts for login purpose. This is a weak security control and it can generate lots of opportunities for the Brute force password attacks. Therefor administrator should immediately change this setting and set some value to restrict the count of failed login attempts. Failed login attempt limit should be as less as possible. In this lab, we will configure this setting to 5 failed login attempts. Have a look at 2 screenshots below, one with the default settings, and the other with the failed login attempt value of 5.

 

 
Use Case # 11 - Let’s change the default password policy as per below requirements using the Gaia Clish mode.
Solution – Please perform these steps to see & change the default password policy as per requirements set above using the Gaia Clish Mode:
 	Login into security Gateway virtual machine ‘GW1’ – ‘192.168.200.11’ Clish mode
 	Login with right set of credentials.
 	Give these commands to see & change the password length to 10 characters
•	Show password-controls min-password-length 
•	Set password-controls min-password-length 10
•	Save config

 

 	Give these commands to see & change the password expiration to 45 days
•	Show password-controls password-expiration 
•	Set password-controls password-expiration 45
•	Save config

 
 	Give these command to change the password expiration warning to 5 days
•	Show password-controls expiration-warning-days 
•	Set password-controls expiration-warning-days 5
•	Save config	 
 	Give these command to change the expiration lockout to 45 days
•	Show password-controls expiration-lockout-days 
•	Set password-controls expiration-lockout-days 45
•	Save config

 

 	Give these commands to change the limit of reusing last used passwords to 20
•	Show password-controls history-checking
•	Show password-controls history-length 
•	Set password-controls history-length 20
•	Save config

 

 	Give these commands to see the failed login attempt settings & set the failed login attempt limit to 5 counts
•	Lock database override
•	Show password-controls deny-on-fail enable
•	Show password-controls deny-on-fail block-admin
•	Show password-controls deny-on-fail failures-allowed
•	set password-controls deny-on-fail enable on
•	set password-controls deny-on-fail block-admin on
•	set password-controls deny-on-fail failures-allowed 5
 

 

Users
User accounts are those individuals who can login into Gaia Operating system with some assigned permissions and perform various tasks or activities. By default, there are 2 user accounts created in the Gaia Operating System. Both these user account are also loaded with default Roles, permissions and feature sets.
The default administrator account created during Gaia Installation is a member of the ‘adminRole’ and has access to all the commands and features supported. You can create many other administrator accounts if you are logged into system using the ‘admin’ account. As a best practice this default administrator account named ‘admin’ should be disabled and a new administrator account should be created with some unique name. 
 
Roles
Roles work like containers, and they can contain many administrator user accounts as members. Roles are preloaded with some permission packs and command sets. All these permissions and command sets are automatically inherited or assigned to a user once that user account becomes the member of the specific Role. 
There are 2 default Roles created in the Gaia Operating System and both the roles also have user assigned to them. 
Role named ‘adminRole’ has a user account ‘admin’ assigned by default as a member. This Role has some access to 154 features and permission to run 49 commands. Refer to the screenshot below:
Roe named ‘monitorRole’ ha a user account ‘monitor’ assigned by default as a member. This Role has access to 153 feature sets and no permission to run any command. Refer to the screenshot below:
You can edit these default Roles and add or remove features or commands. 
 
Roles vs Users
One of the major difference to understand between user and a Role is that Role cannot login into Gaia Operating System, only a user can login. Passwords are not assigned to roles, rather assigned to users. 
You cannot assign specific permissions and feature sets to individual users. On the other hand, Roles are pre-loaded with permissions and command sets. Permissions can be added or removed from a role or a new role can be stitched to fit the requirements. You can assign many members to specific Role. One Role can contain many administrator accounts as members.
User account can be locked but roles cannot be locked. 
Use Case # 12 -- Let’s perform all the activities listed below using the Gaia portal.
 	Create a new Role named ‘raviRole’ and assign all features with Read/Write permissions and also activate all external commands. 	
 	Create a new administrator account with the name ‘ravi’.
 	Assign the role ‘raviRole’ to admin user ‘ravi’.
 	Try to login into the Gaia Operating system with ‘ravi’ admin account.
Solution -- Please perform these steps to perform all the tasks using Gaia portal:
 	Login into Security Gateway Virtual Machine Web-UI console using https://192.168.200.11 	 
 	Login with right set of credentials.
 	obtain the configuration lock by clicking on the Lock on the top of the screen.
 
 	Go to User Management Tab on the left side of the screen.
 	Go to Roles Tab, and click on Add button
 	Go to ‘Features’ tab first and check each feature drop down menu in the ‘R/W’ column, and select ‘Read/Write’ as a permission. Do this for all the features listed. It’s a lengthy exercise and will consume lots of time. 
 
 	Go to ‘Extended Commands’ tab and check each command set in the ‘Active’ Column. There are around 48 external commands listed, so check all the options.
 
 	Click on Ok button, and finally this Role is created with the name ‘raviRole’.
 
 	Role is created, now we will create an admin user, assign this role to the admin user.
 	Go to Users Section  Click on Add button, and fill the form as per below details:
•	Login Name: ravi
•	Password: type a complex password here.
•	Shell: /bin/bash
•	Access Mechanism: check ‘Gaia API’.
•	Available Role: select adminRole
 

Home Directory field displays the current subdirectory created for the new user. You can also create a specific subdirectory manually for the user matching the exact username in the parent directory ‘/home/’. An administrator can also create a subdirectory manually in the ‘/home/’ directory before creating a user, and map it in the ‘Home Directory’ field. If home directory is not created prior to creating a new user, then it will be created automatically.
By default, any new administrator is created, it is assigned the least permissive shell, known as Clish mode, ‘/bin/cli.sh’. But, you can choose any shell manually from the list while creating a new user. 

There are couple of other shell available as well, such as:

/etc/cli.sh 	

/bin/csh	

/bin/sh

/bin/tcsh

/usr/bin/scponly

/sbin/nologin




/etc/cli.sh is the default shell option, & ‘/bin/bash’ is known as Bash Linux Shell. this shell allows user to work with the Expert mode, and you can run the Clish command to enter the Gaia Clish.  

UID field by default has a value ‘zero’. Always remember below 2 main properties related to UID:
 	Integer 0 – UID with integer ‘0 or zero’ is a default option and used for administrator accounts.
 	Integer 103 – 65533 – UID with integer between ‘103 and 65533’ is not default and used for non-administrator user accounts.

 	Administrator user account is created as per requirements given above. See screenshot below:
 
 	Now, let’s disable the default Administrator account named ‘admin’
 	Log out of the Gaia Web-Console, and login again using the newly created admin account ‘ravi’.
 	Here is my screen, my login to the Gaia web console is successful with ‘ravi’ admin account.
 



Use Case # 13 -- Let’s perform all the activities listed below using the Gaia Clish Mode.
 	Create a new Role named ‘raviRole’ and assign all features with Read/Write permissions and also activate all external commands. 	
 	Create a new administrator account with the name ‘ravi’.
 	Assign the role ‘raviRole’ to admin user ‘ravi’.
 	Try to login into the Gaia Operating system with ‘ravi’ admin account.
Solution -- Please perform these steps to perform all the tasks using Gaia Clish Mode:
 	Login into security Gateway virtual machine ‘GW1’ – ‘192.168.200.11’ Clish mode
 	Login with right set of credentials.
 	Give these commands to create a new role with all features and command sets, create a new admin user and assign the role to the admin user.
•	Lock database override
•	Add rba role raviRole domain-type system all-features
•	Save config
•	Add rba user ravi roles raviRole
•	Save config
 

As a best practice, Security Administrators should immediately do the following to strengthen the security:
 	Create a new administrator with admin role assigned with a name other than admin
 	Strengthen the password policy
 	Change the default SSL port from 443 to something else.







Interfaces
Gaia Operating System is a powerful Operating system and it does provide many different types of configurations for interfaces. These are the following types of interface configurations supported by Gaia OS:
	Alias
	VLAN
	VXLAN
	Bond
	Magg
	Bridge
	Loopback
	VPN Tunnel
	6in4 Tunnel
	PPPoE
	GRE

Detailed explanation of each type of interface type is out of scope of this book. The most basic and common type of interface configuration is an L3 configuration, in which an IP address is assigned either statically or dynamically to an interface.
Use Case # 14 – please configure 4 interfaces of the Security Gateway virtual machine with below shared IP addressing details using the Gaia portal. Login into Security Gateway virtual machine using its management IP address – 192.168.200.11.
 	Eth1 – 192.168.137.11	255.255.255.0
 	Eth2 – 192.168.70.11 	255.255.255.0
 	Eth3 – 192.168.80.11	255.255.255.0
Solution -- perform these steps to configure IP addresses manually on interfaces using the Gaia portal:
 	Login into Security Gateway Virtual Machine Web-UI console using https://192.168.200.11 	 
 	Login with right set of credentials.
 	obtain the configuration lock by clicking on the Lock on the top of the screen.
 
 	Go to Network Management Tab on the left side of the screen, & Go to Network interfaces tab
 	Select the interface ‘eth1’, and click on edit button, and configure IP addresses as per screenshot shared below:
 
 	Select the interface ‘eth2’, and click on edit button, and configure IP addresses as per screenshot shared below:
 
 	Select the interface ‘eth3’, and click on edit button, and configure IP addresses as per screenshot shared below:
 
 	This is how all the three interfaces look after above configuration is complete:
 

Use Case # 15 – please configure 4 interfaces of the Security Gateway virtual machine with below shared IP addressing details using the Gaia Clish mode. Login into Security Gateway virtual machine using its management IP address – 192.168.200.11.
 	Eth1 – 192.168.137.11	255.255.255.0
 	Eth2 – 192.168.70.11 	255.255.255.0
 	Eth3 – 192.168.80.11	255.255.255.0
Solution -- perform these steps to configure IP addresses manually on interfaces using the Gaia Clish Mode:
 	Login into security Gateway virtual machine ‘GW1’ – ‘192.168.200.11’ Clish mode
 	Login with right set of credentials.
 	Use these commands to see the state of all the interfaces first:
•	Show interface eth1 state
•	Show interface eth2 state
•	Show interface eth3 state

 
 	Use thee commands to see if there is any IP address assigned on the interfaces:
•	Show interface eth1 ipv4-address
•	Show interface eth2 ipv4-address
•	Show interface eth3 ipv4-address

 

 	Use these commands to set the IP addresses as per requirements on the interfaces
•	set interface eth1 ipv4-address 192.168.137.11 mask-length 24
•	set interface eth2 ipv4-address 192.168.70.11 mask-length 24
•	set interface eth3 ipv4-address 192.168.80.11 mask-length 24
•	save config

 

 	Use these commands to validate if the IP addresses are assigned correctly on the interfaces:
•	Show interface eth1 ipv4-address
•	Show interface eth2 ipv4-address
•	Show interface eth3 ipv4-address

 

Dynamic IP Addressing 
DHCP stands for Dynamic Host Configuration Protocol and it is used to solve the problem of distributing IP addresses dynamically to endpoints and client. DHCP works in both client/server model. 
Check Point Gaia can act as a DHCP server and distribute IP addresses dynamically to several different clients (windows and Linux systems) in the same broadcast domain. 
You can also configure interfaces in Gaia OS to act as a DHCP client so that they can obtain IP addresses dynamically from the DHCP server in the same broadcast domain.  
Dynamic IP addresses are not static in nature, that means these IP addresses are not permanent, and subject to change anytime. Dynamic IP addresses get released and renewed as per the configured leased time. Leased time is a configuration item in the DHCP server, which defines how long the configured IP address will be active. Leased time can be 1 Day, 1 Week, 1 Month or more. 
Perform these steps to configure Gateway1 virtual machine interfaces eth2, and eth3 to receive an IP address dynamically from the DHCP Server using the Gaia Web-UI console:
 	Login into Security Gateway Virtual Machine Web-UI console using https://192.168.200.11 	 
 	Login with right set of credentials.
 	obtain the configuration lock by clicking on the Lock on the top of the screen.
 
 	Go to Network Management Tab on the left side of the screen, & Go to Network interfaces tab
 	Select the interface ‘Eth2’ from the list of interfaces, and click on Edit button
 	Enable the interface by checking the box against ‘Enable’ option if not checked already.
 	Put appropriate comments in the comment box
 	Make sure that the IPV4 tab is currently selected
 	Click on the option “obtain IPv4 address automatically”, and click OK.
 	Repeat the same steps for interface ‘Eth3’ also.
 
 	Now, you will see that both interfaces ‘Eth2’, & ‘Eth3’ will be shown as up, and have obtained IP addresses dynamically from the DHCP server in the same broadcast domain. 
 
 	Check the IP address of interface eth2 and interface eth3 using the command line mode with these commands. You will notice that IP address for ‘eth2’ has changed from 192.168.70.11 to 192.168.70.128, and there is a label of ‘dhcp’ is also tagged along with the IP address. Same for eth3 interface also. 
	 
		
 	So, we have configured 2 Ethernet interfaces as DHCP client and obtained IP address from the DHCP Server in the same broadcast domain. Remember that these IP addresses are dynamic in nature and not static.
 	Now, let’s do some validation testing, login into Security Gateway virtual machine into Clish mode and run following commands:
•	Lock database override
•	Show interface eth2 ipv4-address
•	Show interface eth3 ipv4-address
•	Ping 192.168.70.1
•	Ping 192.168.80.
	 

 	you can use following commands to see the DHCP client configuration and remove the interfaces from DHCP client configuration.
•	Lock database override
•	Show dhcp client interfaces
•	Delete dhcp client interface eth2
•	Delete dhcp client interface eth3
•	Show dhcp client interface
	 






Bond Interfaces (Link Aggregation)
Check Point Security Gateway supports Link Aggregation functionality. Link Aggregation joins multiple physical interfaces into one single virtual interface. This virtual interface is known as a bond interface. Bond interface is created to increase the throughput by adding multiple physical interfaces. 
Imagine if all the interfaces in a security gateway have a throughput of 1 Gbps, and if you create a bond interface by joining 2 interfaces, then the aggregated throughput capacity of this virtual bond interface will be 2 Gbps. 
All the member interfaces in a bond interface also support high availability and load sharing capabilities. These member interfaces are also referred as slave’s interfaces and do not have IP addresses assigned to them. Before you select any physical interface as a member of a bond interface, remove the IP address configuration from the interface. 
You can configure IPv4 or IPv6 IP address on bond interfaces. Also, you can either give IP address statically or use DHCP to obtain IP addresses dynamically. 
You can use maximum of 8 physical interfaces as slave interfaces to form a single bond interface.
AS every physical interface has some IDs, like eth0, eth1, eth2. Similarly, every bond interface is also assigned a Bond ID, like ‘bond1’, ‘bond2.
 
Use Case # 16 -- Create a Bond Interface on Security Gateway virtual machine using the Gaia portal, and validate same via the Gaia Clish mode for below configuration items:
 	Bond Interface ID: bond2 
 	Slave Interfaces: eth2, and eth3
 	IP Address method: Dynamic
 	IP address: obtain dynamically
 	Operation Mode: Active-Backup
 	Connectivity Testing: Check the IP address given to bond interface, and try to ping the core switch IP address 192.168.80.1
 	Delete the bonding interface ‘bond’ using CLI mode.
Solution -- perform these steps to create a virtual ‘Bond Interface’ as per requirements shared above using the Gaia portal:
 	Login into Security Gateway Virtual Machine Web-UI console using https://192.168.200.11 	 
 	Login with right set of credentials.
 	obtain the configuration lock by clicking on the Lock on the top of the screen.
 
 	Go to Network Management Tab on the left side of the screen, & Go to Network interfaces tab
 	Click on Add button, and select ‘Bond’.
 	Go to Bond Tab, and type ‘2’ in the Bond Group field box.
 	Select interfaces ‘eth2’, and ‘eth3’ and click on Add button, now both these interfaces will be shown in the Chosen Interface box.
 	Select ‘Active-Backup’ as an Operation Mode
 
 	Go to Advanced Tab, and select ‘eth2’ as a primary interface.
 
 	Go to IPv4 Tab and select ‘Obtain IPv4 address automatically’, and click OK.
 
 	Wait for some time and refresh the screen, you will see a new Bond interface in the list of interfaces with the name ‘bond2’, and an IP address – 192.168.80.x and subnet mask 255.255.255.0. (why I said x here cause it’s a dynamic IP address, it will be different in your environment).
 
 	Now, let’s do some validation testing, login into Security Gateway virtual machine into Clish mode and run following commands:
o	Lock database override
o	Show interfaces
o	Show interface bond2 ipv4-address
o	Show interface bond state
o	Ping 192.168.80.1
	 
 	Now, let’s do the last task and remove the bond interface ‘bond2’ from the Clish Model. Please run following commands:
•	Lock database override
•	Delete bonding group 2 interface eth2
•	Delete bonding group 2 interface eth3
o	Delete bonding group 2
o	Show interfaces
 

Aliases 
Sometimes you need to configure more than one IP address on a single interface. ‘Aliases interface’ feature lets you assign multiple IP addresses on a single interface. All the IP addresses configured on a single interface will resolve to the common MAC address as an ARP response. ‘Alias interface’ can be configured either via Gaia Mode or Clish Mode. 
Use Case # 17 – please create an alias interface for ‘eth0’ interface and assign it an additional IP address – 192.168.200.21/24 using the Gaia portal & the Gaia Clish mode.
Solution -- Please perform these steps to create an Alias interface for Ethernet interface ‘eth0’, with an additional IP address of 192.168.200.21/24 using the Gaia portal:
 	Login into Security Gateway Virtual Machine Web-UI console using https://192.168.200.11 	 
 	Login with right set of credentials.
 	obtain the configuration lock by clicking on the Lock on the top of the screen.
 
 	Go to Network Management Tab on the left side of the screen, & Go to Network interfaces tab
 	Click on Add button  then Click on Alias button
 	Go to Alias Tab, and select eth0 in the ‘Member of’ field box
 
 	Go to IPv4 Tab, and type 192.168.200.21, and 255.255.255.0 in the subnet mask field, and click on OK.
 
 	Now, new Alias interface will be created as eth0:1 with an IP address of 192.168.200.21 and the interface is up and running. We can also see that there is already an IP address 192.168.200.11 assigned on ‘eth0’ interface.
 
 	Please perform these commands to check the status of Alias interface in the Clish Mode and delete the same interface
o	Login into Clish Mode of Security Gateway virtual machine
o	Use these commands to check the Alias Interface and delete the same
	Show interface eth0 	
	Delete interface eth0 alias eth0:1
	Show interface eth0 aliases
 
 	Now, we will do some validation testing. We will try to ping both the IP addresses – 192.168.200.11, & 192.168.200.21 from one of the workstation in the Mgmt. VLAN. Both the IP addresses should resolve to the same MAC address. The IP address of the workstation is 192.168.200.1. First, let’s ping both the IP addresses from the workstation, and check if ping connectivity is working or not?
 

 	Then, let’s check the ARP entries on the workstation, you will be surprised to see that both the IP addresses are resolving to a same MAC address. 
 
System Commands
As an administrator, you are always concerned with the health of all the gateway components. If components are healthy, they will be able to contribute effectively and efficiently to improve the security posture. If components are not healthy, it is going to cause downtime or raise an event or incident any time. Continuous monitoring of components such as Memory and Hard Disk usage is very important. You can also watch the usage statistics of Hard Disk and memory using the Gaia portal & the Gaia clash mode.
‘show system’ command set is a multi-utility tool box. It provides many system commands to measure the usage of Hard Disk and Memory. It also provides system commands to see current services running. Below are all the commands offered by ‘show system’ command:
 	Show system disk usage
 	Show system memory status
 	Show system services run-time
Hard Disk Usage can be measured using the following command:
•	Show system disk usage


This command provides you following useful details:
 	Different partitions in the Hard Drive of the Gaia system
 	Different logical volumes available in the Gaia system.
 	Default size allocated to each partition and logical volume.
 	Used hard drive size in exact number and % 
 	And the mounting information.  
 	Below is an output of disk usage from Security Gateway virtual machine.

 
Memory is also a critical health component. You can check the current usage and the available memory size using the command show system memory status command. 
Hard Disk Usage can be measured using the following command:
•	Show system memory status
 
DNS
DNS Server helps in resolving hostnames & FQDN to IP addresses. The Gateway virtual machine must point to organization wide primary and secondary DNS servers to resolve all DNS requests initiated by several clients. 
Use Case # 18 -- let’s set up 4.2.2.2 as a primary DNS server, and 8.8.8.8 as a secondary DNS Server on the Security Gateway virtual machine using the Gaia portal, and the Gaia clash mode.
Solution -- Please perform these steps to setup 4.2.2.2 as primary DNS Server, and 8.8.8.8 as secondary DNS server Gaia portal:
 	Login into Security Gateway Virtual Machine Web-UI console using https://192.168.200.11 	 
 	Login with right set of credentials.
 	obtain the configuration lock by clicking on the Lock on the top of the screen.
 
 	Go to Network Management Tab on the left side of the screen.
 	Go to Hosts and DNS section.
 	Type an IP address 4.2.2.2 in the field of Primary DNS Server.
 	Type an IP address 8.8.8.8 in the field of Secondary DNS Server
 	Click on Apply button
 
Solution # 2 -- Please perform these steps to setup 4.2.2.2 as primary DNS Server, and 8.8.8.8 as secondary DNS server Gaia Clish mode:
 	Login into security Gateway virtual machine ‘GW1’ – ‘192.168.200.11’ Clish mode
 	Login with right set of credentials.
 	Use these commands to set the primary and the secondary DNS server IP addresses using the Gaia clash mode:
•	Lock database override
•	Set dns primary 4.2.2.2
•	Set dns secondary 8.8.8.8
•	Save config
•	Show dns primary
•	Show dns secondary
 

Advance Routing
Let’s discuss Advanced Routing section supported in Gaia Operating System. I assume all my readers have basic understanding with static as well dynamic routing. They must understand the difference between static and dynamic routing protocols. Static routing is an easy business but effective only with small size or organization where routing changes are needed seldom. But, if you are in an organization which has multiple remote sites, offices, and all are connected to each other, new routes need to be added or advertised on frequent basis, then static routing is not a scalable and successful solution. Instead we should use dynamic routing protocols to add or advertise new routing definition to all the routers/gateways in an organization. 
Gaia as an Operating System supports both static as well as different dynamic routing protocols like RIP, and OSPF. Gaia Operating System supports both Interior gateway protocols and Exterior Gateway protocols. It supports RIP and OSPF as part of Interior gateway protocols, and BGP a part of Exterior Gateway protocol. 
We will only concentrate on 2 IGP dynamic routing protocols and do extensive labs to understand their functionalities. 
Static Routing
Static routes can be added in the Gaia Operating System either via Gaia portal or the Gaia Clish Mode. Why, we call it as static routes is that these routes remain persistent and added manually by an administrator? Static routes also are not advertised from peer to peer. adding routes manually on all devices may be hectic. Whenever new networks are created, administrator will have to add routes for this network manually on all the routers and gateways. 
A firewall administrator must have complete understanding of the network topology in an organization. He must be aware of all next hope before adding a static route on a Gateway. Let’s revisit the network topology explain earlier in this chapter
Table: IP addressing details for Quantum Security Gateway.
Site A
Server Role	Hostname	Interface	VMnet	IP Address	Subnet Mask
Quantum Security Gateway	GW1	etho	VMnet0	192.168.200.11	255.255.255.0
Quantum Security Gateway	GW1	eth1	VMnet1	192.168.137.11	255.255.255.0
Quantum Security Gateway	GW1	eth2	VMnet2	192.168.70.11	255.255.255.0
Quantum Security Gateway	GW1	eth3	VMnet3	192.168.80.11	255.255.255.0
Default Gateway in Quantum Security Gateway 1	192.168.137.1

Table: IP addressing details for Quantum Security Management Server.
Site A
Server Role	Hostname	Interface	VMnet	IP Address	Subnet Mask
Quantum Security Management	SMS1	etho	VMnet0	192.168.200.10	255.255.255.0
Quantum Security Management	SMS1	eth1	VMnet2	192.168.70.10	255.255.2550
Default Gateway in Quantum Security Management	192.168.70.11
From the topology we can see that we need to add default gateway as a static route on both Quantum Security Management Server and Quantum Security Gateways. Default Gateway for Security Management Server is 192.168.70.11, and default gateway for Security Gateway server is 192.168.137.1
Use Case # 19 -- let’s set a default gateway 192.168.70.11 on Quantum Security Management Server using the Gaia portal.
Solution -- Please perform these steps to setup 192.168.70.11 as a default gateway on security management server using the Gaia portal:
 	Login into Security Management  server Virtual Machine Web-UI console using https://192.168.200.10  	 
 	Login with right set of credentials.
 	obtain the configuration lock by clicking on the Lock on the top of the screen.
 
 	Go to Network Management Tab on the left side of the screen.
 	Go to IPv4 Static Routes
 	You will see one Default route entry already there.
 	Select that routing entry and click on Edit button
 	Again, select the existing route in the ‘Add Gateway’ subsection, and click on Edit button
 
 	Replace the existing IP with ‘192.168.70.11’ and click on OK button.
 
 	It will take you back to the main screen, click on Save button
 
 	This is how the Default Gateway routing entry appear on the system.
 
 	Login into Security Management Server virtual machine Clish mode, and give this command to check the default gateway.
•	netstat –nr
 

Use Case # 20 – Let’s set a default gateway 192.168.137.1 on Quantum Security Gateway server using the Gaia Clish mode.
Solution -- Please perform these steps to setup 192.168.137.1 as a default gateway on security gateway using the Gaia Clish mode:
 	Login into security Gateway virtual machine ‘GW1’ – ‘192.168.200.11’ Clish mode.
 	Login with right set of credentials.
 	First check if the default gateway entry is added or not using ‘netstat –nr’ command
 
 	Give these commands to add a static default gateway
•	Lock database override
•	Set static-route 	default nexthop gateway address 192.168.137.1 on
•	Save config
 
 	Give this command again to check if default gateway entry is added using ‘netstat-nr’ command.
 
RIP
RIP stands for Routing Information Protocol. This Routing protocol come under dynamic routing protocol category and first most protocol to learn. The main job of Routing Information Protocol is first to learn its directly connected routes and then to broadcast same routing details to its peer and neighbor. RIP daemon is not enabled by default. 
RIP routing protocol is the oldest routing protocol in use today. RIP was introduced with Vesion1. IT came with lots of new features but also with some security vulnerabilities. These were fixed in the later version called as Version 2.  
There are many other features supported by RIP, that you must be aware off. Let’s discuss them:
 	Auto-summary    	
 	Export-routemap		
 	Import-routemap
 	Interface		
 	Update-interval		
So, the main job of RIP is to learn the routes from any one router/gateway and update same to the other router/gateway running RIP in the same AS. RIP updates are sent every 30 seconds. 
Summary
We have learnt configuration of different features in this lesson. We have used several ‘show’ & ‘set’ commands in this chapter. Let’s quickly see all the ‘set’ commands used in this chapter:
 	Set interface eth0 state on
 	Set interface eth0 ipv4-address 192.168.200.11 mask-length 24
 	Set expert-password
 	set hostname SMS-TTA-Delhi
 	set hostname GW1-TTA-Delhi
 	Set ipv6-state on
 	Set management interface eth1
 	Set web daemon-enable off
 	Set web SSL-port 443
 	Set web session-timeout 60
 	Set password-controls min-password-length 10o	
 	Set password-controls password-expiration 45
 	Set password-controls expiration-warning-days 5
 	Set password-controls expiration-lockout-days 45
 	Set password-controls history-length 20
 	set password-controls deny-on-fail enable on
 	set password-controls deny-on-fail block-admin on
 	set password-controls deny-on-fail failures-allowed 5
 	Add rba role raviRole domain-type system all-features
 	Add rba user ravi roles raviRole
 	set interface eth1 ipv4-address 192.168.137.11 mask-length 24
 	set interface eth2 ipv4-address 192.168.70.11 mask-length 24
 	set interface eth3 ipv4-address 192.168.80.11 mask-length 24
 	Set dns primary 4.2.2.2
 	Set dns secondary 8.8.8.8
 	Set static-route 	default nexthop gateway address 192.168.137.1 on
 	save config	
