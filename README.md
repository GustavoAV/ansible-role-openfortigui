# Ansible Role - OpenFortiGUI

Ansible role to setup OpenFortiGUI.

- [Ansible Role - OpenFortiGUI](#ansible-role---openfortigui)
  - [Requirements](#requirements)
  - [Usage](#usage)
  - [Development](#development)
  - [References](#references)

## Requirements

Requirements for using this role:

- Operational system: Debian 11+ or Ubuntu 22+

## Usage

> The `defaults/main.yml` file has all the available parameters and their usage descriptions.

Create a `requirements.yml` file with the content below and install with `ansible-galaxy install -r requirements.yml`.

```yaml
---
roles:
  - name: gustavoav.openfortigui
    src: git+https://github.com/GustavoAV/ansible-role-openfortigui.git
```

Create a playbook (e.g: `setup_openfortigui.yml`) and apply with `ansible-playbook setup_openfortigui.yml`.

```yaml
---
- name: Setup openfortigui
  hosts: all
  vars:
    # Set these with a 16 chars alphanumeric random string
    openfortigui_aes_iv: 16-chars-strings
    openfortigui_aes_key: 16-chars-strings
    # Configure app to start with user login
    openfortigui_autostart: true
  # This MUST not be run entirely as root!
  # become: true
  roles: [gustavoav.openfortigui]
```

## Development

> First, install **docker**.

To setup your development environment, run the commands below.

```bash
# Install UV
curl -LsSf https://astral.sh/uv/install.sh | sh
source ~/.local/bin/env

# Install Ansible tools
uv tool install ansible-dev-tools \
  --with-executables-from=ansible-core,ansible-lint \
  --with-requirements requirements.txt

# Validate
ansible --version
molecule --version
```

And then, to test everything:

```bash
molecule test
```

## References

- [OpenFortiGUI Docs](https://hadler.me/linux/openfortigui/)
