fail2ban
=========

[![Build Status](https://travis-ci.org/robertdebock/ansible-role-fail2ban.svg?branch=master)](https://travis-ci.org/robertdebock/ansible-role-fail2ban)

Provides Postfix for your system.

Context
--------
This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/robertdebock.github.io/artifacts/fail2ban.png "Dependency")

Requirements
------------

Access to a repository containing packages, likely on the internet.
For Red Hat systems: Extra Packages for Enterprise Linux. (Hint: robertdebock.epel)

Role Variables
--------------

None known

Dependencies
------------

These roles can help prepare your system.

- robertdebock.bootstrap
- robertdebock.epel

Download the dependencies by issuing this command:
```
ansible-galaxy install --role-file requirements.yml
```

Example Playbook
----------------

```
- hosts: servers

  roles:
    - role: robertdebock.bootstrap
    - role: robertdebock.epel
    - role: robertdebock.fail2ban
```

Install this role using `galaxy install robertdebock.fail2ban`.

License
-------

Apache License, Version 2.0

Author Information
------------------

Robert de Bock <robert@meinit.nl>
