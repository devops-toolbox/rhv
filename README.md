Role Name
=========

rhv: Rhv

[![Build Status](https://travis-ci.org/cmihai-ansible/rhv.svg?branch=master)](https://travis-ci.org/cmihai-ansible/rhv)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devops-toolbox.rhv](https://galaxy.ansible.com/devops-toolbox.rhv)

```bash
ansible-galaxy install devops-toolbox.rhv
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
rhv_packages_state: present
rhv_remove_packages: true
rhv_enable_service: true
rhv_enable_selinux: true
rhv_copy_templates: true
rhv_firewall_configure: true
rhv_firewall_rules:
  - service: ssh
  - port: 3389
rhv_users:
  - user: devops
    group: docker
rhv_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install rhv on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: rhv is configured
      import_role:
        name: devops-toolbox.rhv
      vars:
        rhv_packages_state: present
        rhv_remove_packages: true
        rhv_enable_service: true
        rhv_enable_selinux: true
        rhv_copy_templates: true
        rhv_firewall_configure: true
        rhv_firewall_rules:
          - service: ssh
          - port: 3389
        rhv_users:
          - user: devops
            group: docker
        rhv_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: rhv
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devops-toolbox.)
