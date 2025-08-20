# dbrennand.beszel

![Ansible-Lint](https://github.com/dbrennand/ansible-role-beszel/actions/workflows/ansible-lint.yml/badge.svg)
![Release](https://github.com/dbrennand/ansible-role-beszel/actions/workflows/release.yml/badge.svg)

Ansible role to install and configure a [Beszel](https://github.com/henrygd/beszel) binary agent.

> [!IMPORTANT]
> This Ansible role has been migrated to the [`community.beszel`](https://github.com/ansible-collections/community.beszel) Ansible Collection.
> This Ansible role will continue to function but all future development work will be included in the collection.

## Requirements

None.

## Role Variables

```yaml
beszel_public_key: ""
```

Public key used to authenticate the Beszel binary agent to the Hub.

```yaml
beszel_state: present
```

State of the Beszel binary agent installation. Can be either `present` or `absent`.

```yaml
beszel_version: latest
```

Version of the Beszel binary agent to install. Can be a specific version from GitHub (e.g., `v0.9.1`).

```yaml
beszel_port: 45876
```

Port for the Beszel binary agent to listen on.

```yaml
beszel_install_dir: /usr/local/bin
```

Directory to install the Beszel binary agent into.

```yaml
beszel_user: beszel
```

Name of the user to create and run the Beszel binary agent as.

```yaml
beszel_args: ""
```

Custom arguments for the Beszel binary agent.

```yaml
beszel_extra_filesystems: []
beszel_extra_filesystems:
  - sdb1
  - sdc1
  - mmcblk0
  - /mnt/network-share
```

Extra filesystems to be monitored by the Beszel binary agent. Configures the [EXTRA_FILESYSTEMS](https://beszel.dev/guide/additional-disks#binary-agent) environment variable in the agent systemd unit file.

```yaml
beszel_service_enabled: true
```

Enable the Beszel binary agent systemd service on boot.

```yaml
beszel_service_state: started
```

State of the Beszel binary agent systemd service.

## Dependencies

This role depends on a precompiled binary published on GitHub at [henrygd/beszel](https://github.com/henrygd/beszel/releases)

## Example Playbook

```yaml
- hosts: all
  roles:
    - role: dbrennand.beszel
      vars:
        beszel_public_key: "<Public key for Beszel hub>"

```

## License 📝

[LICENSE](LICENSE)

## Contributors

[dbrennand](https://github.com/dbrennand)

[stegmatze](https://github.com/stegmatze)

[crzykidd](https://github.com/crzykidd)
