# OPNSense - List module

**STATE**: unstable

**TESTS**: Used in multiple ones

## Info

This module can list existing items/entries of a specified part of the OPNSense system.

## Definition

| Parameter | Type   | Required | Default value | Comment                                                                                                                                                                                                           |
|:----------|:-------|:---------|:--------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| target      | string | true     | -             | What part of the running config should be queried/listed. One of: 'alias', 'rule', 'route', 'cron', 'syslog', 'package', 'unbound_host', 'unbound_domain', 'unbound_dot', 'unbound_forward', 'unbound_host_alias' |

## Examples

```yaml
- hosts: localhost
  gather_facts: no
  module_defaults:
    ansibleguy.opnsense.list:
      firewall: 'opnsense.template.ansibleguy.net'
      api_credential_file: '/home/guy/.secret/opn.key'

  tasks:
    - name: Pulling aliases
      ansibleguy.opnsense.list:
        target: 'alias'
      register: existing_aliases

    - name: Printing
      ansible.builtin.debug:
        var: existing_aliases.data

    - name: Pulling routes
      ansibleguy.opnsense.list:
        target: 'route'
      register: existing_routes

    - name: Printing
      ansible.builtin.debug:
        var: existing_routes.data
```