# Ansible Role: Docker for ARM

[![Build Status](https://travis-ci.com/geerlingguy/ansible-role-docker_arm.svg?branch=master)](https://travis-ci.com/geerlingguy/ansible-role-docker_arm)

An Ansible Role that installs [Docker](https://www.docker.com) on Linux, specially tailored for ARM-based computers like the Raspberry Pi.

If you need a more flexible and generic role for Docker, check out [`geerlingguy.docker`](https://galaxy.ansible.com/geerlingguy/docker).

## Role Usage in Real-world projects

Besides the documentation here, please see the [Raspberry Pi Dramble](http://www.pidramble.com) for an example of this role in action, being used with multiple Raspberry Pis to build a Kubernetes cluster, or [Drupal Pi](https://github.com/geerlingguy/drupal-pi) for an example of use with a single Raspberry Pi.

## Requirements

If installing Docker Compose, requires Python Pip already be installed (you can use `geerlingguy.pip` to install it).

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    docker_version: 5:19.03.1~3-0~raspbian-buster

The version of Docker to install. Check for available versions with `apt-cache madison docker-ce`.

    docker_install_compose: true

Whether to install Docker Compose via Pip.

    docker_users:
      - user1
      - user2

A list of system users to be added to the `docker` group (so they can use Docker on the server).

    docker_pip_executable: pip

Set this to `pip` for Python 2 and `pip3` for Python 3.

## Use with Ansible (and `docker` Python library)

Many users of this role wish to also use Ansible to then _build_ Docker images and manage Docker containers on the server where Docker is installed. In this case, you can easily add in the `docker` Python library using the `geerlingguy.pip` role:

```yaml
- hosts: rpi

  vars:
    pip_install_packages:
      - name: docker

  roles:
    - geerlingguy.pip
    - geerlingguy.docker_arm
```

## Dependencies

None.

## Example Playbook

```yaml
- hosts: rpi
  roles:
    - geerlingguy.pip
    - geerlingguy.docker_arm
```

## License

MIT / BSD

## Author Information

This role was created in 2019 by [Jeff Geerling](https://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).
