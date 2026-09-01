# Ansible Role for Docker setup

[![CI](https://github.com/unleftie/ansible-role-docker/actions/workflows/ci.yml/badge.svg)](https://github.com/unleftie/ansible-role-docker/actions/workflows/ci.yml)
[![OpenSSF Scorecard](https://api.securityscorecards.dev/projects/github.com/unleftie/ansible-role-docker/badge)](https://securityscorecards.dev/viewer/?uri=github.com/unleftie/ansible-role-docker)

Thin wrapper role that applies the upstream [`geerlingguy.docker`](https://github.com/geerlingguy/ansible-role-docker) role.
Override variables live in [vars/main.yml](vars/main.yml)

## Compatibility

| Platform | Version |
| -------- | ------- |
| ubuntu   | 26.04   |

## Dependencies

- [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) (v2.14+)
- [Molecule](https://molecule.readthedocs.io/en/latest/installation.html) + (v4.0.4+) + [docker plugin](https://github.com/ansible-community/molecule-plugins) (for local testing)
- [Docker](https://docs.docker.com/get-docker/) (for local testing)

## Role dependencies

- iptables `required`

## Local Testing

```sh
git clone https://github.com/unleftie/ansible-role-docker.git
cd ansible-role-docker
ansible-galaxy install -r requirements.yml
molecule test
```

## Installation

```sh
ansible-galaxy install -r requirements.yml
```

Example [playbook](main.yml)

## 📝 License

This project is licensed under the [MIT](LICENSE).
