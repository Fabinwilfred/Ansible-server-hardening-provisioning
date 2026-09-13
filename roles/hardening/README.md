# hardening

Applies kernel-level sysctl hardening (network and memory protections) via a dedicated sysctl.d drop-in file.

## Variables

See `defaults/main.yml` for all configurable variables and their defaults.

## Example

```yaml
- hosts: all
  become: true
  roles:
    - hardening
```

## License

MIT

## Author

Fabin Wilfred
