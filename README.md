# ALP-Dolomite-Playbooks

This repository contains a collection of Ansible playbooks and roles for configuring ALP-Dolomite systems. These playbooks are designed to automate various tasks and configurations on ALP-Dolomite environments.

## Playbooks

Here is a list of available playbooks:

| Playbook Name                   | Description                                          |
|---------------------------------|------------------------------------------------------|
| `install_docker.yml`            | Install Docker on ALP-Dolomite.                     |
| `setup_firewalld.yml`           | Set up the Firewalld service.                       |
| `setup_kea_dhcp_server.yml`     | Configure and deploy Kea DHCP Server.               |
| `setup_keylime.yml`             | Setup Keylime for ALP-Dolomite.                    |
| `setup_cockpit.yml`             | Install and configure Cockpit.                      |
| `setup_grafana.yml`             | Configure and deploy Grafana.                       |
| `setup_kea_dhcpv6_server.yml`   | Configure and deploy Kea DHCPv6 Server.            |
| `setup_neuvector.yml`           | Setup NeuVector for ALP-Dolomite.                  |

## Roles

Here are the Ansible roles included in this repository:

| Role Name                      | Description                                          |
|---------------------------------|------------------------------------------------------|
| `wordpress_mariadb`            | This role simplifies the installation and configuration of containerized MariaDB and WordPress on ALP-Dolomite using podman. |

## Usage

It is recommended to use an Ansible Core >= 2.13, which corresponds to version 6 or later of the Ansible meta package.

