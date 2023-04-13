# Ansible role: system

[![CI](https://github.com/vnode/ansible-role-system/actions/workflows/ci.yml/badge.svg)](https://github.com/vnode/ansible-role-system/actions/workflows/ci.yml)

This role provides basic system setup and configuration for OpenBSD systems.

# Requirements

## Operation
No external roles and/or modules are required to use this role.

## Testing & Development
For testing and development, this role depends on the following roles and external tools:
- Vagrant (supporting either the VirtualBox or VMWare provider)
- VagrantCloud (specifically, the `generic/openbsd6` box)


# Role Variables
Available variables are listed below, including their default values (see `defaults/main.yml`).
The defaults take in OS-specific settings.  All of these *should* be implemented. If you find they are not, please [open an issue](https://github.com/vnode/ansible-role-ypclient/issues) in the GitHub repository.


## Required variables

Not applicable.


## Optional variables

To be specified further.

# Dependencies
None.


# Example Playbook
Below is an example to set the hostname to something different from the `inventory_hostname` default and using specific kernel and sysctl settings on an OpenBSD system. Additionally, the example ensures e-mail for the `root` user is forwarded to `reporting@example.com`.

```yaml
---
- hosts: openbsd-box
  roles:
    - role: vnode.system
      vars:
        system_hostname: "testhost.testdomain"
        system_kernel_config: |
          # Disable lm(4) sensor on this OpenBSD system
          disable lm*
        system_reports:
          email: reporting@example.com
        system_sysctl_config:
          net.inet.ip.forwarding: 1
          net.inet6.ip6.forwarding: 1
```


# License
MIT


# Author Information
This role was created in 2020 by [Rogier Krieger](https://vnode.net/).
