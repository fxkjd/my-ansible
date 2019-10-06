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

### Logwatch - install and config logwatch 

    $ ansible-playbook -i inventories/my_projects/hosts.ini playbooks/logwatch.yml

### OpenVPN - install and config OpenVPN 

    $ ansible-playbook -i inventories/my_projects/hosts.ini playbooks/openvpn.yml

Configure OpenVPN variables in the OpenVPN section of `group_vars/all.yml` file. 

### Add OpenVPN Clients - Create and download OpenVPN client files 

This playbook needs a list named `clients_to_add`, check `group_vars/add_clients.yml` for an example.

    $ ansible-playbook -i inventories/openvpn/hosts.ini playbooks/add_openvpn_clients.yml -e "@inventories/openvpn/group_vars/add_clients.yml"

The credentials will be in the `fetched_creds/` directory after the playbook finished succesfully. The private key passphrase is stored in the `.txt` file.  
