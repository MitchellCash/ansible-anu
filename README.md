# ANU

[![Build Status](https://travis-ci.com/MitchellCash/ansible-anu.svg?branch=master)](https://travis-ci.com/MitchellCash/ansible-anu)

## What is ANU

ANU (pronounced 'anew' as in A New Ubuntu) is an Ansible playbook to assist in provisioning a new
Ubuntu machine. It depends on certain third-party Ansible roles and then extends them to offer
a more opinionated new Ubunutu setup (see [Features](#features)).

## Features

### Third-party

* Provides OS hardening via [dev-sec.os-hardening](https://github.com/dev-sec/ansible-collection-hardening/tree/master/roles/os_hardening)
* Provides SSH harderning via [dev-sec.ssh-hardening](https://github.com/dev-sec/ansible-collection-hardening/tree/master/roles/ssh_hardening)

### ANU

* Set server timezone to UTC
* Configure UFW to allow traffic on the specified SSH port and enable UFW
* Prompts for a username, password & SSH public key and creates a new user in the "sudo" group

## Requirements

ANU is tested on the following Ubuntu LTS releases:

### Ubuntu 18.04 (Bionic Beaver)

```sh
sudo apt update
sudo apt install software-properties-common ansible
```

### Ubuntu 20.04 (Focal Fossa)

Ubuntu 20.04

**Ansible**


**Ansible (Ubuntu <= 18.04)**

```sh
sudo apt update
sudo apt install software-properties-common
sudo apt-add-repository --yes --update ppa:ansible/ansible
sudo apt install ansible
```

**Passlib**

Required for generating secure passwords.

```sh
sudo apt install python3-pip
pip3 install passlib
```

## Quick Start

Once the requirements are installed, all you need to do is run the following
command to provision your new Ubuntu system:

```sh
ansible-playbook anu.yml
```

## License

ANU is released under the terms of the MIT license. See [LICENSE](LICENSE) for more
information or see https://opensource.org/licenses/MIT.



Dev notes

1. `ansible-galaxy role install -r requirements.yml`
1. `ansible-galaxy collection install -r requirements.yml`
2. `ansible-playbook anu.yml`


On Ubuntu 20.04 need Ansible 2.10

`sudo add-apt-repository ppa:ansible/testing-ansible-2.10`

`sudo apt update`

`sudo apt install ansible`
