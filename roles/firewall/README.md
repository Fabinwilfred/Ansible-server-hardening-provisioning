# firewall

Configures UFW with a default-deny incoming policy, opening only the ports explicitly required (SSH, optionally HTTP).

## Variables

See `defaults/main.yml` for all configurable variables and their defaults.

## Example

```yaml
- hosts: all
  become: true
  roles:
    - firewall
```

## License

MIT

## Author

Fabin Wilfred
