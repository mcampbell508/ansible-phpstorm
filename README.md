# Ansible Role PhpStorm

This is an Ansible role for installing the **latest** stable version of PhpStorm on a Linux machine.

JetBrains kindly provides [this URL](https://data.services.jetbrains.com/products/releases?code=PS&latest=true&type=release) which is used by this role to obtain the download URL of the latest stable version.

## Requirements

You will need to install the following package `python-jmespath` before you can use this role.

```
# Ubuntu

sudo apt-get update
sudo apt-get install python-jmespath

# Fedora

dnf install python-jmespath
```

## Variables

The following variables are available:

```
phpstorm_releases_url: "https://data.services.jetbrains.com/products/releases?code=PS&latest=true&type=release"
phpstorm_version: ""
phpstorm_url: ""
phpstorm_install_path: "/opt/phpstorm"
ansible_user
```

If you would like to install a specific version rather than the latest, then you should override the `phpstorm_url` variable.

## Example Playbook

> Before running this role, it is a good idea to **export any existing PhpStorm settings** you may have, as any existing version will be overwritten.

```
roles:
  - { role: mcampbell508.ansible-phpstorm, tags: phpstorm }
```

### Executing the Playbook

- `ansible-playbook /path/to/playbook-path.yml --ask-become-pass --tags=phpstorm`


#### Notes


- `become` priviliges will be required as we are writing to the `/opt/` directory.
- You will also be prompted to confirm that you have backed up your PhpStorm settings. Enter "yes" to confirm.

## Testing
This role has been tested using Ansible `2.4.1.0` on Ubunut 16.04, so this role might not work when using older versions of Ansible.

## License
MIT, please see [LICENSE](./LICENSE)
