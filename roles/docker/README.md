# docker

Installs Docker Engine from Docker's official APT repository using GPG-keyring verification (not the deprecated apt-key).

## Variables

See `defaults/main.yml` for all configurable variables and their defaults.

## Example

```yaml
- hosts: all
  become: true
  roles:
    - docker
```

## License

MIT

## Author

Fabin Wilfred
