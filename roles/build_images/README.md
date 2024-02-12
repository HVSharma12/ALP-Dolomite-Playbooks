# Ansible Role: build_images

This Ansible role performs tasks to build container images using Podman. It includes steps to retrieve a Git image, create a temporary location, run Git checkout in a Podman container, build a new container image from the checked-out code, and clean up temporary files.

## Requirements

- Ansible 2.9 or higher.
- Podman installed on the host where the role is executed.

## Role Variables

This role requires the definition of the following variables, typically set in the playbook under the `vars` section or in separate variables files:

```yaml
git_image: "registry.suse.com/suse/git:latest" # The image used for Git operations, default:registry.suse.com/suse/git:latest
application_name: "" # The name of the application or container image to build
application_repo: "" # URL of the Git repository containing the application source code
application_branch: "" # The branch of the Git repository to checkout
application_version: "" # The tag/version of the container image to build
```
## Example Playbook

Below is an example playbook using the build_images role:

```yaml

- hosts: servers
  roles:
    - role: build_images
      vars:
        git_image: "registry.suse.com/suse/git:latest"
        application_name: "my_application"
        application_repo: "https://github.com/example/my_application.git"
        application_branch: "main"
        application_version: "1.0.0"
```

## Author

Harshvardhan Sharma
