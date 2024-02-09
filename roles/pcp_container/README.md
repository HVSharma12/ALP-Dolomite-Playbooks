# pcp-container Ansible Role

The `pcp-container` role is designed to deploy Performance Co-Pilot (PCP) containers for collecting and monitoring system performance metrics across your infrastructure. It supports conditional deployment of different configurations based on the requirement for monitoring, and manages PCP containers for metrics collection or remote system control.

## Requirements

- **Ansible 2.9 or higher**: The role has been tested with Ansible versions 2.9 and above.
- **Podman**: Podman must be installed on the target hosts where the containers will be deployed.
- **PCP Image**: Access to the PCP container image, by default `registry.suse.com/suse/pcp:latest`, is required.

## Role Variables

Variables allow customization of the PCP deployment according to your needs. Default values are set in `defaults/main.yml`.

```yaml
pcp_image: "registry.suse.com/suse/pcp:latest"  # Default PCP container image
pcp_container_name: "metrics_collector"        # Base name for the PCP containers
pcp_archives_dir: /root/pcp-archives            # Directory for storing PCP logs and configurations
generate_systemd: false                        # Whether to generate systemd units for the containers
monitoring_system: false                       # Toggle for enabling monitoring system deployment it will install the client container by default
pcp_clients: []                                # List of clients for configuration
```

## Example Playbook

The following example playbook demonstrates how to apply the pcp-container role to all hosts, enabling the monitoring system and specifying clients for monitoring.

```yaml

- name: Apply pcp-container role to hosts
  hosts: all
  become: true
  vars:
    monitoring_system: true #Set to false to deploy client container
    generate_systemd: false
    pcp_clients:
      - CLIENT_HOSTNAME
      - CLIENT_HOSTNAME
  roles:
    - role: pcp_container
```

## Role Tasks Overview
Main Tasks

    Monitoring System Inclusion: Includes tasks from monitoring_system.yml for each specified client if monitoring_system is set to true.
    Control Client Inclusion: Includes tasks from control_client.yml if monitoring_system is not true.

## Monitoring System Tasks

Tasks in monitoring_system.yml set up directories and configuration files for each client, manage the deployment of PCP containers with custom configurations, and handle systemd units if generate_systemd is enabled.

## Author
Harshvardhan Sharma
