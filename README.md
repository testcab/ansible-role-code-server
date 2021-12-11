ansible-role-code-server
========================

[![Ansible Role](https://img.shields.io/ansible/role/40925.svg)](https://galaxy.ansible.com/pallxk/code_server)
[![Build Status](https://travis-ci.org/testcab/ansible-role-code-server.svg?branch=master)](https://travis-ci.org/testcab/ansible-role-code-server)

This role installs and configures the latest or specified version of [code-server], supporting v4, v3, v2 and v1.

```sh
# Install the latest stable version of the role
ansible-galaxy install -f pallxk.code_server

# Install the latest development version of the role
ansible-galaxy install -f pallxk.code_server,master
```

To actually install *code-server*, refer to the section [Example Playbook](#example-playbook).

**Note:** The version of the role is irrelevant to the version of *code-server* you can install. Actually, it installs the latest version of *code-server* by default. And you can also use a lower-versioned role to install a higher-versioned *code-server*.  
When there are changes to the role, the role version will get updated to the latest version number of *code-server*.  
If you're having problems installing any version of code-server, please report the issue.  


Requirements
------------

None.

Role Variables
--------------

Variable             | Default  | Comment
-------------------- | -------- | -------
code_server_ver      | (undefined) | code-server release name on [GitHub](https://github.com/cdr/code-server/releases). <br> Defaults to the **latest** version (including pre-release).
code_server_install_prefix | `/usr/local` | Installation prefix for code-server.
code_server_data_dir | `{{ ansible_user_dir }}/.local/share/code-server` | Defaults to `.local/share/code-server` in the home directory of the remote user.
code_server_work_dir | (undefined) | Working directory. <br> Defaults to welcome screen if not set in v3 and v2. <br> Defaults to the home directory of the remote user in v1.
code_server_auth     | `password` | Authentication with `password` or `none`. <br> Available for code-server v3 and v2.
code_server_password | (undefined) | Leave undefined to use auto-generated password. <br> Check it with `journalctl -u code-server`
code_server_user     | `{{ ansible_user_id }}` | The user to run code-server. <br> Defaults to the user used in ansible ssh connection.
code_server_host     | `0.0.0.0`
code_server_port     | `8080`
code_server_env      | `{}` | Additional environment variables to set for code-server.
code_server_tls_cert | (undefined) | Leave undefined to use self-signed certificate.
code_server_tls_cert_remote | `no` | Change to `yes` if you're using a certificate that's already in your server (e.g.: if you use Let's Encrypt)
code_server_tls_key  | (undefined) | Leave undefined to use self-signed certificate.
code_server_tls_key_remote | `no` | Change to `yes` if you're using a key that's already in your server (e.g.: if you use Let's Encrypt)

Dependencies
------------

None.

Example Playbook
----------------

```yaml
#!/usr/bin/env ansible-playbook
---
- hosts: localhost
  gather_facts: yes
  roles:
    - name: pallxk.code_server
      code_server_password: SuperSecret
      code_server_user: "{{ ansible_user_id }}"
      code_server_host: 0.0.0.0
      code_server_port: 8443
      code_server_env:
        SERVICE_URL: https://open-vsx.org/vscode/gallery
        ITEM_URL: https://open-vsx.org/vscode/item
      code_server_tls_cert: /etc/letsencrypt/live/example.com/fullchain.pem
      code_server_tls_key: /etc/letsencrypt/live/example.com/privkey.pem
```

License
-------

The MIT License (MIT)

Author Information
------------------

[pallxk](https://github.com/pallxk)
[testcab](https://github.com/testcab)


[code-server]: https://github.com/cdr/code-server
