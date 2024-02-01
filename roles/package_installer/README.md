# Package Installer Ansible Role

## Overview

The `package_installer` role is designed to automate the installation of packages required by various roles within your infrastructure. It dynamically compiles a list of packages based on enabled roles and manages their installation.

## Requirements

- Ansible 2.9 or higher.
- Managed hosts must have access to package repositories.

## Role Variables

- `package_installer_role_switches`: A dictionary to enable or disable package installations for specific roles.

## Configuration

The role relies on a structured configuration defined in `group_vars/all/package_installer_packages.yml` to list packages associated with each role. Here's a brief overview:

```yaml
package_installer_role_packages:
  alp_workload_ansible:
    - kernel-default
    # Additional packages and roles follow the same pattern.
```

## Example package_installer.yml

The package_installer.yml playbook provides a template for setting up and installing packages on hosts labeled alphost. This playbook allows for fine-grained control over which roles have their associated packages installed:

```yaml
- name: Setup and install packages
  hosts: alphost
  vars:
    package_installer_role_switches:
      alp_workload_ansible: true
      alp_workload_cockpit-ws: false
      alp_workload_neuvector: false
      alp_docker: false
      system_role_ssh: false
      system_role_selinux: false
      system_role_network: false
      system_role_timesync: false
      system_role_systemd: false
      system_role_cockpit_minimal: false
      system_role_cockpit_default: false
      system_role_cockpit_full: false
      system_role_journald: false
      system_role_kernal_settings: false
  roles:
    - package_installer
```
##Author
HVSharma12
