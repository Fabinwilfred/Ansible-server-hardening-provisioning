# users

Creates managed user accounts, deploys SSH public keys, and grants passwordless sudo to accounts flagged as admins.

## Variables

See `defaults/main.yml` for all configurable variables and their defaults.

## Example

```yaml
- hosts: all
  become: true
  roles:
    - users
```

## License

Open source

## Author

Fabin Wilfred
