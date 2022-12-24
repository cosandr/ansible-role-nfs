# ansible-role-nfs

![GitHub](https://img.shields.io/github/license/cosandr/ansible-role-nfs) ![GitHub last commit](https://img.shields.io/github/last-commit/cosandr/ansible-role-nfs) ![GitHub issues](https://img.shields.io/github/issues-raw/cosandr/ansible-role-nfs)

**Ansible role for setting up nfs.**

## Supported Platforms

| OS Family | Distribution  | Latest | Supported Version(s) | Comment |
|-----------|---------------|--------|----------------------|---------|
| RedHat    | RHEL          | :heavy_check_mark: | 9 | |
|           | RockyLinux    | :heavy_check_mark: | 8, 9 | |
|           | AlmaLinux     | :heavy_check_mark: | 8, 9 | |
|           | Fedora        | :heavy_check_mark: | 35, 36, 37 | |

## Requirements

Ansible 2.12 or higher.

## Variables

| Name           | Default Value | Description                        |
| -------------- | ------------- | -----------------------------------|
| `nfs_shares` | [] | List of NFS shares to configure, see playbook for example |
| `nfs_idmapping_configure` | true | Set to false to disable idmapping config |
| `nfs_idmapping_client` | false | Set to true to enable NFS client idmapping |
| `nfs_idmapping_server` | false | Set to true to enable NFS server idmapping |


## Dependencies

None.

## Example Playbook

```yaml
---

- hosts: all
  become: true
  # Not required
  gather_facts: false
  roles:
    - role: nfs
      vars:
        nfs_shares:
          - path: /mnt
            options: "rw,no_root_squash"
            sources:
              - "10.1.1.1"
              - "10.1.1.2"
              - "10.1.1.3"
```

## Author

[Andrei Costescu](https://github.com/cosandr/)
