# OPNSense - Alias module

**STATE**: testing - but usable

This module allows you to manage single aliases.

If you want to mass-manage aliases - take a look at the [multi_alias](https://github.com/ansibleguy/collection_opnsense/blob/stable/docs/use_multi_alias.md) module. It is scales better for that use-case!

```yaml
- hosts: localhost
  gather_facts: no
  tasks:
    - name: Example
      ansibleguy.opnsense.alias:
        firewall: 'opnsense.template.ansibleguy.net'
        api_credential_file: '/home/guy/.secret/opn.key'
        name: 'ANSIBLE_TEST1'
        description: 'just a test'
        content: '1.1.1.1'
        state: 'present'
        # type: 'host'  # default
        # ssl_ca_file: '/etc/ssl/certs/custom/ca.crt'
        # ssl_verify: False
        # api_key: !vault ...  # alternative to 'api_credential_file'
        # api_secret: !vault ...
        # debug: false

    - name: Adding
      ansibleguy.opnsense.alias:
        firewall: 'opnsense.template.ansibleguy.net'
        api_credential_file: '/home/guy/.secret/opn.key'
        name: 'ANSIBLE_TEST2'
        content: '192.168.1.1'

    - name: Changing
      ansibleguy.opnsense.alias:
        firewall: 'opnsense.template.ansibleguy.net'
        api_credential_file: '/home/guy/.secret/opn.key'
        name: 'ANSIBLE_TEST2'
        content: ['192.168.1.5', '192.168.10.4']

    - name: Removing
      ansibleguy.opnsense.alias:
        firewall: 'opnsense.template.ansibleguy.net'
        api_credential_file: '/home/guy/.secret/opn.key'
        name: 'ANSIBLE_TEST3'
        state: 'absent'

    - name: Disabling
      ansibleguy.opnsense.alias:
        firewall: 'opnsense.template.ansibleguy.net'
        api_credential_file: '/home/guy/.secret/opn.key'
        name: 'ANSIBLE_TEST2'
        enabled: false
```