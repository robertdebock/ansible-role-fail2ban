# [fail2ban](#fail2ban)

Install and configure fail2ban on your system.

|GitHub|GitLab|Quality|Downloads|Version|
|------|------|-------|---------|-------|
|[![github](https://github.com/robertdebock/ansible-role-fail2ban/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-fail2ban/actions)|[![gitlab](https://gitlab.com/robertdebock-iac/ansible-role-fail2ban/badges/master/pipeline.svg)](https://gitlab.com/robertdebock-iac/ansible-role-fail2ban)|[![quality](https://img.shields.io/ansible/quality/22987)](https://galaxy.ansible.com/robertdebock/fail2ban)|[![downloads](https://img.shields.io/ansible/role/d/22987)](https://galaxy.ansible.com/robertdebock/fail2ban)|[![Version](https://img.shields.io/github/release/robertdebock/ansible-role-fail2ban.svg)](https://github.com/robertdebock/ansible-role-fail2ban/releases/)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/robertdebock/ansible-role-fail2ban/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    - role: robertdebock.fail2ban
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/robertdebock/ansible-role-fail2ban/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: Prepare
  hosts: all
  become: yes
  gather_facts: no

  roles:
    - role: robertdebock.bootstrap
    - role: robertdebock.epel
```

Also see a [full explanation and example](https://robertdebock.nl/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/robertdebock/ansible-role-fail2ban/blob/master/defaults/main.yml):

```yaml
---
# defaults file for fail2ban

fail2ban_loglevel: INFO
fail2ban_logtarget: /var/log/fail2ban.log

fail2ban_ignoreself: "true"
fail2ban_ignoreips:
  - "127.0.0.1/8 ::1"

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

# Path to directory containing filters to copy in filter.d
# fail2ban_filterd_path:
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/robertdebock/ansible-role-fail2ban/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | GitLab |
|-------------|--------|--------|
|[robertdebock.bootstrap](https://galaxy.ansible.com/robertdebock/bootstrap)|[![Build Status GitHub](https://github.com/robertdebock/ansible-role-bootstrap/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-bootstrap/actions)|[![Build Status GitLab](https://gitlab.com/robertdebock-iac/ansible-role-bootstrap/badges/master/pipeline.svg)](https://gitlab.com/robertdebock-iac/ansible-role-bootstrap)|
|[robertdebock.epel](https://galaxy.ansible.com/robertdebock/epel)|[![Build Status GitHub](https://github.com/robertdebock/ansible-role-epel/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-epel/actions)|[![Build Status GitLab](https://gitlab.com/robertdebock-iac/ansible-role-epel/badges/master/pipeline.svg)](https://gitlab.com/robertdebock-iac/ansible-role-epel)|

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/ansible-role-fail2ban/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/robertdebock):

|container|tags|
|---------|----|
|[Amazon](https://hub.docker.com/repository/docker/robertdebock/amazonlinux/general)|Candidate|
|[EL](https://hub.docker.com/repository/docker/robertdebock/enterpriselinux/general)|8, 9|
|[Debian](https://hub.docker.com/repository/docker/robertdebock/debian/general)|all|
|[Fedora](https://hub.docker.com/repository/docker/robertdebock/fedora/general)|all|
|[Ubuntu](https://hub.docker.com/repository/docker/robertdebock/ubuntu/general)|all|

The minimum version of Ansible required is 2.12, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/robertdebock/ansible-role-fail2ban/issues)

## [License](#license)

[Apache-2.0](https://github.com/robertdebock/ansible-role-fail2ban/blob/master/LICENSE).

## [Author Information](#author-information)

[robertdebock](https://robertdebock.nl/)

Please consider [sponsoring me](https://github.com/sponsors/robertdebock).
