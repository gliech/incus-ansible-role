# [Incus Server Ansible Role][1]

[![test & release][2]][3]

This Ansible role installs Incus from the OS package manager and configures it
using a preseed object.

## Requirements

None.

## Role Variables

<table>
<tr><th>Name</th><th>Required</th><th>Type / Choices</th><th>Description</th></tr>
<tr><td><code>incus_config</code></td>
<td>yes</td>
<td>object</td>
<td>

Incus preseed configuration object. See the [Incus documentation][5] for
details. If you want idempotency checks to work correctly, you have to make sure
not to ommit any values which are output by `incus admin init --dump`, as the
role uses the difference between that and this variable to detect changes.

**Example:**
```yaml
config: {}
networks:
  - config:
      ipv4.address: none
      ipv4.nat: "true"
      ipv6.address: none
      ipv6.nat: "true"
    description: ""
    name: incusbr0
    type: bridge
    project: default
storage_pools:
  - config:
      source: /var/lib/incus/storage-pools/default
    description: ""
    name: default
    driver: dir
profiles:
  - config:
      security.idmap.isolated: "true"
    description: Default Incus profile
    devices:
      eth0:
        name: eth0
        network: incusbr0
        type: nic
      root:
        path: /
        pool: default
        type: disk
    name: default
projects:
  - config:
      features.images: "true"
      features.networks: "true"
      features.networks.zones: "true"
      features.profiles: "true"
      features.storage.buckets: "true"
      features.storage.volumes: "true"
    description: Default Incus project
    name: default
```
</td></tr>


<tr><td><code>incus_extra_users</code></td>
<td>no</td>
<td>list(string)</td>
<td>

This role will always add the ansible user to the incus group, so that it can
communicate with the incus unix socket to perform some of the tasks in this
role. You can optionally use this variable to specify additional user names to
add to the group.

**Default:** `[]`
</td></tr>


<tr><td><code>incus_subid_offset</code></td>
<td>no</td>
<td>integer</td>
<td>

Offset configured for the subordinate user IDs and subordinate group IDs in
`/etc/subuid` and `/etc/subgid` respectively.

**Default:** `1000000`
</td></tr>


<tr><td><code>incus_subid_range</code></td>
<td>no</td>
<td>integer</td>
<td>

Range configured for the subordinate user IDs and subordinate group IDs in
`/etc/subuid` and `/etc/subgid` respectively.

**Default:** `6553600`
</td></tr>
</table>

## Dependencies

None.

## Example Playbook

```yaml
- hosts: container_host
  tasks:
    - ansible.builtin.import_role:
        name: gliech.incus
      vars:
        incus_config:
          config: {}
          networks: []
          storage_pools:
            - config:
                source: /var/lib/incus/storage-pools/default
              description: ""
              name: default
              driver: dir
          profiles:
            - config:
                security.privileged: "true"
              description: Default Incus profile
              devices:
                root:
                  path: /
                  pool: default
                  type: disk
              name: default
          projects:
            - config:
                features.images: "true"
                features.networks: "true"
                features.networks.zones: "true"
                features.profiles: "true"
                features.storage.buckets: "true"
                features.storage.volumes: "true"
              description: Default Incus project
              name: default
```

## License

This project is licensed under the terms of the [GNU General Public License v3.0](LICENSE)

[1]: https://galaxy.ansible.com/ui/standalone/roles/gliech/incus/
[2]: https://github.com/gliech/incus-ansible-role/actions/workflows/release.yml/badge.svg
[3]: https://github.com/gliech/incus-ansible-role/actions/workflows/release.yml
[4]: https://github.com/gliech/semantic-release-config-github-ansible-role
[5]: https://linuxcontainers.org/incus/docs/main/howto/initialize/#non-interactive-configuration
