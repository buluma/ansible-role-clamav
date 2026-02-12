# [Ansible role clamav](#ansible-role-clamav)

Install and configure clamav on your system.

|GitHub|GitLab|Downloads|Version|
|------|------|---------|-------|
|[![github](https://github.com/buluma/ansible-role-clamav/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-clamav/actions)|[![gitlab](https://gitlab.com/shadowwalker/ansible-role-clamav/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-clamav)|[![downloads](https://img.shields.io/ansible/role/d/buluma/clamav)](https://galaxy.ansible.com/buluma/clamav)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-clamav.svg)](https://github.com/buluma/ansible-role-clamav/releases/)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/buluma/ansible-role-clamav/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  become: true
  gather_facts: true

  roles:
    - role: buluma.clamav
      freshclam_private_mirrors:
        - https://www.danami.com/hotfix/clamav
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/buluma/ansible-role-clamav/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: Prepare
  hosts: all
  gather_facts: false
  become: true

  roles:
    - role: buluma.bootstrap
    - role: buluma.epel
```

Also see a [full explanation and example](https://buluma.github.io/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/buluma/ansible-role-clamav/blob/master/defaults/main.yml):

```yaml
---
# defaults file for clamav

# SELinux has to be configured to allow scanning. Set clamav_can_scan_system to
# either "true" or "false". Only has effect on systems that support SELinux.
clamav_can_scan_system: true

# Configure any parameter using "regexp" and "line". The parameter "regexp"
# contains the line that needs to be replaced. The replacement is stored in
# "line".
clamav_configuration:
  - line: "Example"
    state: absent
  - line: "TCPSocket 10025"
  - line: "TCPAddr 127.0.0.1"
  - line: "LogFile /var/log/clamd.scan"

# If you have local clamav mirrors (as recommended by ClamAV),
# you will also need to define a list variable with your mirrors to add,
# as the following example indicates:
# freshclam_private_mirrors:
#   - mirror1.mynetwork.com
#   - mirror2.mynetwork.com
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-clamav/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | GitLab |
|-------------|--------|--------|
|[buluma.bootstrap](https://galaxy.ansible.com/buluma/bootstrap)|[![Build Status GitHub](https://github.com/buluma/ansible-role-bootstrap/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-bootstrap/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-bootstrap/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-bootstrap)|
|[buluma.epel](https://galaxy.ansible.com/buluma/epel)|[![Build Status GitHub](https://github.com/buluma/ansible-role-epel/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-epel/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-epel/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-epel)|

## [Context](#context)

This role is part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-clamav/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|[Alpine](https://hub.docker.com/r/buluma/alpine)|all|
|[Amazon](https://hub.docker.com/r/buluma/amazonlinux)|all|
|[EL](https://hub.docker.com/r/buluma/enterpriselinux)|all|
|[Debian](https://hub.docker.com/r/buluma/debian)|all|
|[Fedora](https://hub.docker.com/r/buluma/fedora)|all|
|[Ubuntu](https://hub.docker.com/r/buluma/ubuntu)|all|

The minimum version of Ansible required is 2.12, tests have been done on:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them on [GitHub](https://github.com/buluma/ansible-role-clamav/issues).

## [License](#license)

[Apache-2.0](https://github.com/buluma/ansible-role-clamav/blob/master/LICENSE).

## [Author Information](#author-information)

[buluma](https://buluma.github.io/)

