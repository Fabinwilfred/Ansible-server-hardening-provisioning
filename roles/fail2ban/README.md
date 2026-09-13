# fail2ban

Installs and configures fail2ban to automatically ban hosts showing brute-force or abusive login patterns.

## Variables

See `defaults/main.yml` for all configurable variables and their defaults.

## Example

```yaml
- hosts: all
  become: true
  roles:
    - fail2ban
```

## License

MIT

## Author

Fabin Wilfred
