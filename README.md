ovv.transmission
================

[![Build Status](https://travis-ci.org/ovv/ansible-role-transmission.svg?branch=master)](https://travis-ci.org/ovv/ansible-role-transmission)

Ansible role to install and configure Transmission.

Requirements
------------

An nginx installation is recommended. We recommend using [pyslackers.nginx](https://github.com/pyslackers/ansible-role-nginx).

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
* `rpc_port`: RPC listening port (default to `8080`).
* `rpc_user`: Authorized user for RPC.
* `rpc_password`: Password for RPC user.

* `transmission_complete_directory`: Directory for completed downloads (default to `/var/lib/transmission-daemon/complete`).
* `transmission_complete_directory_group`: Group for completed downloads directory (default to `debian-transmission`).
* `transmission_complete_directory_mode`: Mode for completed downloads directory (default to `0774`).
* `transmission_peer_port`: Transmission port (default to `51412`).

Example Playbook
----------------

```yml
- hosts: localhost
  roles:
    - ovv.transmission
    - pyslackers.nginx
  vars:
    rpc_user: foo
    rpc_password: bar
    rpc_enabled: true

    # pyslackers.nginx variables
    nginx_sites:
      transmission:
        locations:
          - location: /rpc
            proxy_pass: http://127.0.0.1:8080
          - location: /web/
            proxy_pass: http://127.0.0.1:8080
          - location: /upload
            proxy_pass: http://127.0.0.1:8080
          - location: /web/style
            custom: alias /usr/share/transmission/web/style/;
          - location: /web/javascript
            custom: alias /usr/share/transmission/web/javascript/;
          - location: /web/images/
            custom: alias /usr/share/transmission/web/images/;
          - location: /
            proxy_pass: http://127.0.0.1:8080/web
```

License
-------

MIT
