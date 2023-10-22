# <p align="center">Ubuntu SSH Config RAM Playbook</p> 
 <p align="center">powered by Ansible&trade;</p> 

<br>
<br>

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
      <td><img src="https://img.shields.io/badge/YAML-Used-green?logo=yaml"></td>
      <td><img src="https://img.shields.io/badge/Role-System%20Administrator-%23197aaa?logo=linux&logoColor=white"></td>
      <td><img src="https://img.shields.io/badge/Automation-Enabled-brightgreen?logo=robot-framework"></td>
      <td><img src="https://img.shields.io/badge/Ansible-2.10%2B-blue?logo=ansible"></td>
      <td><img src="https://img.shields.io/badge/License-MIT-blue.svg"></td>
    </tr>
    <tr>
      <td><img src="https://img.shields.io/badge/ARM-Architecture-blue"></td>
      <td><img src="https://img.shields.io/badge/Linux-Used-green?logo=linux"></td>
      <td><img src="https://img.shields.io/badge/Markdown-Used-green?logo=markdown"></td>
      <td><img src="https://img.shields.io/badge/Homelab-Geeks-blue"></td>
      <td><img src="https://img.shields.io/badge/Tutorial-Provided-blue"></td>
    </tr>
  </table>
</p>


<br>
<br>
<br>

## <p align="center" > Project Description </p>

This Ansible role, named "ubuntu-ssh-config," is designed to automate the setup and configuration of Ubuntu-based SSH systems. It applies predefined values by the user to the `sshd_config` file, and provides a convenient way to display debug output for troubleshooting.

---
<br>
<br>

## Table of Contents

- [Ubuntu SSH Config RAM Playbook](#ubuntu-ssh-config-ram-playbook)
  - [ Project Description ](#-project-description-)
  - [Table of Contents](#table-of-contents)
  - [Role Details](#role-details)
  - [Role Tasks](#role-tasks)
    - [This role performs the following tasks:](#this-role-performs-the-following-tasks)
  - [Role Variables](#role-variables)
  - [Dependencies](#dependencies)
  - [Requirements](#requirements)
  - [Usage](#usage)
  - [Example Playbook](#example-playbook)
  - [About the Author](#about-the-author)

<br>

---
<br>
<br>

## Role Details

Role Name: ubuntu-ssh-config

Role Description: Automated SSH Config setup for Ubuntu-based systems.

Author: Renato Silva

<br>

## Role Tasks

### This role performs the following tasks:

<br>

1. **Creates a backup**:
   - This task a creates a `/etc/ssh/sshd_config` file inside same folder.
   - It uses the `cp` command for that.

<br>

1. **Change current SSH Values**:
   - Reads the variables value from `defaults/main.yml`.
   - Search for specific string inside `/etc/ssh/sshd_config` and change them based on variables.
   - Notifies handler requesting SSH restart after completion.
<br>

1. **Outputs changes to user console**:
   - This task prints a list of all changes.
   - It uses a register for each SSH setting, and outputs them to the console.

<br>

## Role Variables

ssh_port:  
permit_root_login:  
pubkey_authentication:  
permit_empty_passwords:  
allow_password_login:  
kerberos_authentication:  
gssapi_authentication:  
<br>

## Dependencies

- **Ansible** 2.1+ is required for global use of this repository. _(mandatory)_  
- **Git** is required to clone the repository.  _(mandatory)_  
- **OpensSSH** is required ensure that the host running ansible has access to the desired hosts. _(mandatory)_  

<br>

## Requirements

- The target system should be running Linux Ubuntu distro or Debian based.

<br>

## Usage

Include this role in your Ansible project's roles directory.
Customize the list of packages to install by editing the defaults/main.yml file.
Create a playbook that uses the role, as shown in the example playbook below inside your `playbooks/` folder.
Run the playbook to automate the REMOTE hosts SSH configuration.

<br>

## Example Playbook

ere's an example of how to use this role in an Ansible playbook:

<pre>

---
- name: Configure SSH Connection 
  hosts: all
  become: yes
  roles:
    - ubuntu-ssh-config

</pre>

If you want to be prompted for each variable instead of using the `defaults/main.yml` file, you must add `vars_prompt:` into your playbook file, as below:

<pre>

---
- name: Configure SSH Connection 
  hosts: all
  become: yes
  roles:
    - ubuntu-ssh-config

  vars_prompt:
    - name: ssh_port
      prompt: "Enter SSH Port : "
      private: false
      default: "{{ ssh_port }}"
    - name: permit_root_login
      prompt: "Permit root login:"
      private: false
      default: " {{ permit_root_login }}"

... and so on
</pre>

In your playbook, specify the hosts where you want to apply this role, in the example above playbook will be applied to all.

---

## About the Author  

- Author: Renato Silva 
- Contact: renato@nexusecurus.com
- Year: 2023  