# Install ALP Workloads Ansible Role

## Overview

This Ansible role facilitates the installation of various ALP workload containers. It ensures the necessary infrastructure is in place and manages container images effectively.

## Requirements

- Ansible 2.9 or higher.
- Podman installed on the target machine.
- Access to a container registry where ALP workload images are stored.

## Role Variables

- `workloads_list`: A dictionary containing a list of workloads to be managed. Each workload specifies the container name, registry, path, version, and labels for install and uninstall operations.

## Default Workloads Configuration

The role comes pre-configured with a list of default workloads in the `group_vars/all/defaults` file. Users can customize this list as needed for their specific requirements. Here's a brief overview of the default configuration:

```yaml
workloads_list:
  workloads:
    - name: ansible
      container:
        name: ansible
        registry: registry.opensuse.org
        path: suse/alp/workloads/tumbleweed_containerfiles/suse/alp/workloads
        version: latest
      labels:
        install: install
        uninstall: uninstall
```
Additional workloads are defined similarly.

## Basic Usage

To use this role, you will typically run the install_alp_workloads.yml Ansible playbook, which includes this role and specifies any necessary variables or overrides.

## Authors
- Original Author: rtamalin
- Modifications by: HVSharma12
