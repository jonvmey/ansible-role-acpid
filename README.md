# Ansible Role: acpid

Install and configures acpid service on Linux.

## Requirements

None.

## Role Variables

| Variable | Description | Default value |
|----------|-------------|---------------|
| `acpid_events_list` | List of events to manage **(see details!)** | `[]` |

#### `acpid_events_list` details

Each item in the list can have the following attributes:

| Variable | Description | required |
|----------|-------------|----------|
| `name` | Event name | yes |
| `state` | Event state 'present' (default) or 'absent' | no |
| `event` | Regex against which events are matched | yes |
| `action` | Shell command to invoke for a matching event | yes |

## Dependencies

None.

## Example Playbook

```yaml
---
- hosts: servers
  roles:
    - jonvmey.acpid
  vars:
    acpid_events_list:
      - name: brightness_down
        state: present
        event: video/brightnessdown
        action: xbacklight -dec 5
```

## License

MIT

## Author Information

This role was created in 2022 by [Jonathan VanderMey](https://github.com/jonvmey)
