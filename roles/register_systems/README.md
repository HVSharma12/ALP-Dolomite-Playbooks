# Ansible Role for SUSE System Registration Management

This Ansible role facilitates the registration and deregistration processes for SUSE Linux Enterprise Micro systems with the SUSE Customer Center or a specified local registration server. It automates the use of the `transactional-update` command to ensure your systems are registered for updates and support, requiring root privileges and the presence of the `transactional-update` utility on the target system.

## Requirements

- **Ansible 2.9+**: Tested with Ansible 2.9 and higher versions.
- **Root Access**: Execution requires root privileges.
- **Transactional Update Utility**: The `transactional-update` must be installed and available on the target system.

## Role Variables

- `suse_registration_code`: Your SUSE registration code.
- `suse_email_address`: Email associated with your SUSE account.
- `suse_registration_server_url`: (Optional) URL of a local registration server.
- `reregister`: Boolean, set to `true` to re-register the system.
- `suse_deregister`: Boolean, set to `true` for system deregistration.

## Tasks Overview

1. **Pre-requisites Verification**: Ensures execution as root and checks for `transactional-update`.
2. **Registration Status**: Checks and sets the current system registration status.
3. **System Registration**: Registers or re-registers the system.
4. **System Deregistration**: Deregisters the system if required.
5. **Conditional Reboot**: Reboots the system if necessary.

## Example Playbook

```yaml
- name: Manage SUSE System Registration
  hosts: all
  become: true
  vars:
    suse_registration_code: 'YOUR_REGISTRATION_CODE_HERE'
    suse_email_address: 'YOUR_EMAIL_ADDRESS_HERE'
    suse_registration_server_url: 'https://suse_register.example.com/'
    reregister: false
    suse_deregister: false
  tasks:
    - name: Include SUSE System Registration Role
      ansible.builtin.include_role:
        name: suse_system_registration
```

## Author Information

This role was originally created by Sebastian Meyer. Enhancements and the addition of the transactional-update functionality were contributed by HVSharma.
