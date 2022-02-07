# Ansible Role for ipset

Manages Linux [IP sets](https://ipset.netfilter.org/) using the
[ipset](https://ipset.netfilter.org/ipset.man.html) utility.

IP sets are useful for firewall rules.

This role works well with the [ome.iptables-raw](https://github.com/ome/ansible-role-iptables-raw)
Ansible role for managing IPTables rules.

## Usage

Include the role in an Ansible Galaxy `requirements.yml` file:

```yaml
roles:
  - src: https://gitlab.com/jbeard.dev/ansible/jbeard-ipset.git
    scm: git
    name: ipset
```

Include in a playbook:

```yaml
- name: foo
  hosts: foo
  vars:
    ipsets:
      - name: foo_intranet
        type: 'hash:net'
        set:
          - 192.168.0.0/24
          - 192.168.16.0/24
      - name: bar_servers
        type: 'hash:net'
        set:
          - 192.168.0.4
          - 192.168.16.7
  roles:
    - ipset
```
