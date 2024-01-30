# Ansible Role: wordpress_mariadb

## Description

This Ansible role is designed to simplify the installation of containerized MariaDB and WordPress on ALP-Dolomite using podman. It streamlines the setup process, ensuring that you have a sample WordPress site up and running quickly.

## Role Variables

You can customize the following variables as per your requirements:

| Variable Name        | Default Value                 | Description                                           |
|----------------------|-------------------------------|-------------------------------------------------------|
| `app_name`           | `wordpress-test-app`         | The name of the WordPress application.                |
| `wordpress_volume`   | `wordpress`                   | The volume for WordPress data.                        |
| `image.wordpress`    | `docker.io/library/wordpress` | The WordPress container image.                        |
| `image.mariadb`      | `registry.opensuse.org/opensuse/mariadb` | The MariaDB container image.          |
| `database.user`      | `wordpress_user`             | The username for the WordPress database.             |
| `database.database`  | `db`                          | The name of the WordPress database.                   |
| `database.password`  | `database_password`           | The password for the WordPress database.              |
| `database.root_password` | `database_root_password`   | The root password for MariaDB.                       |
| `database.host`      | `mariadb`                     | The host where the database is located.              |
| `database.volume`    | `mariadb`                     | The volume for MariaDB data.                         |

## Example Playbook

Here is an example playbook demonstrating how to use this role:

```yaml
- hosts: alphost
  roles:
    - wordpress_mariadb
