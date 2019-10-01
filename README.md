# My Ansible Files

Ansible role and playbooks for installing several things and managing also several things.

## Configuration 

Copy the sample Ansible inventory and variables to edit for your setup. (I will use `my_project` as an example for the rest of this documentation)

    cp -r inventories/sample inventories/my_project

Edit the inventory hosts (`hosts.ini`) to target your desired host. You may also change the configuration variables in (`group_vars/all.yml`).

## First 20 seconds in a server

Basic configuration for a fresh server. Modify the configuration variables in `First Setup` section.

Run the `first_setup` playbook

    $ ansible-playbook --ask-pass -i inventories/my_projects/hosts.ini playbooks/first_setup.yml

This should be the only time that you have to use a password for a server.

## Other playbooks 

Logwatch - install and config logwatch 

    $ ansible-playbook -i inventories/my_projects/hosts.ini playbooks/logwatch.yml
