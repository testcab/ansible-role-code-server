ansible-role-code-server
========================

[![Ansible Role](https://img.shields.io/ansible/role/40925.svg?style=flat-square)](https://galaxy.ansible.com/pallxk/code_server)

This role installs and configures [code-server], supporting both v1 and v2.

Requirements
------------

None.

Role Variables
--------------

Variable             | Default  | Comment
-------------------- | -------- | -------
code_server_ver      | `2.1523-vsc1.38.1` | code-server release name on [GitHub](https://github.com/cdr/code-server/releases)
code_server_data_dir | `~/.local/share/code-server`
code_server_work_dir | `~` | Working directory
code_server_password | (not defined) | Leave not defined to use auto-generated password. <br> Check it with `journalctl -u code-server`
code_server_user     | `root` | The user to run code-server
code_server_host     | `0.0.0.0`
code_server_port     | `8080`
tls_cert             | (not defined) | Leave not defined to use self-signed certificate.
tls_cert_remote      | `no` | Change to `yes` if you're using a certificate that's already in your server (e.g.: if you use Let's Encrypt)
tls_key              | (not defined) | Leave not defined to use self-signed certificate.
tls_key_remote      | `no` | Change to `yes` if you're using a key that's already in your server (e.g.: if you use Let's Encrypt)

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
    - name: pallxk/code_server
      code_server_work_dir: ~/code-server
      code_server_password: SuperSecret
      code_server_user: "{{ ansible_user_id }}"
      code_server_host: 0.0.0.0
      code_server_port: 8443
      tls_cert: /etc/letsencrypt/live/example.com/fullchain.pem
      tls_key: /etc/letsencrypt/live/example.com/privkey.pem
```

License
-------

The MIT License (MIT)

Author Information
------------------

[pallxk](https://github.com/pallxk)
[testcab](https://github.com/testcab)


[code-server]: https://github.com/cdr/code-server
