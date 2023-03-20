# Ansible Role: vagrant-ansible-init

[![Build](https://github.com/coglinev3/ansible-role-vagrant-ansible-init/actions/workflows/build.yml/badge.svg)](https://github.com/coglinev3/ansible-role-vagrant-ansible-init/actions/workflows/build.yml) ![GitHub tag (latest by date)](https://img.shields.io/github/v/tag/coglinev3/ansible-role-vagrant-ansible-init) [![License](https://img.shields.io/badge/License-BSD%203--Clause-blue.svg)](https://raw.githubusercontent.com/coglinev3/ansible-role-vagrant-ansible-init/master/LICENSE)

The role was developed for initializing
[a Multi-VM Vagrant environment](https://ansible-development.readthedocs.io/),
with one Ansible management node and several Ansible clients (see
[Read the Docs](https://ansible-development.readthedocs.io/) for details about
this environment). Various Ansible settings are made and the SSH host keys of
the client systems are determined and written to the file `/etc/ssh/ssh_known_hosts`.
In addition, the public SSH keys for the user vagrant for the different systems
are determined and written to the directory `/home/vagrant/.ssh` on the Ansible
management node.

After that, the Ansible management node can access the Ansible clients via SSH
with *StrictHostKeyChecking* activated.


## Requirements

[This Multi-VM Vagrant environment for Developing and Testing Ansible Roles](https://ansible-development.readthedocs.io/),
Version 3.0.1 or higher.

## Role Variables

Available variables are listed below, along with default values:

```yml
# Home directory for user vagrant
vagrant_home_directory: /home/vagrant

# Directory for vagrant's individual machine configuration
#
# Attention: This only works if the original vagrant folder whit its
# subdirectory '.vagrant' is synced to virtual machine. For example with the
# following line in the Vagrant file:
# config.vm.synced_folder ".", "/vagrant", type: "virtualbox" 
vagrant_machines_directory: /vagrant/.vagrant/machines/

# default inventory file for Ansible
ansible_inventory_file: /vagrant/provisioning/vagrant.ini
```

## Dependencies

The role can be used with the following operating systems as Ansible management node:
* Alpine 3.14,
* Alpine 3.15,
* Alpine 3.15,
* Alpine 3.17,
* Enterprise Linux 7, 
* Enterprise Linux 8, 
* Enterprise Linux 9, 
* Debian 9 (Stretch),
* Debian 10 (Buster),
* Debian 11 (Bullseye),
* Fedora 35,
* Fedora 36.
* Fedora 37.
* Ubuntu 18.04 LTS (Bionic Beaver),
* Ubuntu 20.04 LTS (Focal Fossa),
* Ubuntu 22.04 LTS (Jammy Jellyfish).

## Example Playbook

```yml
---
# file: test.yml

- name: Example playbook for using role coglinev3.vagrant_ansible_init
  hosts: management-node
  become: true
  roles:
    - { role: coglinev3.vagrant_ansible_init }
```

## Version

Release: 1.4.0

## License

BSD

## Author Information

Copyright &copy; 2023 Cogline.v3.
