# [fail2ban](#fail2ban)

Install and configure fail2ban on your system.

|Travis|GitHub|GitLab|Quality|Downloads|Version|
|------|------|------|-------|---------|-------|
|[![travis](https://travis-ci.com/robertdebock/ansible-role-fail2ban.svg?branch=master)](https://travis-ci.com/robertdebock/ansible-role-fail2ban)|[![github](https://github.com/robertdebock/ansible-role-fail2ban/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-fail2ban/actions)|[![gitlab](https://gitlab.com/robertdebock/ansible-role-fail2ban/badges/master/pipeline.svg)](https://gitlab.com/robertdebock/ansible-role-fail2ban)|[![quality](https://img.shields.io/ansible/quality/22987)](https://galaxy.ansible.com/robertdebock/fail2ban)|[![downloads](https://img.shields.io/ansible/role/d/22987)](https://galaxy.ansible.com/robertdebock/fail2ban)|[![Version](https://img.shields.io/github/release/robertdebock/ansible-role-fail2ban.svg)](https://github.com/robertdebock/ansible-role-fail2ban/releases/)|

## [Example Playbook](#example-playbook)

This example is taken from `molecule/resources/converge.yml` and is tested on each push, pull request and release.
```yaml
---
- name: Converge
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    - role: robertdebock.fail2ban
```

The machine needs to be prepared in CI this is done using `molecule/resources/prepare.yml`:
```yaml
---
- name: Prepare
  hosts: all
  gather_facts: no
  become: yes

  roles:
    - role: robertdebock.bootstrap
    - role: robertdebock.epel
```

Also see a [full explanation and example](https://robertdebock.nl/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

These variables are set in `defaults/main.yml`:
```yaml
---
# defaults file for fail2ban

fail2ban_loglevel: INFO
fail2ban_logtarget: /var/log/fail2ban.log

fail2ban_ignoreself: "true"
fail2ban_ignoreips: "127.0.0.1/8 ::1"

# In seconds
fail2ban_bantime: 600
fail2ban_findtime: 600

fail2ban_maxretry: 5
fail2ban_destemail: root@localhost
fail2ban_sender: root@{{ ansible_fqdn }}

fail2ban_configuration: []
#  - option: loglevel
#    value: "INFO"
#    section: Definition

fail2ban_jail_configuration: []
#  - option: ignoreself
#    value: "true"
#    section: DEFAULT
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/robertdebock/ansible-role-fail2ban/blob/master/requirements.txt).

## [Status of requirements](#status-of-requirements)

The following roles are used to prepare a system. You may choose to prepare your system in another way, I have tested these roles as well.

| Requirement | Travis | GitHub |
|-------------|--------|--------|
| [robertdebock.bootstrap](https://galaxy.ansible.com/robertdebock/bootstrap) | [![Build Status Travis](https://travis-ci.com/robertdebock/ansible-role-bootstrap.svg?branch=master)](https://travis-ci.com/robertdebock/ansible-role-bootstrap) | [![Build Status GitHub](https://github.com/robertdebock/ansible-role-bootstrap/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-bootstrap/actions) |
| [robertdebock.epel](https://galaxy.ansible.com/robertdebock/epel) | [![Build Status Travis](https://travis-ci.com/robertdebock/ansible-role-epel.svg?branch=master)](https://travis-ci.com/robertdebock/ansible-role-epel) | [![Build Status GitHub](https://github.com/robertdebock/ansible-role-epel/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-epel/actions) |

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/drawings/artifacts/fail2ban.png "Dependency")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/robertdebock):

|container|tags|
|---------|----|
|amazon|Candidate|
|el|7, 8|
|debian|buster, bullseye|
|fedora|all|
|ubuntu|focal, bionic|

The minimum version of Ansible required is 2.9, tests have been done to:

- The previous version.
- The current version.
- The development version.

## [Exceptions](#exceptions)

Some variarations of the build matrix do not work. These are the variations and reasons why the build won't work:

| variation                 | reason                 |
|---------------------------|------------------------|
| alpine | Service `fail2ban' needs non existent service `logger' |
| amazonlinux:1 | Based on EL6, not supported since 2020Q4. |
| opensuse | The package fail2ban depends on python2, we switched to python3. |


## [Testing](#testing)

[Unit tests](https://travis-ci.com/robertdebock/ansible-role-fail2ban) are done on every commit, pull request, release and periodically.

If you find issues, please register them in [GitHub](https://github.com/robertdebock/ansible-role-fail2ban/issues)

Testing is done using [Tox](https://tox.readthedocs.io/en/latest/) and [Molecule](https://github.com/ansible/molecule):

[Tox](https://tox.readthedocs.io/en/latest/) tests multiple ansible versions.
[Molecule](https://github.com/ansible/molecule) tests multiple distributions.

To test using the defaults (any installed ansible version, namespace: `robertdebock`, image: `fedora`, tag: `latest`):

```
molecule test

# Or select a specific image:
image=ubuntu molecule test
# Or select a specific image and a specific tag:
image="debian" tag="stable" tox
```

Or you can test multiple versions of Ansible, and select images:
Tox allows multiple versions of Ansible to be tested. To run the default (namespace: `robertdebock`, image: `fedora`, tag: `latest`) tests:

```
tox

# To run CentOS (namespace: `robertdebock`, tag: `latest`)
image="centos" tox
# Or customize more:
image="debian" tag="stable" tox
```

## [License](#license)

Apache-2.0

## [Contributors](#contributors)

I'd like to thank everybody that made contributions to this repository. It motivates me, improves the code and is just fun to collaborate.

- [j8r](https://github.com/j8r)
- [rgevaert](https://github.com/rgevaert)

## [Author Information](#author-information)

[Robert de Bock](https://robertdebock.nl/)

Please consider [sponsoring me](https://github.com/sponsors/robertdebock).
