# <p align="center">Ubuntu Initial Setup RAM Playbook</p> 
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

This Ansible role, named "ubuntu-setup-init," is designed to automate the initial setup and configuration of Ubuntu-based systems. It ensures that the system is updated, installs essential packages, and provides a convenient way to display debug output for troubleshooting.

---
<br>
<br>

## Table of Contents

- [Ubuntu Initial Setup RAM Playbook](#ubuntu-initial-setup-ram-playbook)
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

Role Name: ubuntu-setup-init

Role Description: Automated initial setup and package installation for Ubuntu-based systems.

Author: Renato Silva

<br>

## Role Tasks

### This role performs the following tasks:

<br>

1. **Update APT Cache**:

   - Updates the APT package cache to ensure that the system has the latest information about available packages.
   - Uses the Ansible apt module to update the cache.
   - The update_cache task ensures that the package information is current.  

<br>

2. **Install Additional Packages**:

   - Installs a set of essential packages specified in the role's default variables.
   - Uses the Ansible apt module to install the packages.
   - The list of packages to install is defined in the defaults/main.yml file.  

<br>

3. **Display Debug Output**:

   - Displays debug output for troubleshooting and monitoring.
   - The output includes information about the APT cache update and package installation.
   - The output is helpful for verifying the execution of tasks.  

<br>

## Role Variables

packages: A list of essential packages to install. You can customize this list in the defaults/main.yml file.

<br>

## Dependencies

- **Ansible** 2.1+ is required for global use of this repository. _(mandatory)_  
- **Git** is required to clone the repository.  _(mandatory)_  
- **OpensSSH** is required ensure that the host running ansible has access to the desired hosts. _(mandatory)_  

<br>

## Requirements

- The target system should be running Linux Ubuntu distro.

<br>

## Usage

Include this role in your Ansible project's roles directory.
Customize the list of packages to install by editing the defaults/main.yml file.
Create a playbook that uses the role, as shown in the example playbook below inside your `playbooks/` folder.
Run the playbook to automate the initial setup and package installation on your Ubuntu-based systems.

<br>

## Example Playbook

Here's an example of how to use this role in an Ansible playbook:

<pre>

---
- name: Initialize Ubuntu System
  hosts: all
  become: yes
  roles:
    - ubuntu-setup-init

</pre>

In your playbook, specify the hosts where you want to apply this role, in the example above playbook will be applied to all.

---

## About the Author  

- Author: Renato Silva 
- Contact: renato@nexusecurus.com
- Year: 2023  