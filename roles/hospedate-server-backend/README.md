# Hospedate Backend

* **standard**: install the  dependencies from APT repositories and the


## Supported versions and systems Gazellacom

| System / Python | 3.10| 3.12|
|-----------------|-----|-----|
| Ubuntu 22.04    | yes | yes |
| Ubuntu 24.04    | yes | yes |

## Example (Playbook)


### Define host.production file

```yaml
[production]
localhost

[gazellacom:vars]
ansible_user=ubuntu
ansible_become=yes
ansible_python_interpreter=/usr/bin/python3
ansible_ssh_private_key_file= ./KEY-SWISSTECH.pem

[gazellaerp]
localhost

[gazellaerp:vars]
ansible_user=ubuntu
ansible_become=yes
ansible_python_interpreter=/usr/bin/python3
ansible_ssh_private_key_file= ./KEY-SWISSTECH.pem

```



### gazellaerp_install_type: standard (default)

Standard installation (assuming that PostgreSQL is installed and running on
AWS RSD Services):

```yaml
- name: Gazella ERP
  hosts: gazellaerp-server
  become: true
  roles:
    - role: gazella.erp
      gazellaerp_install_type: standard
      gazellaerp_version: 11.0
      gazellaerp_user: gazellaerp-user
      gazellaerp_logdir: /var/log/odoo
      gazellaerp_workdir: /opt/odoo
      gazellaerp_rootdir: /opt/odoo
      gazellaerp_init: True
      gazellaerp_repo_type: git
      gazellaerp_repo_url: https://www.github.com/odoo/odoo.git
      gazellaerp_repo_dest: /opt/odoo
      gazellaerp_repo_rev: 11.0 # branch name
```




