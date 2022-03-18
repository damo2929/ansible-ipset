# Ansible Role for ipset

Manages Linux [IP sets](https://ipset.netfilter.org/) using the
[ipset](https://ipset.netfilter.org/ipset.man.html) utility.

IP sets are useful for firewall rules.

This role works well with the [ome.iptables-raw](https://github.com/ome/ansible-role-iptables-raw)
Ansible role for managing IPTables rules.

## Usage

Include the role in an Ansible Galaxy [`requirements.yml`](https://galaxy.ansible.com/docs/using/installing.html#multiple-roles-from-multiple-files) file:

```yaml
roles:
  - src: https://github.com/joshbeard/ansible-ipset.git
    version: '0.1.0'
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

## Role Variables

Default values are set in [`defaults/main.yml`](https://github.com/joshbeard/ansible-ipset/blob/master/defaults/main.yml).

### `ipset_config_dir`

The absolute path to the config directory for ipset configurations.

Default: `/etc/sysconfig/ipset.d`

### `ipset_save_file`

The base filename of the ipset config file.

Default: `ipset.cfg`

### `ipsets`

List of ipset configuration.

The list should contain dictionaries for each ipset with the following keys:

* `name` - the name of the ipset
* `type` - the type of the ipset (e.g. `hash:net`)
* `set` - list of addresses to include in the ipset.

Refer to the [example above](#usage).

Default: `[]`

### `ipset_maxelem`

The maximal number of elements which can be stored in the set.

Default: `65536`

## License

[Zero-Clause BSD](https://opensource.org/licenses/0BSD)

See [`LICENSE`](https://github.com/joshbeard/ansible-ipset/blob/master/LICENSE)

## Authors

[Josh Beard](https://joshbeard.me)
