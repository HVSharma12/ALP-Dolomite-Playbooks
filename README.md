# ALP-Dolomite-Playbooks

This repository contains a collection of Ansible playbooks and roles for configuring ALP-Dolomite systems. These playbooks are designed to automate various tasks and configurations on ALP-Dolomite environments.

## Playbooks

Here is a list of available playbooks:

| Playbook Name                   | Description                                          |
|---------------------------------|------------------------------------------------------|
| `setup_docker.yml`         | Playbook installing docker                                |

## Roles

Here are the Ansible roles included in this repository:

| Role Name                      | Description                                          |
|---------------------------------|------------------------------------------------------|
| `wordpress_mariadb`            | This role simplifies the installation of containerized MariaDB and WordPress using podman. |
| `register_systems`            | This Ansible role facilitates the registration and deregistration processes for SUSE Linux Enterprise Micro systems |
| `podman_containers`            | This role manages the entire lifecycle of Podman containers and their dependencies, such as networks, volumes, and pods. |
| `setup_alp_workloads`          | This role installs containerized ALP workloads         |
| `pcp_container`                | The `pcp-container` role is designed to deploy Performance Co-Pilot (PCP) containers |

## Usage

It is recommended to use an Ansible Core >= 2.13, which corresponds to version 6 or later of the Ansible meta package.
