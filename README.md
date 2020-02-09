Role Name
=========

codeready-containers: Codeready-containers

[![Build Status](https://travis-ci.org/cmihai-ansible/codeready-containers.svg?branch=master)](https://travis-ci.org/cmihai-ansible/codeready-containers)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devops-toolbox.codeready-containers](https://galaxy.ansible.com/devops-toolbox.codeready-containers)

```bash
ansible-galaxy install devops-toolbox.codeready-containers
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
codeready-containers_packages_state: present
codeready-containers_remove_packages: true
codeready-containers_enable_service: true
codeready-containers_enable_selinux: true
codeready-containers_copy_templates: true
codeready-containers_firewall_configure: true
codeready-containers_firewall_rules:
  - service: ssh
  - port: 3389
codeready-containers_users:
  - user: devops
    group: docker
codeready-containers_selinux_booleans:
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
- name: Install codeready-containers on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: codeready-containers is configured
      import_role:
        name: devops-toolbox.codeready-containers
      vars:
        codeready-containers_packages_state: present
        codeready-containers_remove_packages: true
        codeready-containers_enable_service: true
        codeready-containers_enable_selinux: true
        codeready-containers_copy_templates: true
        codeready-containers_firewall_configure: true
        codeready-containers_firewall_rules:
          - service: ssh
          - port: 3389
        codeready-containers_users:
          - user: devops
            group: docker
        codeready-containers_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: codeready-containers
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devops-toolbox.)
