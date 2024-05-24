# Passbolt Ansible Role: Quick Setup Guide

## Overview
This Ansible role sets up Passbolt on Ubuntu 20.04 for local testing, handling package installation, MySQL configuration, Passbolt setup, and Nginx configuration.

## Prerequisites
- Ansible installed
- Ubuntu 20.04
- Root or sudo access

## Instructions

### 1. Clone the Repository
Download the Ansible role into your project directory.

### 2. Create Inventory File
Create `inventory.ini`:
```ini
localhost ansible_connection=local

### 3. Create Playbook
Create playbook.yml:

---
- hosts: localhost
  become: yes
  roles:
    - passbolt

### 4. Run the Playbook
Execute with:

ansible-playbook -i inventory.ini playbook.yml

### Customization
Modify variables in defaults/main.yml:

passbolt_db_name: passbolt
passbolt_db_user: passbolt_user
passbolt_db_password: passbolt_password


Override in playbook.yml if needed:

---
- hosts: localhost
  become: yes
  roles:
    - role: passbolt
      passbolt_db_name: custom_db
      passbolt_db_user: custom_user
      passbolt_db_password: custom_password

## Scaling the Setup

### Using Ansible Tower or AWX
For larger deployments on AWS, consider using Ansible Tower or AWX for better management, scheduling, and monitoring of your Ansible playbooks.

1. **Install Ansible Tower or AWX**.
2. **Create an Organization**.
3. **Add Inventory**: Define your AWS instances as inventory in the platform.
4. **Create a Project**: Link your Ansible role repository.
5. **Create a Job Template**: Define a job template to run your playbook.
6. **Run the Job**: Execute the job template to deploy Passbolt on your AWS instances.



Conclusion
Follow these steps to set up the Passbolt Ansible role on Ubuntu 20.04. Adjust configurations as needed.

