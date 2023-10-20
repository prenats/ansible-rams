# <p align="center">Ubuntu Check Updates RAM Playbook</p> 
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

## <p align="center">Project Description</p>

This Ansible role, named "ubuntu-check-updates," is designed to verify pending updates for Ubuntu-based systems. It checks the APT cache to see which packages are falling behind and need an update. After completion, a list of packages per host is displayed to the user.

---
<br>
<br>

## Table of Contents

- [Ubuntu Check Updates RAM Playbook](#ubuntu-check-updates-ram-playbook)
  - [Project Description](#project-description)
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

Role Name: ubuntu-check-updates

Role Description: Automated check for update packages, with no installation, for Ubuntu-based systems.

Author: Renato Silva

<br>

## Role Tasks

### This role performs the following tasks:

<br>

1. **Update APT Cache**:

   - Updates the APT package cache to ensure that the system has the latest information about available packages.
   - Uses the Ansible apt module to update the cache.
   - The update_cache task ensures that the package information is current.
   - A list of packages is displayed in the console per host.

<br>

## Role Variables

None.

<br>

## Dependencies

- **Ansible** 2.1+ is required for the global use of this repository. _(mandatory)_  
- **Git** is required to clone the repository.  _(mandatory)_  
- **OpenSSH** is required to ensure that the host running Ansible has access to the desired hosts. _(mandatory)_  

<br>

## Requirements

- The target system should be running the Linux Ubuntu distro.

<br>

## Usage

Include this role in your Ansible project's roles directory.
Customize the list of packages to install by editing the defaults/main.yml file.
Create a playbook that uses the role, as shown in the example playbook below inside your `playbooks/` folder.
Run the playbook to check if there are any pending package updates on your Ubuntu-based systems.

<br>

## Example Playbook

Here's an example of how to use this role in an Ansible playbook:

<pre>

---
- name: Check System for Updates
  hosts: all
  become: yes
  roles:
    - ubuntu-check-updates

</pre>

In your playbook, specify the hosts where you want to apply this role, in the example above playbook will be applied to all.

---

## About the Author  

- Author: Renato Silva 
- Contact: renato@nexusecurus.com
- Year: 2023
