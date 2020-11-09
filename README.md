# Ansible role: PHP

Install and configure PHP, typically for use with Drupal sites in Acro Media NGINX + FPM hosting environments.

## Requirements

* Ubuntu LTS (16.04 or newer)

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
    php_default_version: 7.4
    php_versions:
      - 7.2
      - 7.3
      - 7.4
    php74_add_modules:
      - php7.4-extra-thingy
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
