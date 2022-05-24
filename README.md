# Ansible role: PHP

![.github/workflows/molecule.yml](https://github.com/AcroMedia/ansible-role-php/workflows/.github/workflows/molecule.yml/badge.svg)

Install and configure PHP, typically for use with Drupal sites in Acro Media NGINX + FPM hosting environments.



## Requirements

* Ubuntu LTS (18.04 or newer)

## Role Variables

* php_default_version: The default CLI version of php for the server
* php_memory_limit: The maximum memory limit
* php_max_input_vars: The maximum input vars
* php_versions: A list of versions to install
* phpXX_add_modules: A list of extra apt packages not already included in the [default list](./defaults/main.yml), where XX corresponds to the PHP version(s) you're installing.

## Dependencies

None

## Example Playbook
```yaml
- name: Install + Configure PHP
  hosts: servers
  gather_facts: yes
  become: yes
  vars:
    php_default_version: 8.0
    php_versions:
      - 7.2
      - 7.3
      - 8.0
    php74_add_modules:
      - php8.0-extra-thingy
  roles:
    - role: acromedia.php
      tags:
        - php
```

## License

GPLv3

## Author Information

Acro Media Inc.
https://www.acromedia.com/
