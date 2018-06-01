# [Pterodactyl](https://pterodactyl.io/) installer for [Ansible](https://www.ansible.com/)
Ansible playbook for setting up the pterodactyl panel and daemon

## Requirements

* A fresh install of **Ubuntu 16.04**, try it on other distros at your own peril. (needs apt)
* **python** installed for ansible to work

## Generic steps for both types of install

1. Check the `hosts.example` file on the required variables for your ansible hosts file

## Steps For Daemon Install

1. Install your OS
2. Set up ansible on your controller machine and make sure that your server has the required entry in the `/etc/ansible/hosts` file.
3. Run the playbook `ansible-playbook pterodactyldaemon.yml -b -K -l '<HOST or ANSIBLE GROUP>'`
4. Copy the config from your panel to `/srv/daemon/config/core.json` on your new node
5. Run `systemctl start wings`

## Steps For Panel Install

1. Install your OS
2. Set up ansible on your controller machine and make sure that your server has the required entry in the `/etc/ansible/hosts` file.
3. Run the playbook `ansible-playbook pterodactylpanel.yml -b -K -l '<HOST or ANSIBLE GROUP>'`
4. save the passwords that shows in the output logs
5. Configure your email settings with `php artisan p:environment:mail`