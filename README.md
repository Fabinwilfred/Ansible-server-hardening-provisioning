# Ansible Server Hardening & Provisioning

A comprehensive Ansible project for automating server hardening and provisioning tasks. This repository provides playbooks and roles to secure and configure servers following industry best practices.

## 📋 Table of Contents

- [Overview](#overview)
- [Repository Structure](#repository-structure)
- [Prerequisites](#prerequisites)
- [Quick Start](#quick-start)
- [Project Structure](#project-structure)
- [Configuration](#configuration)
- [Usage](#usage)
- [Requirements](#requirements)
- [Contributing](#contributing)
- [License](#license)

## Overview

This Ansible project automates the hardening and provisioning of servers with a focus on:

- Security hardening best practices
- System configuration and provisioning
- Automated server setup and maintenance
- Reusable playbooks and roles

## Repository Structure

```
.
├── ansible.cfg              # Ansible configuration file
├── requirements.yml         # Ansible collections and dependencies
├── inventories/             # Inventory files for hosts/groups
├── playbooks/               # Main playbooks for orchestration
└── roles/                   # Reusable Ansible roles
```

### Directory Descriptions

- **`ansible.cfg`** - Ansible configuration settings (roles path, defaults, etc.)
- **`requirements.yml`** - Ansible Galaxy requirements for collections
- **`inventories/`** - Host inventory files organized by environment or group
- **`playbooks/`** - Orchestration playbooks that use roles
- **`roles/`** - Individual Ansible roles for specific tasks (hardening, configuration, etc.)

## Prerequisites

Before using this project, ensure you have:

- **Ansible** >= 2.9 installed ([Installation Guide](https://docs.ansible.com/ansible/latest/installation_guide/index.html))
- **Python** >= 3.6 on control node
- **SSH access** to target servers
- Appropriate **permissions** on target systems

## Quick Start

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Fabinwilfred/Ansible-server-hardening-provisioning.git
   cd Ansible-server-hardening-provisioning
   ```

2. **Install dependencies:**
   ```bash
   ansible-galaxy collection install -r requirements.yml
   ```

3. **Update inventory:**
   Edit `inventories/` with your target host information

4. **Run a playbook:**
   ```bash
   ansible-playbook playbooks/your-playbook.yml -i inventories/your-inventory
   ```

## Project Structure

### ansible.cfg

```ini
[defaults]
roles_path = ./roles
```

Configures Ansible to use the local `roles` directory.

### requirements.yml

```yaml
---
collections:
  - name: community.general
  - name: ansible.posix
```

Specifies required Ansible collections:
- **community.general** - General-purpose community modules
- **ansible.posix** - POSIX-specific modules for Linux/Unix systems

## Configuration

### Ansible Configuration

Modify `ansible.cfg` to customize Ansible behavior:

```ini
[defaults]
roles_path = ./roles
host_key_checking = False
inventory = ./inventories/hosts
```

### Inventory Setup

Add your servers to `inventories/` files:

```ini
[webservers]
web1.example.com
web2.example.com

[databases]
db1.example.com
db2.example.com

[all:vars]
ansible_user=admin
ansible_ssh_private_key_file=~/.ssh/id_rsa
```

## Usage

### Running Playbooks

Execute playbooks against your inventory:

```bash
# Run a specific playbook
ansible-playbook playbooks/hardening.yml -i inventories/production

# Run with specific tags
ansible-playbook playbooks/hardening.yml -i inventories/production -t "firewall"

# Run with verbosity
ansible-playbook playbooks/hardening.yml -i inventories/production -vv

# Dry-run mode
ansible-playbook playbooks/hardening.yml -i inventories/production --check
```

### Running Specific Roles

Execute individual roles:

```bash
ansible-playbook -i inventories/hosts -c local -e "target=localhost" playbooks/role-name.yml
```

### Useful Ansible Commands

```bash
# List all hosts in inventory
ansible-inventory -i inventories/hosts --list

# Ping all hosts
ansible all -i inventories/hosts -m ping

# Gather facts about hosts
ansible all -i inventories/hosts -m setup
```

## Requirements

### Collections

The project requires the following Ansible collections (managed by `requirements.yml`):

- **community.general** - Extended modules for various system tasks
- **ansible.posix** - POSIX and Linux-specific functionality

Install with:
```bash
ansible-galaxy collection install -r requirements.yml
```

## Contributing

Contributions are welcome! Please:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/improvement`)
3. Make your changes
4. Test thoroughly
5. Commit with clear messages (`git commit -m 'Add feature'`)
6. Push to your fork (`git push origin feature/improvement`)
7. Open a Pull Request

## Best Practices

- **Test in a non-production environment first** using `--check` mode
- **Use tags** to run specific playbook sections
- **Maintain inventory** files organized by environment
- **Document roles** and their dependencies
- **Keep roles focused** on a single responsibility
- **Version lock** collection dependencies when stable

## License

This project is open source. See LICENSE file for details.

---

**Created by:** Fabinwilfred  
**Repository:** [Ansible-server-hardening-provisioning](https://github.com/Fabinwilfred/Ansible-server-hardening-provisioning)
