# [Pterodactyl](https://pterodactyl.io/) installer for [Ansible](https://www.ansible.com/)
Ansible playbook for setting up the pterodactyl panel and daemon

## Requirements

* A fresh install of **Ubuntu 16.04** or **CentOS 7.4**, might also work with Debian, but untested.
* **python** installed for ansible to work

## Generic steps for both types of install

1. Check the `hosts.example` file on the required variables for your ansible hosts file `/etc/ansible/hosts`

## Steps For Full Install

1. Install your OS on both Panel and Daemon servers.
2. Set up ansible on your controller machine and make sure that your server has the required entry in the `/etc/ansible/hosts` file.
3. Run the playbook `ansible-playbook pterodactyl.yml -b -K`
4. Save the passwords that shows in the output logs
5. Configure your email settings with `php artisan p:environment:mail`
6. Copy the config from your panel to `/srv/daemon/config/core.json` on your new daemon server
7. Run `systemctl start wings` on your daemon server

## Steps For Daemon Only Install

1. Install your OS
2. Set up ansible on your controller machine and make sure that your server has the required entry in the `/etc/ansible/hosts` file.
3. Run the playbook `ansible-playbook pterodactyl.yml -b -K -l 'pterodaemon'`
4. Copy the config from your panel to `/srv/daemon/config/core.json` on your new daemon server
5. Run `systemctl start wings`

## Steps For Panel Only Install

1. Install your OS
2. Set up ansible on your controller machine and make sure that your server has the required entry in the `/etc/ansible/hosts` file.
3. Run the playbook `ansible-playbook pterodactyl.yml -b -K -l 'pteropanel'`
4. save the passwords that shows in the output logs
5. Configure your email settings with `php artisan p:environment:mail`