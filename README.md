ovv.transmission
================

[![Build Status](https://travis-ci.org/ovv/ansible-role-transmission.svg?branch=master)](https://travis-ci.org/ovv/ansible-role-transmission)

Ansible role to install and configure Transmission.

Installation
------------

To install this roles clone it into your roles directory.

```bash
$ git clone https://github.com/ovv/ansible-role-transmission.git ovv.transmission
```

If your playbook already reside inside a git repository you can clone it by using git submodules.

```bash
$ git submodule add -b master https://github.com/ovv/ansible-role-transmission.git ovv.transmission
```

Role Variables
--------------

* `rpc_enabled`: Enable transmission RPC (default to `false`).
* `rpc_address`: RPC listening address (default to `127.0.0.1`).
* `rpc_port`: RPC listening port (default to `8080`).
* `rpc_user`: Authorized user for RPC.
* `rpc_password`: Password for RPC user.
* `rpc_whitelist`: Whitelist IPs for RPC (default to `127.0.0.1,192.168.*.*`).

* `complete_directory`: Directory for completed downloads (default to `/var/lib/transmission-daemon/complete`).
* `transmission_peer_port`: Transmission port (default to `51412`).

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
