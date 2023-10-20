# <p align="center">Ubuntu Remote-Auto-Management System</p> 
 <p align="center">powered by Ansible&trade;</p> 


 ![nexussecurus](/images/nexusecurus.png)


<p align="center">
  <table>
    <tr>
      <th>Supported HW</th>
      <th>Target OS</th>
      <th>Code Stats</th>
      <th>Audience</th>
      <th>Type</th>
      <th>Dependencies</th>
      <th>License</th>
    </tr>
    <tr>
      <td><img src="https://img.shields.io/badge/Architecture-x86_64-blue?logo=intel&logoColor=white"></td>
      <td><img src="https://img.shields.io/badge/Ubuntu-Server-orange?logo=ubuntu"></td>
      <td><img src="https://img.shields.io/badge/YAML-Used-yellow?logo=yaml"></td>
      <td><img src="https://img.shields.io/badge/Role-System%20Administrator-%23197aaa?logo=linux&logoColor=white"></td>
      <td><img src="https://img.shields.io/badge/Automation-Enabled-brightyellow?logo=robot-framework"></td>
      <td><img src="https://img.shields.io/badge/Ansible-2.10%2B-blue?logo=ansible"></td>
      <td><img src="https://img.shields.io/badge/License-MIT-blue.svg"></td>
    </tr>
    <tr>
      <td><img src="https://img.shields.io/badge/ARM-Architecture-blue"></td>
      <td><img src="https://img.shields.io/badge/Linux-Used-yellow?logo=linux"></td>
      <td><img src="https://img.shields.io/badge/Markdown-Used-yellow?logo=markdown"></td>
      <td><img src="https://img.shields.io/badge/Homelab-Geeks-blue"></td>
      <td><img src="https://img.shields.io/badge/Tutorial-Provided-blue"></td>
    </tr>
  </table>
</p>


<br>
<br>
<br>


## <p align="center" > Project Description </p>

How many server instances are not fully up to date, just because its a painful operation just to login into those 100 server instances?  

Here is were Ansible comes to the rescue.

This project repo aims to simplify Linux server and desktop management while exploring all the capabilities of Ansible software. Along with all configuration files already deployed for a easy way to setup, i added a collection of basic Ansible playbooks to automate simple or even some more complex tasks, saving you time and effort.

**Key Features**:

_Remote Control_: Manage Linux systems from anywhere, no matter the distance.  
_Efficiency_: Automate configuration, software installation, and maintenance.  
_Versatile_: Suitable for individuals, IT professionals, and server farms.

**Get Started**:

Down below you will get everything you need to know. Explore our playbooks and streamline your administrative tasks.



---
<br>
<br>

### <p align="center"><a name="table-of-contents"></a>Table of Contents</p>
<br>

