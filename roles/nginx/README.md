# nginx

Installs Nginx and deploys a minimal templated document root, used as the base web-serving role.

## Variables

See `defaults/main.yml` for all configurable variables and their defaults.

## Example

```yaml
- hosts: all
  become: true
  roles:
    - nginx
```

## License

MIT

## Author

Fabin Wilfred
