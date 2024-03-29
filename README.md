# ANU

[![CI](https://github.com/MitchellCash/ansible-anu/actions/workflows/ci.yml/badge.svg)](https://github.com/MitchellCash/ansible-anu/actions/workflows/ci.yml)

## What is ANU

ANU (pronounced 'anew' as in A New Ubuntu) is an Ansible playbook to assist in provisioning a new
Ubuntu machine. It depends on certain third-party Ansible roles and then extends them to offer
a more opinionated new Ubuntu setup (see [Features](#features)).

## Features

### Third-party

* Provides OS hardening via [dev-sec.os-hardening](https://github.com/dev-sec/ansible-collection-hardening/tree/master/roles/os_hardening)
* Provides SSH hardening via [dev-sec.ssh-hardening](https://github.com/dev-sec/ansible-collection-hardening/tree/master/roles/ssh_hardening)

### ANU

* Set server timezone to UTC
* Configure UFW to allow traffic on the specified SSH port and enable UFW
* Prompts for a username, password & SSH public key and creates a new user in the "sudo" group

## Requirements

ANU is tested on the following Ubuntu LTS releases:

### Ubuntu 18.04 (Bionic Beaver)

```sh
sudo apt update
sudo apt install software-properties-common
sudo add-apt-repository --yes --update ppa:ansible/ansible
sudo apt install ansible
```

### Ubuntu 20.04 (Focal Fossa)

Ubuntu 20.04 requires Ansible >=2.10, which as of the time of writing is not yet available in the
main Ansible PPA. In order to install 2.10 we must add the `ansible/ansible-2.10` PPA.

```sh
sudo apt update
sudo apt install software-properties-common
sudo add-apt-repository ppa:ansible/ansible-2.10
sudo apt install ansible
```

## Quick Start

Once the requirements are installed, all you need to do is run the following commands to provision
your new Ubuntu system:

```sh
# Install collection requirements.
ansible-galaxy collection install -r requirements.yml

# Install role requirements.
ansible-galaxy role install -r requirements.yml

# Run the ANU playbook.
ansible-playbook anu.yml
```

## Known Issues

After running this playbook you can sometimes experience strange networking issues (like when using
`apt`). This can sometimes be relating to connecting to servers over IPv6. To resolve this issue:

Open `/etc/gai.conf` and uncomment the following line:

```sh
# precedence ::ffff:0:0/96 100
```

This will allow you to still use IPv6 but sets IPv4 as the precedence so that apt won’t get stuck.

## License

ANU is released under the terms of the MIT license. See [LICENSE](LICENSE) for more information or
see https://opensource.org/licenses/MIT.