- [Ubuntu Remote-Auto-Management System](#ubuntu-remote-auto-management-system)
  - [ Project Description ](#-project-description-)
    - [Table of Contents](#table-of-contents)
  - [Current list of Playbooks for Streamlined Ubuntu Server Management](#current-list-of-playbooks-for-streamlined-ubuntu-server-management)
  - [Role Details](#role-details)
  - [Dependencies and Requirements](#dependencies-and-requirements)
  - [Installation procedure](#installation-procedure)
      - [1 - **Install required packages**:](#1---install-required-packages)
      - [2 - **Configure SSH Access**:](#2---configure-ssh-access)
      - [2.1 - **Generate an SSH key pair**:](#21---generate-an-ssh-key-pair)
      - [2.2 - **Copy the public key to the target host's `~/.ssh/authorized_keys` file**:](#22---copy-the-public-key-to-the-target-hosts-sshauthorized_keys-file)
      - [2.3 - **Test SSH access**:](#23---test-ssh-access)
      - [3 - **Clone the repository into your $HOME**:](#3---clone-the-repository-into-your-home)
  - [Additional information / Documentation **(MUST READ!!!)**](#additional-information--documentation-must-read)
      - [1 - Configure Host Inventory:](#1---configure-host-inventory)
      - [2 - Manage Host Variables:](#2---manage-host-variables)
      - [3 - Configure Group Variables:](#3---configure-group-variables)
      - [4 - Running Ansible Modules:](#4---running-ansible-modules)
      - [5 - Running Ansible Playbooks:](#5---running-ansible-playbooks)
      - [6 - Is REMOTE host user is ROOT?:](#6---is-remote-host-user-is-root)
      - [7 - Avoid using plaintext passwords inside the host\_vars for REMOTE authentication:](#7---avoid-using-plaintext-passwords-inside-the-host_vars-for-remote-authentication)
      - [8 - KNOWN Issues \& Bugs:](#8---known-issues--bugs)
  - [Usage](#usage)
  - [About the Author](#about-the-author)

<br>

---
<br>
<br>

## Current list of Playbooks for Streamlined Ubuntu Server Management  

<br>

1 - [**ubuntu-check-updates**](roles/ubuntu-check-updates/README.md) - Role Description: Check hosts for any pending updates, and list them to the user in console.  
2 - [**ubuntu-setup-init**](roles/ubuntu-setup-init/README.md) - Role Description: Automated initial setup and package installation for Ubuntu-based systems.  
3 - [**ubuntu-nvidia-init**](roles/ubuntu-nvidia-init/README.md) - Role Description: Automated setup for Nvidia GPU drivers and tools on Ubuntu-based systems.

---

<br>
<br>

## Role Details  

Each playbook is purpose-built to simplify a specific aspect or setup configuration of Linux Servers management. Say goodbye to complex, manual tasks, and embrace the power of automation, powered by Ansible.

<br>

## Dependencies and Requirements  


- **Ansible** 2.1+ is required for global use of this repository. <span style="color: red;">(MANDATORY)</span>  
- **Git** is required to clone the repository.  <span style="color: red;">(MANDATORY)</span>  
- **OpensSSH** is required ensure that the host running ansible has access to the desired hosts. <span style="color: red;">(MANDATORY)</span>  



<br>

## Installation procedure  

#### 1 - **Install required packages**:  

  To be able to use Ansible you need to install it, along with some other dependencies.  
  
  Install them with the following command:

```bash
sudo apt update
sudo apt install software-properties-common ansible openssh-server git -y
```  

<br>


  #### 2 - **Configure SSH Access**:

  Ensure you have SSH access to each host where you want to execute a playbook. ansible.cfg in this repository expects an `id_ansible` SSH private key located in `~/.ssh/` for authentication. Set up SSH access as follows:


  *If you want to use your own private key, edit the configuration file ansible.cfg, after cloning the repository, and skip next step **2.1 "Generate an SSH key Pair"***
<br>


   #### 2.1 - **Generate an SSH key pair**:

```bash
ssh-keygen -t ed25519 -b 4096 -f ~/.ssh/id_ansible
``` 

<br>


   #### 2.2 - **Copy the public key to the target host's `~/.ssh/authorized_keys` file**:

```bash
ssh-copy-id -i ~/.ssh/id_ansible user@hostname_or_IPaddress
```  


<br>


   #### 2.3 - **Test SSH access**:

```bash
ssh -i ~/.ssh/id_ansible user@hostname_or_IPaddress
```  

<br>

#### 3 - **Clone the repository into your $HOME**: 
Clone this repository to your home directory, which is configured to work seamlessly with the project. Use the following commands to clone the repository:

```bash
    cd ~
    git clone https://github.com/prenats/nexsec-ansible.git
```

---

<br>


## Additional information / Documentation **(MUST READ!!!)**

This section contains additional information on how to configure hosts files and variables, such as the concept of filenames and directory structure.

It also contains information about some possible errors you may encounter and their respective fixes.

 <br>

#### 1 - Configure Host Inventory:

By default, the hosts are named as "server1," "server2," and so on. If you wish you can keep these default names. However, if you prefer you can custom host and group names:

- Open the `inventory/hosts.yaml` file.
- Update the ip address of each host to the one corresponding to your host. <span style="color: red;">(MANDATORY)</span>
- Update the host and group names to your desired custom names, avoiding symbols like "." or "-".  <span style="color: yellow;">(INFORMATION)</span>

 <br>

#### 2 - Manage Host Variables:

- Each host already has a corresponding file in the `host_vars` directory, located in both the root directory and the `playbooks/host_vars` folder. <span style="color: yellow;">(INFORMATION)</span>

- These files must share the same name as the host you designated in `inventory/hosts.yaml` (e.g., `server1.yaml`, `server2.yaml`). <span style="color: yellow;">(INFORMATION)</span>

- If you modified the default host names in the `inventory/hosts.yaml` file, ensure you rename each file accordingly. <span style="color: yellow;">(INFORMATION)</span>

- Edit the corresponding file (e.g. `host_vars/server1.yaml` or `playbooks/host_vars/server1.yaml`) and add the variables for that host. <span style="color: red;">(MANDATORY)</span>

- These files can include variables such as login username, SSH port, and other host-specific settings essential for automated host access.

 <br>

#### 3 - Configure Group Variables:

- Similarly, each group should have a corresponding file in the `group_vars` directory within both the root directory and the `playbooks/group_vars` folder. <span style="color: yellow;">(INFORMATION)</span>

- The process for naming these files is the same as for host variables (e.g., `group1.yaml`, `group2.yaml`). <span style="color: yellow;">(INFORMATION)</span>

- If you changed the default group names in the `inventory/hosts.yaml` file, make sure to rename each file accordingly. <span style="color: yellow;">(INFORMATION)</span>

- Edit the corresponding file (e.g. `group_vars/group1.yaml` or `playbooks/group_vars/group1.yaml`) and add the common variables for that group if any. <span style="color: red;">(MANDATORY)</span>

- These files can encompass variables such as SSH user, SSH port, SSH private key, and other group-specific settings crucial for automated access to groups with shared configurations like SSH ports and usernames.  
  
  <br>

#### 4 - Running Ansible Modules:

- If you're using the `ansible` command to run modules such as ping or others, make your necessary edits in the files under the `host_vars/` and `group_vars/` directories. <span style="color: yellow;">(INFORMATION)</span>

 <br>

#### 5 - Running Ansible Playbooks:

- For those using the `ansible-playbook` command, make your edits in the files located under the `playbooks/host_vars/` and `playbooks/group_vars/` directories. <span style="color: yellow;">(INFORMATION)</span>

By following these steps, you'll have the freedom to opt for either default or custom host names and effectively manage your inventory and variables. This approach simplifies the process of automating your Ubuntu server systems with Ansible while ensuring organized and efficient configuration management.  

<br>

#### 6 - Is REMOTE host user is ROOT?: 

If your host user is root, then you'll need to enable root access in /etc/ssh/sshd_config file inside that same host. I recommend setting it to prohibit-password authentication instead of allowing password which poses a security risk. <span style="color: yellow;">(ATTENTION)</span>

To achieve this just edit your /etc/ssh/sshd_config:
```bash
sudo nano /etc/ssh/sshd_config
```
Look for line and remove the #, save the file and exit.:
```bash
#PermitRootLogin prohibit-password
```
Then restart the SSH server with:

```bash
sudo service ssh restart
```

Note: The id_ansible.pub key should be added to authorized_keys in root .ssh/ folder.

<br>

#### 7 - Avoid using plaintext passwords inside the host_vars for REMOTE authentication:

When accessing to your hosts through an ansible module or playbook with sudo powers, it will prompt the user to input password for each host. Which its not acceptable, so, we have some options to solve this problem. 
- 1st one is the not recommended one, as i said above using plaintext passwords inside the host_vars for REMOTE authentication is a extremely high security risk. 
- The second one is using ansible-vault to storage and encrypt the user credentials. 
- The third one and the one we are using is disabling password request for sudo users in the remote system. <span style="color: orange;">(RECOMMENDED)</span>

To accomplish that, run this command in every remote host you plan to access with Ansible:
```bash
sudo echo "$USER ALL=(ALL) NOPASSWD=ALL" > /etc/sudoers.d/$USER
```

#### 8 - KNOWN Issues & Bugs:

For some reason having programs or packages like `figlet` or even `neofetch` declared in .bashrc or .zshrc on remote hosts, will break ansible connection, remove them or Ansible wont be able to connect without issues. <span style="color: yellow;">(ATTENTION)</span>

---

<br>

## Usage

In the works.....

<br>

## About the Author  

- Author: Renato Silva 
- Contact: renato@nexusecurus.com
- Year: 2023  


 <br>

---

Give it a try, and join the Ubuntu RAM System revolution adding some of your favorite Ansible Playbooks! 🚀🖥️🤖
