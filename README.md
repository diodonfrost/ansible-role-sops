# ansible-role-sops

[![molecule](https://github.com/diodonfrost/ansible-role-sops/workflows/molecule/badge.svg)](https://github.com/diodonfrost/ansible-role-sops/actions)
[![Ansible Galaxy](https://img.shields.io/badge/galaxy-diodonfrost.sops-660198.svg)](https://galaxy.ansible.com/diodonfrost/sops)

This role provide a compliance for install sops on your target host.

## Requirements

None.

## Role Variables

This role has multiple variables. The defaults for all these variables are the following:

```yaml
---
# defaults file for sops

# Define sops version to install
# Default: latest
sops_version: latest

# Define where to download sops package url
# Default: use local system path defined in Ansible vars/*.yml
sops_pkg_url: "{{ default_sops_pkg_url }}"

# Define where to install sops binary
# Default: use local system path defined in Ansible vars/*.yml
sops_bin_directory: "{{ default_sops_bin_directory }}"
```

## Dependencies

None

## Example Playbook

This is a sample playbook file for deploying the Ansible Galaxy sops role in a localhost and installing the latest version of sops.

```yaml
---
- hosts: localhost
  become: true
  roles:
    - role: diodonfrost.sops
```

This role can also install a specific version of sops.

```yaml
---
- hosts: localhost
  become: true
  roles:
    - role: diodonfrost.sops
      vars:
        sops_version: v3.7.3
```

## Local Testing

This project uses [Molecule](http://molecule.readthedocs.io/) to aid in the
development and testing.

To develop or test you'll need to have installed the following:

* Linux (e.g. [Ubuntu](http://www.ubuntu.com/))
* [Docker](https://www.docker.com/)
* [Python](https://www.python.org/) (including python-pip)
* [Ansible](https://www.ansible.com/)
* [Molecule](http://molecule.readthedocs.io/)
* [Libvirt](https://www.virtualbox.org/) (if you test windows system)
* [Vagrant](https://www.vagrantup.com/downloads.html) (if you test windows system)

### Testing with Docker

```shell
# Install requirements
pip install -r requirements-dev.txt

# Test ansible role with ubuntu 22.04
molecule test

# Test ansible role with ubuntu 20.04
image=ansible-ubuntu:20.04 molecule test

# Test ansible role with alpine latest
image=ansible-alpine:latest molecule test

# Create ubuntu 22.04 instance
molecule create

# Apply role on ubuntu 22.04 instance
molecule converge

# Launch tests on ubuntu 22.04 instance
molecule verify
```

### Testing with Vagrant and Libvirt

```shell
# Test ansible role with Windows
molecule test -s windows
```

## License

Apache 2

## Author Information

This role was created in 2023 by diodonfrost.
