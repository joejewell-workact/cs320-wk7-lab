# CS320 Week 7: Multi-Distribution WordPress Deployment

This project uses Ansible to deploy a complete WordPress site on a LEMP stack
(Linux, NGINX, MariaDB, PHP) from one main playbook that works on both
Debian-based and Red Hat-based systems. It was built from the Chapter 5 project.
Idempotence is checked with a second site.yml run (see Testing).

## Supported distros
- alma
- ubuntu

## The project consists of

- site.yml
- validate.yml
- roles/stack_install
- roles/stack_config
- roles/wordpress
- group_vars/wordpress_servers/vars.yml
- group_vars/wordpress_servers/vault.yml
- requirements.yml

## Required software

- Python 3
- Ansible (ansible-core plus the collections in requirements.yml:
  ansible.mariadb, ansible.posix, community.general)

## How to run

ansible wordpress_servers -m ansible.builtin.ping

ansible-playbook site.yml --syntax-check

ansible-playbook site.yml

ansible-playbook site.yml

ansible-playbook validate.yml


Then browse to https://10.2.37.98 and https://10.2.37.99 and log in at https://10.2.37.x/wp-admin as wpadmin.


## Testing

Deploy 2 times and ensure wordpress is running on both hosts
