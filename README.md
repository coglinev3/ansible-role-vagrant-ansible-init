# Ansible Role: vagrant-ansible-init

The role was developed for a Vagrant environment, with one management node and several Ansible clients. Among other things, the IP addresses and hostnames of the Ansible clients are entered in the `/etc/hosts` file. The SSH host keys of the client systems are determined and written to the file `/etc/ssh/ssh_known_hosts`. Furthermore, the public SSH keys of the user vagrant are determined for the different systems and stored in the directory `/home/vagrant/.ssh`. on the ansible management node.

Thereafter, the Ansible management node can access the Ansible clients via SSH without turning StrictHostKeyChecking off.

## Requirements

A Vagrant environment with [default shared directory](https://www.vagrantup.com/docs/provisioning/ansible_local.html) on Ansible management node enabled (. → /vagrant).

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

This role has been tested with an Enterprise Linux 7 system as Ansible master.

## Example Playbook

```yml
---
# file: test.yml

- hosts: management-node
  become: true
  roles:
    - { role: vagrant-ansible-init }

```

## Version

Release: x.y.z

## License

BSD

## Author Information

This Ansible Role was created in 2018, by Cogline.v3.
