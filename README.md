ansible-role-code-server
========================

[![Ansible Role](https://img.shields.io/ansible/role/40925.svg)](https://galaxy.ansible.com/pallxk/code_server)
[![Build Status](https://travis-ci.org/testcab/ansible-role-code-server.svg?branch=master)](https://travis-ci.org/testcab/ansible-role-code-server)

This role installs and configures the latest or specified version of [code-server], supporting v3, v2 and v1.

Requirements
------------

None.

Role Variables
--------------

Variable             | Default  | Comment
-------------------- | -------- | -------
code_server_ver      | (undefined) | code-server release name on [GitHub](https://github.com/cdr/code-server/releases). <br> Defaults to the latest version (including pre-release).
code_server_data_dir | `{{ ansible_user_dir }}/.local/share/code-server` | Defaults to `.local/share/code-server` in the home directory of the remote user.
code_server_work_dir | (undefined) | Working directory. <br> Defaults to welcome screen if not set in v3 and v2. <br> Defaults to the home directory of the remote user in v1.
code_server_auth     | `password` | Authentication with `password` or `none`. <br> Available for code-server v3 and v2.
code_server_password | (undefined) | Leave undefined to use auto-generated password. <br> Check it with `journalctl -u code-server`
code_server_user     | `{{ ansible_user_id }}` | The user to run code-server. <br> Defaults to the user used in ansible ssh connection.
code_server_host     | `0.0.0.0`
code_server_port     | `8080`
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
