# ANU

[![Build Status](https://travis-ci.com/mitchellcash/ansible-anu.svg?branch=master)](https://travis-ci.com/mitchellcash/ansible-anu)

## What is ANU?

ANU (pronounced 'anew' as in A New Ubuntu) is an Ansible playbook to assist in
provisioning a new Ubuntu machine. It helps create a secure base system, without
being too overbearing.

## Features

* Remove APT packages with known issues ([Source](https://github.com/dev-sec/ansible-os-hardening#packages))
  * xinetd
  * inetd
  * tftp-server
  * ypserv
  * telnet-server
  * rsh-server
  * prelink
* Set secure OpenSSH config values (assumes OpenSSH 6.7+) ([Source](https://infosec.mozilla.org/guidelines/openssh.html#modern-openssh-67))
* Deactivate Diffie-Hellman moduli less than 3072-bit long ([Source](https://infosec.mozilla.org/guidelines/openssh.html#modern-openssh-67))
* Prompts for a username/password and creates a new user in the "sudo" group ([Source](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-16-04#step-three-%E2%80%94-root-privileges))

## Requirements

ANU is tested on both Ubuntu 14.04 (Trusty Tahr) and Ubuntu 16.04 (Xenial Xerus).

**Ansible**

```
sudo apt-get install software-properties-common
sudo apt-add-repository ppa:ansible/ansible
sudo apt-get update
sudo apt-get install ansible
```

**Passlib**

Passlib requires Python 2 (>= 2.6) or Python 3 (>= 3.3).

```
sudo apt-get install python-pip
pip install passlib
```

## Quick Start

Once the requirements are installed, all you need to do is run the following
command to provision your new Ubuntu system:

```
ansible-playbook anu.yml
```

## License

ANU is released under the terms of the MIT license. See [LICENSE](LICENSE) for more
information or see https://opensource.org/licenses/MIT.
