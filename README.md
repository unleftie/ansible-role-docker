# Role for Docker setup

[![CI](https://github.com/unleftie/ansible-role-docker/actions/workflows/ci.yml/badge.svg)](https://github.com/unleftie/ansible-role-docker/actions/workflows/ci.yml)

## Compatibility

| Platform   | Version |
| ---------- | ------- |
| debian     | 12      |
| el (rocky) | 9       |
| ubuntu     | 22.04   |

## Dependencies

- [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) (v2.14+)
- [Molecule](https://molecule.readthedocs.io/en/latest/installation.html) + (v4.0.4+) + [docker plugin](https://github.com/ansible-community/molecule-plugins) (for local testing)
- [Docker](https://docs.docker.com/get-docker/) (for local testing)

## Role dependencies

- iptables `required`

## Repository secrets

| Variable  | Description                                            | Value  |
| --------- | ------------------------------------------------------ | ------ |
| GHA_TOKEN | Github Token with public repositories read-only access | string |

## Local Testing

```sh
git clone https://github.com/unleftie/ansible-role-docker.git
cd ansible-role-docker/
molecule test
```

## Installation

> Upgradability notice: When upgrading from old version of this role, be aware that some files may be lost.

To deploy the Docker on hosts, add the Datadog role to your playbook. Below are some sample playbooks to assist you with using the Docker Ansible role.

```yml
- name: Sample 1
  hosts: all
  become: true
  pre_tasks:
    - name: Ensure apt cache are updated
      apt:
        update_cache: true
        cache_valid_time: 3600
      when: ansible_os_family == "Debian"
  tasks:
    - include_role:
        name: "ansible-role-docker"
```

## Variables

| Variable                        | Description                                     | Value                    |
| ------------------------------- | ----------------------------------------------- | ------------------------ |
| `docker_install`                | Whether to install Docker                       | true/false               |
| `docker_ip_pool`                | The list of CIDR ranges used by Docker          |
| `docker_ip_pool_size`           | The CIDR netmask used by Docker                 |
| `docker_root_dir`               | Root directory path                             |
| `docker_install_compose_plugin` | Whether to install Docker Compose plugin        | true/false               |
| `docker_install_compose`        | Whether to install Docker Compose               | true/false               |
| `docker_install_machine`        | Whether to install Docker Machine               | true/false               |
| `docker_force_update`           | Whether to reinstall Docker forcibly            | true/false               |
| `docker_repo_url`               | Docker repository url                           |
| `docker_apt_release_channel`    | Docker apt release channel                      |
| `docker_apt_arch`               | Docker apt architecture                         |
| `docker_apt_ignore_key_error`   | Whether to ignore apt key error                 | true/false               |
| `docker_apt_gpg_key`            | GPG key url for Docker apt repository           |
| `docker_apt_repository`         | Docker apt repository                           |
| `docker_yum_repo_url`           | Docker yum repository url                       |
| `docker_yum_gpg_key`            | GPG key url for Docker yum repository           |
| `docker_compose_version`        | The pinned version of Docker Compose to install | e.g. "v2.10.2", "latest" |
| `docker_compose_arch`           | Docker Compose binary architecture              |
| `docker_compose_path`           | Path to copy Docker Compose binary              |
| `docker_compose_url`            | Docker Compose repository url                   |

## Repositories

| #                     | Default repository                                      |
| --------------------- | ------------------------------------------------------- |
| docker_repo_url       | https://download.docker.com/linux                       |
| docker_compose_url    | https://github.com/docker/compose                       |
| docker_yum_repo_url   | https://download.docker.com/linux/centos/docker-ce.repo |
| docker_apt_repository | https://download.docker.com/linux/debian                |

## 📝 License

This project is licensed under the [MIT](LICENSE).
