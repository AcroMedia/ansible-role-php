# Ansible role: PHP

![.github/workflows/molecule.yml](https://github.com/AcroMedia/ansible-role-php/workflows/.github/workflows/molecule.yml/badge.svg)

Install and configure PHP, typically for use with Drupal sites in Acro Media NGINX + FPM hosting environments.


## Requirements

* Ubuntu LTS (18.04 or newer)


## Role Variables

#### `php_default_version`
  * The default CLI version of php to set on the server.
  * Defaults to `8.1`

#### `php_memory_limit`
* The default maximum memory limit
* Applies to all php versions installed
* Defaults to `256M`.

#### `php_max_input_vars`
* The maximum number of input vars that can be accepted in a POST request
* Drupal typically needs this way higher than the default
* Applies to all php versions installed
* Defaults to `3001`.

#### `php_versions`
* A list of versions to install.
* Defaults to `[ {{php_default_version}} ]`.

#### `php_add_modules`
* A list of extra apt packages not already included in the default list. See [defaults/main.yml](defaults/main.yml).
* Defaults to an empty list. `[]`

#### `php_modules`
* Auto defined and populated by default, based on the combination of `php_versions` and `php_default_module_name_suffixes` (see [defaults/main.yml](defaults/main.yml))
* If you specify this var in your playbook, you will **completely override the ENTIRE list of ALL modules, for ANY PHP version** that the role installs. E.g. If you have multiple versions of php installed, you'll need to specify all modules for every version yourself.


## Dependencies

None


## Example Playbook
```yaml
- name: Install + Configure PHP
  hosts: servers
  gather_facts: yes
  become: yes
  vars:
    php_default_version: '8.1'
    php_versions:
      - '7.4'
      - '8.0'
      - '8.1'
    php_add_modules:
      - php7.4-foo
      - php8.0-foo
      - php8.1-foo
      - php8.1-bar
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
