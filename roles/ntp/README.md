# ntp

Installs and configures chrony for accurate host time, required for reliable log correlation and TLS/cert validation.

## Variables

See `defaults/main.yml` for all configurable variables and their defaults.

## Example

```yaml
- hosts: all
  become: true
  roles:
    - ntp
```

## License

Open source

## Author

Fabin Wilfred
