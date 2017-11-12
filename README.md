pyslackers.python
=========

[![Build Status](https://travis-ci.org/ovv/ansible-role-transmission.svg?branch=master)](https://travis-ci.org/ovv/ansible-role-transmission)

Ansible role to install and configure Transmission.

Role Variables
--------------

* `rpc_enabled`: Enable transmission RPC (default to `false`).
* `rpc_address`: RPC listening address (default to `127.0.0.1`).
* `rpc_port`: RPC listening port (default to `8080`).
* `rpc_user`: Authorized user for RPC.
* `rpc_password`: Password for RPC user.
* `rpc_whitelist`: Whitelist IPs for RPC (default to `127.0.0.1,192.168.*.*`).

* `complete_directory`: Directory for completed downloads (default to `/home/{{ transmission_sftp_user }}/complete` or `/var/lib/transmission-daemon/complete`).
* `transmission_peer_port`: Transmission port (default to `51412`).

* `transmission_sftp_user`: Create user for sftp access.
* `transmission_sftp_password`: Password for sftp user.

Example Playbook
----------------

```yml
- hosts: localhost
  vars:
    rpc_user: foo
    rpc_password: bar
    rpc_enabled: false
  roles:
    - ovv.transmission
```

License
-------

MIT
