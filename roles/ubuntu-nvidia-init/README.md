# <p align="center">Ubuntu NVIDIA Drivers Setup RAM Playbook</p> 
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
    <td><img src="https://img.shields.io/badge/NVIDIA-Supported-green?logo=NVIDIA&logoColor=white"></td>
  </table>
</p>


<br>
<br>
<br>

## <p align="center" > Project Description </p>

This Ansible role, named "ubuntu-nvidia-init," is designed to automate the NVIDIA Driver setup and configuration in Ubuntu-based systems. It ensures that previous drivers are remove prior to installing, and provides a convenient way to display debug output for troubleshooting.

## Table of Contents

- [Ubuntu NVIDIA Drivers Setup RAM Playbook](#ubuntu-nvidia-drivers-setup-ram-playbook)
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

Role Name: ubuntu-nvidia-init

Role Description: Automated NVIDIA Driver setup and package installation for Ubuntu-based systems.

Author: Renato Silva

<br>

## Role Tasks

### This role performs the following tasks:

<br>

1. **Check if NVIDIA driver is installed**:
   - This task checks whether NVIDIA drivers are already installed on the system.
   - It uses the `dpkg` command to check for the presence of NVIDIA driver packages.
   - The result is registered as `nvidia_check`.

<br>

2. **Remove existing NVIDIA driver**:
   - If NVIDIA drivers are detected, this task removes them from the system.
   - It uses the `apt` module to remove any existing NVIDIA driver packages.
   - The task is conditional and only executed if NVIDIA drivers are detected.
   - The result is registered as `remove_nvidia_driver_output`.

<br>

3. **Install NVIDIA Driver 535**:
   - This task installs the NVIDIA driver version 525.
   - It uses the `apt` module to install the specified NVIDIA driver package.
   - The result is registered as `install_nvidia_driver_output`.

<br>

4. **Install CUDA toolkit**:
   - This task installs the NVIDIA CUDA toolkit and development libraries.
   - It uses the `apt` module to install the CUDA toolkit packages.
   - The result is registered as `install_cuda_toolkit_output`.

<br>

5. **Install nvtop**:
   - This task installs the `nvtop` package, a system monitor for NVIDIA GPUs.
   - It uses the `apt` module to install the `nvtop` package.
   - The result is registered as `install_nvtop_output`.

<br>

## Role Variables

nvidia-driver-packages: NVIDIA driver version 535.xx.
cuda_packages: NVIDIA CUDA Toolkit and NVIDIA CUDA Development Packages.
monitor_packages: NVTop package for NVIDIA monitoring.

<br>

## Dependencies

- **Ansible** 2.1+ is required for global use of this repository. _(mandatory)_  
- **Git** is required to clone the repository.  _(mandatory)_  
- **OpensSSH** is required ensure that the host running ansible has access to the desired hosts. _(mandatory)_  

<br>

## Requirements

- The target system should be running Linux Ubuntu distro with a NVIDIA GPU installed.

<br>

## Usage

Include this role in your Ansible project's roles directory.
Customize the list of packages to install by editing the defaults/main.yml file.
Create a playbook that uses the role, as shown in the example playbook below inside your `playbooks/` folder.
Run the playbook to automate the installation setup and package installation of NVIDIA Drivers on your Ubuntu-based systems.

<br>

## Example Playbook

Here's an example of how to use this role in an Ansible playbook:

<pre>

---
- name: Install NVIDIA Driver
  hosts: all
  become: yes
  roles:
    - ubuntu-nvidia-init

</pre>

In your playbook, specify the hosts where you want to apply this role, in the example above playbook will be applied to all.

---

## About the Author  

- Author: Renato Silva 
- Contact: renato@nexusecurus.com
- Year: 2023  2023