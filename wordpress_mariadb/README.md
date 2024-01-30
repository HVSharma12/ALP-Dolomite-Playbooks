Ansible Role: wordpress_mariadb
Description

This Ansible role is designed to simplify the installation and configuration of containerised MariaDB, and WordPress on ALP-Dolomite using podman. It streamlines the setup process, ensuring that you have a sample WordPress site up and running quickly.

Role Variables

The following variables can be customized as per your requirements:

    db_name 
        Inform the name of the WordPress database.

    db_user 
        Inform the username for the WordPress database.

    root_login 
        Specify the root user for MariaDB.

    root_password 
        Set the root password for MariaDB.

    db_host 
        Specify the database host.

Example Playbook

Here is an example playbook demonstrating how to use this role:

yaml

- hosts: alphost
  roles:
    - role: /path/mariadb_apache_wordpress

Contributing

We welcome contributions, bug reports, feature requests, and ideas. Please feel free to create issues in the Issues section of this repository.
