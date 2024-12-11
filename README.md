# Ansible Configuration Management Project

This repository contains Ansible playbooks and roles to automate essential configuration management tasks across a fleet of servers. The project is designed to demonstrate the use of Ansible for managing web servers, databases, user accounts, compliance, logging, and backups.

---

## Features

### 1. Web Server Configuration
- Automates the setup of a LAMP/LEMP stack (Linux, Apache/Nginx, MySQL, PHP).
- Configures secure settings such as disabling unused ports and enforcing HTTPS.

### 2. Database Configuration
- Automates installation and configuration of MySQL.
- Manages secure user creation, permissions.

### 3. User and Permission Management
- Creates user accounts and passwordless authentication using SSH.
- Enforces password policies and inactivity timeouts.

### 4. Compliance Automation
- Ensures server compliance with CIS benchmarks.
- Tasks include disabling root SSH login, updating software, and enforcing firewall rules.

### 5. Centralized Logging Configuration
- Configures rsyslog to send logs to a centralized logging server.
  

### 6. Backup and Restore Configuration
- Automates database backups and transfers them to a remote server.
- Deletes local backup copies post-transfer.

---

## Project Structure

```plaintext
---
├── inventory/                # Inventory files for defining hosts and groups
│   └── hosts.ini             # Static inventory file
│  
├── roles/                    # Individual Ansible roles
|   ├── Firewall              # Role for ufw configuration ( internal firewall )
│   ├── web_server            # Role for web server configuration
│   ├── database_server       # Role for database configuration
│   ├── user_management       # Role for user and permission management
│   ├── compliance            # Role for compliance automation
│   ├── logging               # Role for centralized logging
│   └── backup                # Role for database backup
|
├── playbooks/                # Orchestration playbooks
│   |── main.yml              # Main playbook to orchestrate all roles
|   └── backup_transfer.yaml  # Playbook to transfer database backup
|
└── README.md                 # Project documentation
```

---

## Getting Started

### Prerequisites
- Ansible installed on the control node.
- Python 3 installed on all managed nodes.
- SSH access to managed nodes.

### Setup

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/SivaSankarMG/Ansible.git
   cd Ansible
   ```

2. **Define Inventory:**
   Update `inventory/hosts.ini`.

3. **Set Variables:**
   Update variables to match your environment.

---

## Usage

- Test connectivity to hosts:
  ```bash
  ansible -i inventory/hosts.ini all -m ping
  ```

- Use `ansible-playbook` to run the playbook:
  ```bash
  ansible-playbook -i inventory/hosts.ini playbooks/main.yml
  ```
---

## Security
- Sensitive credentials are managed using Ansible Vault.
- Ensure firewall rules are appropriately configured.

---

## Contributing
Contributions are welcome! Please open an issue or submit a pull request for any improvements or additional features.

---
