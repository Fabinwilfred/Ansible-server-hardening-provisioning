# kubernetes

Installs kubectl from the official Kubernetes APT repository using GPG-keyring verification.

## Variables

See `defaults/main.yml` for all configurable variables and their defaults.

## Example

```yaml
- hosts: all
  become: true
  roles:
    - kubernetes
```

## License

MIT

## Author

Fabin Wilfred
