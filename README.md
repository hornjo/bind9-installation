bind9-installation
=========

Installs and maintains bind9 installation and configuration.

Requirements
------------

Install all needed packages from the requirements files.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```YAML
---
- name: Install bind9 dns
  hosts: mgm-vm
  roles:
    - hornjo.bind9-installation
  vars:
    bind9_acl:
      - localhost
      - localnets
      - 10.51.0.0/24
      - 10.49.0.0/24
    bind9_forwarders:
      - 1.1.1.1
      - 1.0.0.1
    bind9_mail_address: info.k8s
    bind9_zones_forward:
      k8s:
        - {record_type: A, value1: firewall, value2: 10.10.1.254}
    bind9_zones_reverse:
      1.10.10:
        - {ip: 254, name: firewall.k8s}
    bind9_zones_remote:
      - {domain: remote.domain.local, remote_dns: 10.0.0.1}
      - {domain: 0.0.10.in-addr.arpa, remote_dns: 10.0.0.1}

```
