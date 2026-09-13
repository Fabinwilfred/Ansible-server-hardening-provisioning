# audit

Installs auditd and deploys a custom audit ruleset for tracking security-relevant system events.

## Variables

See `defaults/main.yml` for all configurable variables and their defaults.

## Example

```yaml
- hosts: all
  become: true
  roles:
    - audit
```

## License

MIT

## Author

Fabin Wilfred
