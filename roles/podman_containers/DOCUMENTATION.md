# Podman Containers Management Role Documentation

This document provides detailed information about the parameters used in the Ansible role for managing Podman containers, networks, pods, and volumes. The role allows for declarative configuration of containerized environments using Podman, facilitating the deployment, management, and scaling of containerized applications.

## Overview

The role comprises several tasks, each responsible for managing a specific aspect of the containerized environment. These tasks include deploying containers, setting up networks, creating and managing pods, and managing volumes for persistent storage. 

Below is a breakdown of the parameters for each task, providing insights into their purpose and usage.

### Containers (`podman_container`)

The `podman_container` task is responsible for managing Podman containers. Here are the parameters used:

- `name`: The name of the container. This is a mandatory parameter.
- `command`: The command to execute when the container starts. Defaults to the command defined in the container image.
- `detach`: Run the container in detached mode. Defaults to `yes`.
- `env`: A dictionary of environment variables to set inside the container.
- `image`: The container image to use.
- `labels`: A dictionary of labels to apply to the container.
- `network`: The network configuration for the container.
- `publish`: A list of ports to publish from the container.
- `restart_policy`: The container's restart policy.
- `state`: The desired state of the container. Default is `started`.
- `volume`: A list of volumes to mount inside the container.
- `cap_add`, `cap_drop`: Capabilities to add or drop from the container.
- `cpu_shares`, `cpus`: CPU-related settings for the container.
- `dns`: A list of DNS servers for the container.
- `healthcheck`: Healthcheck parameters for the container, such as `interval`, `timeout`, `start_period`, and `retries`.
- `hostname`: The hostname to set for the container.
- `init`: Whether to run an init inside the container. Defaults to `no`.
- `memory`: The amount of memory the container is allowed to use.
- `pod`: The name of the pod to associate the container with.
- `privileged`: Whether to run the container in privileged mode.
- `read_only`: Whether the container's root filesystem should be mounted as read-only.
- `rm`: Automatically remove the container when it exits.
- `security_opt`, `sysctl`, `tmpfs`, `shm_size`: Various security and system options.
- `cpu_quota`, `cpu_period`, `cpuset_cpus`, `cpuset_mems`: CPU and memory allocation settings.
- `network_aliases`: Network aliases for the container.

### Networks (`podman_network`)

The `podman_network` task manages Podman networks.

- `name`: The name of the network. Required.
- `debug`: Enable debug mode for network commands.
- `disable_dns`: Disable DNS within the network.
- `driver`: The network driver to use. Defaults to `bridge`.
- `gateway`, `ip_range`, `subnet`: Networking details.
- `ipv6`: Enable IPv6.
- `macvlan`: MACVLAN settings.
- `opt`, `metric`, `mode`, `mtu`, `parent`, `vlan`: Various network options.
- `recreate`: Whether to recreate the network if it already exists.
- `state`: The desired state of the network. Default is `present`.

### Pods (`podman_pod`)

The `podman_pod` task handles Podman pods.

- `name`: The name of the pod. Required.
- `state`: The desired state of the pod. Default is `started`.
- `publish`: Ports to publish from the pod.
- `hostname`: The hostname for the pod.
- `infra`: Whether to create an infra container for the pod. Defaults to `true`.
- `network`: Network configuration for the pod.
- `ports`, `share`, `volume`: Additional pod settings.
- `debug`: Enable debug mode.
- `recreate`: Whether to recreate the pod if it exists.

### Volumes (`podman_volume`)

The `podman_volume` task manages Podman volumes.

- `name`: The name of the volume. Required.
- `driver`: The volume driver. Defaults to `local`.
- `label`, `options`: Labels and options for the volume.
- `recreate`: Whether to recreate the volume if it exists.
- `state`: The desired state of the volume. Default is `present`.
- `debug`: Enable debug mode for volume commands.

## Example Usage

Refer to the example playbook in the `README.md` file for a practical implementation of these parameters. The example illustrates how to deploy a WordPress site with a MariaDB database using Podman containers.

## Additional Notes

- When using these parameters, ensure that you provide values that match your deployment and security requirements.
- For `healthcheck` and other complex parameters, refer to the Podman documentation for detailed usage patterns.

This documentation aims to provide a clear understanding of each parameter's role and usage within the Ansible tasks. For further customization and advanced configurations, consult the Podman and Ansible documentation.
