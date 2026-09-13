# ssh

Hardens sshd: disables root login and password authentication, enforces key-only auth, and limits authentication attempts.

## Variables

See `defaults/main.yml` for all configurable variables and their defaults.

## Example

```yaml
- hosts: all
  become: true
  roles:
    - ssh
```

## License

MIT

## Author

Fabin Wilfred
