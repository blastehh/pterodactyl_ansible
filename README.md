# pterodactyl_ansible
Ansible playbook for setting up the pterodactyl daemon

## Requirements

* A fresh install of **Ubuntu 16.04**, try it on other distros at your own peril. (needs apt)
* **python** installed for ansible to work

* Your ansible file needs some host variables for the let's encrypt cert
`/etc/ansible/hosts`
```
[pterodactyl]
**<YOUR DOMAIN>** ansible_user=root letsencrypt_email=**<YOUR EMAIL>** domain_name=**<YOUR DOMAIN>**
```

## Steps

1. Install your OS
2. Set up ansible on your controller machine and make sure that your server has the required entry in the `/etc/ansible/hosts` file.
3. Run the playbook `ansible-playbook pterodactyl.yml -b -K -l '**<HOST or ANSIBLE GROUP>**'
4. Copy the config from your panel to `/srv/daemon/config/core.json` on your new node
5. Run `systemctl start wings`