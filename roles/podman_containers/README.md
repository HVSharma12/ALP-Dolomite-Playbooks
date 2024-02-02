# Ansible Role for Podman Containers Management

This Ansible role is designed to manage the entire lifecycle of Podman containers and their dependencies, such as networks, volumes, and pods. It allows for a declarative approach to configuring containerized environments using Ansible, making it easier to deploy, update, and maintain applications and their infrastructure.

## Requirements

- **Ansible 2.9+**: This role is tested with Ansible 2.9 and above.
- **Podman**: The target systems must have Podman installed. This role does not handle the Podman installation, so you must ensure Podman is set up before using this role.

## Role Variables

This role utilizes a range of variables to define the desired state of Podman entities. These variables are split across four categories: networks, volumes, pods, and containers. You can set these variables within your playbook under the `vars` section or within the role's `defaults/main.yml` file if you prefer to have default values.

### Networks (`podman_networks`)

Defines the Podman networks to be managed. Each item in this list can include properties like `name`, `driver`, `subnet`, etc.

- `name`: The name of the network.
- `driver`: Specifies the network's driver, typically `bridge`.
- `subnet`, `gateway`, `ip_range`: Networking details for custom network configurations.
- `ipv6`: Enable IPv6 networking (boolean).
- Other network-specific settings as required.

### Volumes (`podman_volumes`)

Manages volumes for persistent data storage. Items can include `name`, `driver`, and `options`.

- `name`: The volume name.
- `driver`: The storage driver for the volume, usually `local`.
- `options`: Additional driver options.

### Pods (`podman_pods`)

Defines the pods to manage, facilitating multi-container deployments.

- `name`: The pod name.
- `publish`: Ports to publish from the pod.
- `network`: Network configuration for the pod.
- Other pod-specific settings as needed.

### Containers (`podman_containers`)

Specifies the containers to deploy and manage, including their image, environment variables, volumes, and more.

- `name`: The container name.
- `image`: The container image to use.
- `env`: Environment variables for the container.
- `volume`: Volumes to mount into the container.
- Detailed container-specific settings like `cpu_shares`, `memory`, `restart_policy`, etc.

## Detailed Parameter Documentation

For a detailed explanation of all the parameters used in this role, please refer to the [`DOCUMENTATION.md`](./DOCUMENTATION.md) file in this repository. This document provides an in-depth look at each parameter, including its purpose, expected values, and usage examples. It is essential reading for anyone looking to customize this role to fit their specific requirements.

## Example Playbook

The following playbook demonstrates how to use this role to deploy a WordPress application with a MariaDB database, using Podman for containerization. 

```yaml
- name: Deploy Podman Networks and Containers
  hosts: your_target_host
  become: true
  vars:
    podman_networks:
      - name: wordpress_network
        driver: bridge
    podman_volumes:
      - name: wordpress_data_volume
      - name: mariadb_data_volume
    podman_pods:
      - name: wordpress-test-app
        publish:
          - "8080:80"
        network: "wordpress_network"
        infra: true
    podman_containers:
      - name: mariadb
        image: "registry.opensuse.org/opensuse/mariadb:latest"
        volumes:
          - "mariadb_data_volume:/var/lib/mysql:Z"
        env:
          MYSQL_USER: "wordpress_user"
          MYSQL_PASSWORD: "wordpress_password"
          MYSQL_DATABASE: "wordpress_db"
          MYSQL_ROOT_PASSWORD: "mariadb_root_password"
        restart_policy: "always"
        pod: "wordpress-test-app"
      - name: wordpress
        image: "docker.io/library/wordpress:latest"
        volumes:
          - "wordpress_data_volume:/var/www/html"
        env:
          WORDPRESS_DB_USER: "wordpress_user"
          WORDPRESS_DB_PASSWORD: "wordpress_password"
          WORDPRESS_DB_NAME: "wordpress_db"
          WORDPRESS_DB_HOST: "mariadb"
        restart_policy: "always"
        pod: "wordpress-test-app"

  tasks:
    - name: Include the role
      ansible.builtin.include_role:
        name: podman_containers
```

## Usage

- Prepare your environment: Ensure Podman is installed on your target systems.
- Define your playbook: Use the example above as a template. Adjust the variables to match your specific deployment requirements.
- Execute the playbook: Run your playbook using ansible-playbook, pointing to your inventory.

## Authors

HVSharma
