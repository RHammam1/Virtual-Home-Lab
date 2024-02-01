# Home Lab Setup with Virtual Box and Active Directory

## Overview

This project documents the setup and configuration of a home lab environment using Virtual Box, focusing on creating a simulated network infrastructure with Windows 10 and Windows Server 2019 virtual machines. The primary goal is to replicate real-world scenarios and gain hands-on experience in areas such as virtualization, network administration, and Active Directory management.

![Network Graph (1)](https://github.com/RHammam1/Virtual-Home-Lab/assets/56901837/f6b74eb4-c07c-4266-bf89-16bcc18cf88d)

## Key Steps

### 1. Installing tools

- Downloaded and installed Virtual Box for virtualization.
- Downloaded Windows 10 ISO and Windows Server 2019 ISO.

### 2. Virtual Box Setup

- Created a new virtual machine named 'DC' to act as the domain controller. This machine will have Windows Server 2019 installed.
- Created a new virtual machine named 'CLIENT1' to act as a client machine. This machine will have Windows 10 Pro installed.

### 3. Setup IP Addressing

- As shown in the network graph, the domain controller will have two network adapters: one connecting to my home internet ('INTERNET') and one being an internal network ('INTERNAL') that client machines will connect to.
- Identified my home network in adapter options and renamed it to 'INTERNET'. The other adapter is renamed to 'INTERNAL'.
- Went into the IPv4 properties of the internal network and assigned it the IP of 172.16.0.1, a mask of 255.255.255.0, and a DNS of 127.0.0.1 (loopback address). 
  
![image](https://github.com/RHammam1/Virtual-Home-Lab/assets/56901837/18b3b5b9-1ba7-40de-9e4c-1e6299a742f2) ![image](https://github.com/RHammam1/Virtual-Home-Lab/assets/56901837/89f719ca-55fb-4b6a-a2cb-a99e7b29f33d)

### 4. Active Directory Domain Services
- Installed Active Directory Domain Services via Server Manager.
- In the configuration wizard, added a new forest, naming it 'mydomain.com'.
- These steps upgraded this virtual machine into the domain controller.

### 5. Active Directory Users and Computers
- Created a new organizational unit to create a new administrator account.
- Entered the properties of this new user, making it a member of 'Domain Admins'.  ![image](https://github.com/RHammam1/Virtual-Home-Lab/assets/56901837/256f38da-171f-4640-9037-b5b00ead83e3)
- Signed out and signed into the newly created domain admin account.

### 6. Configuring remote access and DHCP server. 
(This allows our windows 10 client to be on the private internal network but still acesss the internet via the domain controller.) 

- Installed Remote Access via Server Manager, ensuring to select the routing service to be installed.
- Configured routing and remote access and installed NAT (Network Address Translation) to use my home network to access the internet.
- Installed DHCP via Server Manager, allowing clients on the network to automatically get their IP address.
- Created a new scope to give IPs to clients in a specified range (172.16.0.100-200).  ![image](https://github.com/RHammam1/Virtual-Home-Lab/assets/56901837/14ae2e32-aac9-4ed6-9d98-8c7bc0eb6396)


### 7. Powershell script for creating users
- Thanks to Josh Madakor for this public script available from his [GitHub](https://github.com/joshmadakor1)
- Opened an elevated PowerShell, navigated to the unzipped folder containing the script.
- Ran the script creating ~1000 users in a organized unit named '_USERS' simulating a corporate enviorment.
![2024-02-01 16-09-58](https://github.com/RHammam1/Virtual-Home-Lab/assets/56901837/bf256077-968d-435a-bd2c-a1f00b595322)

### 8. Onboarding the client machine
- In the Virtual Box settings for the client machine set the network to 'internal network'
- Started up the machine, ran ipconfig, and pinged a website in Command Prompt to ensure our network properties check out. ![image](https://github.com/RHammam1/Virtual-Home-Lab/assets/56901837/41d6cb11-2ae1-4ab2-9ce5-768a406ee1d7)
- Headed into system properties on the client machine to change the machine's domain to 'mydomain.com' and signed in with an account created earlier.
- In the DHCP - Address Leases on the DC machine, we'll see the address lease of the newly connected client machine. ![image](https://github.com/RHammam1/Virtual-Home-Lab/assets/56901837/5d80278f-9115-4114-bf59-f9e0fb3d40b0)
  
- Along with the computer name in Active Directory Users and Computers - Computers

   ![image](https://github.com/RHammam1/Virtual-Home-Lab/assets/56901837/b0ae8430-9ff0-498b-b386-ef7aa0586a0a)



