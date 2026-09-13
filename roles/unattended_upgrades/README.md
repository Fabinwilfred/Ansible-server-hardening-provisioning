# unattended_upgrades

Enables unattended-upgrades for automatic security patching, with configurable auto-reboot behaviour.

## Variables

See `defaults/main.yml` for all configurable variables and their defaults.

## Example

```yaml
- hosts: all
  become: true
  roles:
    - unattended_upgrades
```

## License

Open source

## Author

Fabin Wilfred
