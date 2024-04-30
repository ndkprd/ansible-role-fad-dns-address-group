# ansible-role-fad-dns-address-group

An Ansible role to manage Fortinet's FortiADC DNS Server Group Address resources via HTTP REST API.

## Usage

## Inventory Example

```ini
[fortiadc]
fad-01.ndkprd.com ansible_host=10.10.10.10 fad_apitoken=loremipsum fad_vdom=root

```

### Playbook Example

```yaml
---

- name: Update/create FortiADC resources.
  hosts: all
  become: false
  gather_facts: false
  connection: local
  vars:
    fad_dns_address_groups:
      - name: local
        address_group_members:
          - id: 1 # high number of ID for mkey
            addr_type: ipv4 # or ipv6
            ip6_network: "::/0"
            ip4_network: "10.0.0.0/8"
            action: "include" # or exclude
          - id: 2 # high number of ID for mkey
            addr_type: ipv4 # or ipv6
            ip6_network: "::/0"
            ip4_network: "172.16.0.0/12"
            action: "include" # or exclude
          - id: 3 # high number of ID for mkey
            addr_type: ipv4 # or ipv6
            ip6_network: "::/0"
            ip4_network: "192.168.0.0/16"
            action: "include" # or exclude

  roles:
    - ndkprd.fad_dns_address_groups

```

## Limitation

Only tested against FortiADC with v7.0 firmware.

## License

MIT, please use at your own risk.
