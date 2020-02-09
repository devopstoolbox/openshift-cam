Role Name
=========

openshift-cam: Openshift-cam

[![Build Status](https://travis-ci.org/cmihai-ansible/openshift-cam.svg?branch=master)](https://travis-ci.org/cmihai-ansible/openshift-cam)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.openshift-cam](https://galaxy.ansible.com/devopstoolbox.openshift-cam)

```bash
ansible-galaxy install devopstoolbox.openshift-cam
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
openshift-cam_packages_state: present
openshift-cam_remove_packages: true
openshift-cam_enable_service: true
openshift-cam_enable_selinux: true
openshift-cam_copy_templates: true
openshift-cam_firewall_configure: true
openshift-cam_firewall_rules:
  - service: ssh
  - port: 3389
openshift-cam_users:
  - user: devops
    group: docker
openshift-cam_selinux_booleans:
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
- name: Install openshift-cam on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: openshift-cam is configured
      import_role:
        name: devopstoolbox.openshift-cam
      vars:
        openshift-cam_packages_state: present
        openshift-cam_remove_packages: true
        openshift-cam_enable_service: true
        openshift-cam_enable_selinux: true
        openshift-cam_copy_templates: true
        openshift-cam_firewall_configure: true
        openshift-cam_firewall_rules:
          - service: ssh
          - port: 3389
        openshift-cam_users:
          - user: devops
            group: docker
        openshift-cam_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: openshift-cam
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devopstoolbox.)
