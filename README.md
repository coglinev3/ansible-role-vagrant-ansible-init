# Ansible Role: vagrant-ansible-init

[![Build Status](https://travis-ci.org/coglinev3/vagrant-ansible-init.svg?branch=master)](https://travis-ci.org/coglinev3/vagrant-ansible-init)

The role was developed for initializing
[a Multi-VM Vagrant environment](https://ansible-development.readthedocs.io/),
with one management node and several Ansible clients (see
[Read the Docs](https://ansible-development.readthedocs.io/) for details about
this environment). Different Ansible settings are made and the SSH host keys of
the client systems are determined and written to the file
`/etc/ssh/ssh_known_hosts`. Furthermore, the public SSH keys of the user
vagrant are determined for the different systems and stored in the directory
`/home/vagrant/.ssh`. on the ansible management node.

Thereafter, the Ansible management node can access the Ansible clients via SSH
without turning StrictHostKeyChecking off.

## Requirements

[This Multi-VM Vagrant environment for Developing and Testing Ansible Roles](https://ansible-development.readthedocs.io/), Version 2.0.0 or higher.

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
```

## Dependencies

The role can be used with the following operating systems as Ansible management node:
* CentOS 6
* CentOS 7
* Ubuntu 16.04 LTS (Xenial Xerus)
* Ubuntu 18.04 LTS (Bionic Beaver)
* Ubuntu 18.10 (Cosmic Cuttlefish)
* Ubuntu 19.04 (Disco Dingo)
* Debian 8 (Jessie)
* Debian 9 (Stretch)
* Debian 10 (Buster)


## Example Playbook

```yml
---
# file: test.yml

- hosts: localhost
  become: true
  roles:
    - { role: coglinev3.vagrant-ansible-init }

```

## Version

Release: 1.2.0

## License

BSD

## Author Information

This Ansible Role was created in 2018, by Cogline.v3.
