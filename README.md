<div align="center">

### NYX™ · INFRASTRUCTURE AUTOMATION

<sub>BUILD · AUTOMATE · DEPLOY</sub>

</div>

---

### ABOUT

Infrastructure automation for **NYX**, a persistent, multi-planet
**Star Wars RP** project powered by **nanos world** and **Unreal Engine 5**.

This repository contains the Ansible configuration used to prepare
the infrastructure, starting with a single-server laboratory.

### TOOLS & TECHNOLOGIES

<p align="center"><sub><b>CURRENT FOUNDATION</b></sub></p>
<p align="center">
  <img src="https://skillicons.dev/icons?i=linux&amp;theme=dark" width="48" height="48" title="Linux" alt="Linux" />
  <img src="https://skillicons.dev/icons?i=ansible&amp;theme=dark" width="48" height="48" title="Ansible" alt="Ansible" />
  <img src="https://skillicons.dev/icons?i=git&amp;theme=dark" width="48" height="48" title="Git" alt="Git" />
</p>

### IMPLEMENTED

- Local Ansible inventory targeting the laboratory host.
- Reusable `nyx_filesystem` role with configurable defaults.
- Directory management with explicit ownership and permissions.
- Missing-directory recreation and idempotence verified.

| Path | Purpose | Ownership | Permissions |
|---|---|---|---|
| `/etc/nyx` | NYX configuration | `root:root` | `0750` |
| `/etc/nyx/compose` | Future deployed Compose definitions | `root:root` | `0750` |
| `/var/lib/nyx` | Future NYX-managed persistent data | `root:root` | `0750` |

### REPOSITORY STRUCTURE

| Path | Responsibility |
|---|---|
| `ansible.cfg` | Inventory and role search paths |
| `ansible/inventory.yml` | Managed hosts and connection settings |
| `ansible/playbooks/filesystem.yml` | Filesystem preparation playbook |
| `ansible/roles/nyx_filesystem/defaults/main.yml` | Default role parameters |
| `ansible/roles/nyx_filesystem/tasks/main.yml` | Directory management tasks |

### USAGE

Run from the repository root, on the laboratory host.
The current inventory uses a local connection.

Check syntax:

```bash
ansible-playbook ansible/playbooks/filesystem.yml --syntax-check
```

Preview changes:

```bash
ansible-playbook ansible/playbooks/filesystem.yml --check --diff -K
```

Apply the configuration:

```bash
ansible-playbook ansible/playbooks/filesystem.yml -K
```

Run again to verify idempotence. When the managed state is already
correct, the recap should report `changed=0` and no failures.

### ROADMAP

- [x] Ansible filesystem role
- [x] Directory permissions and idempotence validation
- [ ] Repository quality checks and CI
- [ ] Host security and Docker
- [ ] Secrets management
- [ ] Web and game services
- [ ] Monitoring, backups and recovery

---

### COPYRIGHT

Copyright © 2026 NYX. All rights reserved.

No license is granted for use, modification, or redistribution,
except as permitted by applicable law or GitHub’s Terms of Service.
For permission requests, please contact the author.
