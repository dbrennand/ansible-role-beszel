# dbrennand.beszel

![Ansible-Lint](https://github.com/dbrennand/ansible-role-beszel/actions/workflows/ansible-lint.yml/badge.svg)
![Release](https://github.com/dbrennand/ansible-role-beszel/actions/workflows/release.yml/badge.svg)

Ansible role to install and configure a [Beszel](https://github.com/henrygd/beszel) binary agent.

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
beszel_auto_deploy: false
```
When `beszel_auto_deploy` is enabled, the Beszel agent is installed automatically across multiple machines, allowing new systems to be provisioned for monitoring without manual steps. Note: Currently, automatic deployment supports only FQDNs, not IP addresses.
Indicates whether the Beszel agent should be deployed using the fully automatic method. Set to `true` to enable automatic deployment; otherwise, manual steps be required.

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

```yaml
beszel_hub_url: ""
```

Set the beszel hub url. For example: `https://beszel.example.com`

```yaml
beszel_domain: ""
```

Set the domain that your servers use. For example: `example.com`

```yaml
beszel_users:
  - ""
```

List the Beszel user IDs to which the systems should be attached.

```yaml
beszel_api_token: ""
```
Set the API token for the Beszel Hub. To obtain the token, log in as a superuser and open your browser's developer tools. In local storage, locate the key `__pb_superuser_auth__`—its value is the API token. Note: This token is time-limited; you can inspect its expiration at [jwt.io](https://jwt.io).

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
