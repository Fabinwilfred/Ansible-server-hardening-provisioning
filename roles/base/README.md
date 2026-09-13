# base

Base package installation, timezone, and hostname configuration applied to every managed host before role-specific hardening runs.

## Variables

See `defaults/main.yml` for all configurable variables and their defaults.

## Example

```yaml
- hosts: all
  become: true
  roles:
    - base
```

## License

Open source

## Author

Fabin Wilfred
