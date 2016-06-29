Role Name
=========

A simple role for setting up a bind server.

Requirements
------------

Ansbile 2.0 or greater

Role Variables
--------------
```yaml
# defaults file for ansible-bind
firewall_zone: public

dns_serial: 3
dns_refresh: 604800
dns_retry: 86400
dns_expire: 2419200
dns_negative_cache_ttl: 604800
```
Dependencies
------------

No Dependencies

Example Playbook
----------------
```yaml
# file: bind.yaml
- hosts: bind-servers
  roles:
  - ansible-bind
  any_errors_fatal: true
  vars:
  - domain: kenscloud.io
  - forwarders:
    - 8.8.8.8
    - 8.8.4.4
  - a_records:
    - host: "*.apps.kenscloud.io"
      ip: 192.168.1.5
```
Example Inventory
-----------------
```ini
[bind-servers:children]
bind-masters
bind-slaves

[bind-masters]
rheldev

[bind-slaves]
```
License
-------

BSD
