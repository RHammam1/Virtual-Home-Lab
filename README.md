# Home Lab Setup with VirtualBox and Active Directory

## Overview

This project documents the setup and configuration of a home lab environment using VirtualBox, focusing on creating a simulated network infrastructure with Windows 10 and Windows Server 2019 virtual machines. The primary goal is to replicate real-world scenarios and gain hands-on experience in areas such as virtualization, network administration, and Active Directory management.

## Key Steps

### 1. Virtual Machine Deployment

- Downloaded and installed VirtualBox for virtualization.
- Deployed Windows 10 and Windows Server 2019 virtual machines to create a client-server architecture.

### 2. Active Directory Setup

- Installed and configured Active Directory Domain Services (AD DS) on the Windows Server 2019 VM.
- Completed post-deployment configuration for optimal performance and security.

### 3. Networking

- Established IP addressing schemes and configured network connectivity between virtual machines.
- Implemented Routing and Remote Access services for enhanced remote connectivity.
- Configured NAT for internet connectivity within the virtualized environment.

### 4. User and Group Management

- Created and managed organizational units, user accounts, and groups within the Active Directory environment.
- Elevated administrative control by designating a domain admin and implementing secure user and access management.

### 5. DHCP Configuration

- Deployed and fine-tuned DHCP to automate IP address assignment for efficient network management.

### 6. PowerShell Scripting

- Utilized a PowerShell script to mass-create users in the Active Directory Users and Computers section, simulating real-life scenarios.

### 7. Client-Server Interaction

- Simulated client-server interaction by creating a virtual machine as a client computer, seamlessly connecting it to the domain controller via an internal network.

## Getting Started

1. Clone this repository to your local machine:

    ```bash
    git clone https://github.com/your-username/home-lab-setup.git
    ```

2. Follow the detailed setup instructions in the documentation folder to recreate the home lab environment.

3. Explore the PowerShell scripts in the scripts folder for automation examples.

## Contributing

Feel free to contribute by submitting issues, providing suggestions, or making pull requests to improve the project.

## License

This project is licensed under the [MIT License](LICENSE).
