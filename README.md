
## Prerequisites

- **Ansible** >= 2.14 installed ([Installation Guide](https://docs.ansible.com/ansible/latest/installation_guide/index.html))
- **Python** >= 3.6 on the control node
- **SSH access** to target servers
- **Sudo/become access** on target systems

## Quick Start

1. **Clone the repository:**
```bash
   git clone https://github.com/Fabinwilfred/Ansible-server-hardening-provisioning.git
   cd Ansible-server-hardening-provisioning
```

2. **Install required collections:**
```bash
   ansible-galaxy collection install -r requirements.yml
```

3. **Point the inventory at your own host(s):**
   Edit `inventories/production/hosts.yml` (or create your own inventory file) with your target host information.

4. **Run the playbook:**
```bash
   ansible-playbook -i inventories/production/hosts.yml playbooks/site.yml --ask-become-pass
```

   Add `--check --diff` first if you want a dry run before applying anything for real.

## Configuration

`ansible.cfg` currently sets:

```ini
[defaults]
roles_path = ./roles
```

Variables that control role behavior (timezone, `ssh_port`, allowed SSH users, firewall policy, etc.) live in `inventories/production/group_vars/all.yml` and each role's own `defaults/main.yml` — override them per-environment via inventory `group_vars`/`host_vars` rather than editing role defaults directly.

## Vault-Backed Secrets

The `users` role supports loading real credentials and SSH keys from an `ansible-vault`-encrypted file instead of the generic example in `defaults/main.yml`. To set one up:

```bash
ansible-vault create roles/users/vars/vault.yml
```

Enter content matching the variable names the role expects:

```yaml
---
users:
  - name: youruser
    groups: []
    sudo: true
    # omit "password" entirely for SSH-key-only accounts

user_ssh_keys:
  youruser: "ssh-ed25519 AAAA... your-public-key"
```

Then add `--ask-vault-pass` to your `ansible-playbook` command. The role falls back safely to the generic `deployer` example in `defaults/main.yml` if no vault file is present.

## Usage

```bash
# Full run
ansible-playbook -i inventories/production/hosts.yml playbooks/site.yml --ask-become-pass

# Dry run (no changes applied)
ansible-playbook -i inventories/production/hosts.yml playbooks/site.yml --check --diff --ask-become-pass

# Run against one host only
ansible-playbook -i inventories/production/hosts.yml playbooks/site.yml --limit your-host --ask-become-pass

# Run a subset of roles by tag (currently: audit)
ansible-playbook -i inventories/production/hosts.yml playbooks/site.yml --tags audit --ask-become-pass

# With vault-backed user credentials
ansible-playbook -i inventories/production/hosts.yml playbooks/site.yml --ask-become-pass --ask-vault-pass
```

### Useful Ansible Commands

```bash
# Check syntax without running anything
ansible-playbook -i inventories/production/hosts.yml playbooks/site.yml --syntax-check

# Ping all hosts
ansible all -i inventories/production/hosts.yml -m ping

# List all hosts in inventory
ansible-inventory -i inventories/production/hosts.yml --list
```

## Requirements

Collections required (managed by `requirements.yml`, installed via `ansible-galaxy collection install -r requirements.yml`):

- **community.general** — UFW and other extended modules
- **ansible.posix** — `authorized_key` and other POSIX-specific modules

## Contributing

Contributions are welcome:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/improvement`)
3. Make your changes
4. Test with `--check --diff` before a real run
5. Commit with clear messages
6. Open a Pull Request

## Best Practices

- Test in a non-production environment first, using `--check --diff`
- Use `--limit` to target a single host while testing
- Keep real secrets in `ansible-vault`, never in plaintext defaults
- Keep roles focused on a single responsibility

## License

This project is open source. See LICENSE file for details.

---

**Created by:** Fabin Wilfred
**Repository:** [Ansible-server-hardening-provisioning](https://github.com/Fabinwilfred/Ansible-server-hardening-provisioning)
READMEEOF
