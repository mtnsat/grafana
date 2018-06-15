# Grafana

[![License](https://img.shields.io/badge/license-New%20BSD-blue.svg?style=flat)](https://raw.githubusercontent.com/ansiblebit/grafana/master/LICENSE)
[![Build Status](https://travis-ci.org/ansiblebit/grafana.svg?branch=master)](https://travis-ci.org/ansiblebit/grafana)

[![Platform](http://img.shields.io/badge/platform-debian-a80030.svg?style=flat)](#)
[![Platform](http://img.shields.io/badge/platform-ubuntu-dd4814.svg?style=flat)](#)

[![Project Stats](https://www.openhub.net/p/ansiblebit-grafana/widgets/project_thin_badge.gif)](https://www.openhub.net/p/ansiblebit-grafana/)

[Ansible][ansible] role to setup [Grafana][grafana].


## Tests

| Family | Distribution | Version | Test Status |
|:-:|:-:|:-:|:-:|
| Debian | Debian  | Jessie  | [![x86_64](http://img.shields.io/badge/x86_64-passed-006400.svg?style=flat)](#) |
| Debian | Debian  | Wheezy  | [![x86_64](http://img.shields.io/badge/x86_64-passed-006400.svg?style=flat)](#) |
| Debian | Ubuntu  | Xenial  | [![x86_64](http://img.shields.io/badge/x86_64-passed-006400.svg?style=flat)](#) |
| Debian | Ubuntu  | Trusty  | [![x86_64](http://img.shields.io/badge/x86_64-passed-006400.svg?style=flat)](#) |
| Debian | Ubuntu  | Precise | [![x86_64](http://img.shields.io/badge/x86_64-passed-006400.svg?style=flat)](#) |
| Debian | Ubuntu  | Vivid   | [![x86_64](http://img.shields.io/badge/x86_64-passed-006400.svg?style=flat)](#) |


## Requirements

- ansible >= 1.9.6


## Role Variables

- **grafana_admin_password**: password for the [Grafana][grafana] administrator account.
- **grafana_admin_user**: user name for the [Grafana][grafana] administrator account.
- **grafana_apt_dependencies**: packages needed to be able to run this playbook or install [Grafana][grafana].
- **grafana_conf_file**: the file that will contain [Grafana][grafana]'s configuration.
- **grafana_conf_data**: the contents of [Grafana][grafana]'s configuration file.
- **grafana_default**: the contents of [Grafana][grafana]'s init script environment. 
- **grafana_dir_conf**: the directory where the [Grafana][grafana] configuration file will be stored.
- **grafana_dir_data**: the directory where the [Grafana][grafana] data will be stored.
- **grafana_dir_home**: the [Grafana][grafana] home directory.
- **grafana_dir_log**: the directory where the [Grafana][grafana] log files will be stored.
- **grafana_dir_plugins**: the directory where the [Grafana][grafana] plugins will be stored.
- **grafana_http_port**: the port where the [Grafana][grafana] service will be running.
- **grafana_group**: the [Grafana][grafana] group.
- **grafana_pid_file_dir**: directory where PID file will be written to.
- **grafana_pid_file**: path to PID file.
- **grafana_user**: the [Grafana][grafana] user.
- **grafana_enable_ldap**: set to `true` when using ldap

## LDAP Variables
- **grafana_ldap_host**: space seperated values for ldap server 
- **grafana_ldap_port**: port for ldap config
- **grafana_use_ssl**: set to `true` if ldap server supports TLS
- **grafana_start_tls**: Set to true if connect ldap server with STARTTLS pattern (create connection in insecure, then upgrade to secure connection with TLS)
- **grafana_skip_ssl_verify**: set to true if you want to skip ssl cert validation
- **grafana_bind_dn**: ldap bind dn
- **grafana_bind_password**:  ldap bind password `If the password contains # or ; you have to wrap it with triple quotes. Ex """#password;"""`
- **grafana_search_filter**: User search filter, for example "(cn=%s)" or "(sAMAccountName=%s)" or "(uid=%s)"
- **grafana_search_base_dn**: An array of base dns to search through
- **grafana_ldap_name**: Specify names of the ldap attributes your ldap uses for name.
- **grafana_ldap_surname**: Specify names of the ldap attributes your ldap uses for surname.
- **grafana_ldap_username**: Specify names of the ldap attributes your ldap uses for username.
- **grafana_ldap_memeber_of**: Specify names of the ldap attributes your ldap uses for member_of.
- **grafana_ldap_email**: Specify names of the ldap attributes your ldap uses for email.
- **grafana_group_mappings**: Map ldap groups to [Grafana][grafana] org roles.  list the org role followed by the dn 
```
grafana_group_mappings:
  Admin:
    - 'cn=users,dc=grafana,dc=org'
  Viewer:
    - '*'
```

Unless stated otherwise a default value is provided for each of the variables mentioned above in the `defaults` directory.


## Dependencies

None.


## Playbooks

    - hosts: servers
      roles:
         - role: ansiblebit.grafana

## Tags

- **configuration**: configuration tasks.
- **debug**: task to debug role variables.
- **installation**: installation tasks.
- **validation**: task to validate role variables.


## Test

To run the tests you will need to install:

- [tox](https://tox.readthedocs.org/)
- [vagrant](https://www.vagrantup.com/)

To run all tests against all pre-defined OS/distributions * ansible versions:

```
$ tox
```

To run tests for `trusty64`:

```
$ cd tests
$ bash test_idempotence.sh --box trusty64.vagrant.dev
# log file will be stores under tests/log
```

To perform debugging on a specific environment:

```
$ cd tests
$ vagrant up trusty64.vagrant.dev

# to provision using the test.yml playbook (as many time as you need)
$ vagrant provision trusty64.vagrant.dev

# to access the Vagrant box
$ vagrant ssh trusty64.vagrant.dev
```


## Links

- [Grafana : Installing on Debian / Ubuntu](http://docs.grafana.org/installation/debian/)


## License

[BSD][license]


## Author Information

- [steenzout][steenzout]


[ansible]:      https://www.ansible.com         "Ansible"
[grafana]:      http://grafana.org              "Grafana"
[license]:      https://github.com/ansiblebit/grafana/blob/master/LICENSE  "BSD license"
[steenzout]:    https://github.com/steenzout/   "Pedro Salgado"
