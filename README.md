# [Pterodactyl](https://pterodactyl.io/) installer for [Ansible](https://www.ansible.com/)
Ansible playbook for setting up the pterodactyl panel and Wings

## Requirements

* A fresh install of**Ubuntu 20.04**, **CentOS 7.4+**, or **Debian 9**.
* **python** installed for ansible to work. This playbook will try to install python first.

This playbook is updated to install php 8.1 for Ubuntu 20.04, but is untested.
 
## Generic steps for both types of install

1. Check the `hosts.example` file on the required variables for your ansible hosts file `/etc/ansible/hosts`

## Steps For Full Install

1. Install your OS on both Panel and Daemon servers.
2. Set up ansible on your controller machine and make sure that your server has the required entry in the `/etc/ansible/hosts` file.
3. Run the playbook `ansible-playbook pterodactyl.yml -b -K`
4. Save the passwords that shows in the output logs
5. Configure your email settings with `php artisan p:environment:mail`
6. Copy the config from your panel to `/etc/pterodactyl/config.yml` on your new Wings server
7. Run `systemctl start wings` on your wings server

## Steps For Wings Only Install

1. Install your OS
2. Set up ansible on your controller machine and make sure that your server has the required entry in the `/etc/ansible/hosts` file.
3. Run the playbook `ansible-playbook pterodactyl.yml -b -K -l 'pterodaemon'`
4. Copy the config from your panel to `/etc/pterodactyl/config.yml` on your new Wings server
5. Run `systemctl start wings`

## Steps For Panel Only Install

1. Install your OS
2. Set up ansible on your controller machine and make sure that your server has the required entry in the `/etc/ansible/hosts` file.
3. Run the playbook `ansible-playbook pterodactyl.yml -b -K -l 'pteropanel'`
4. save the passwords that shows in the output logs
5. Configure your email settings with `php artisan p:environment:mail`
