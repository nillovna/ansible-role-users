# ansible-role-users

This role creates users with specified home directory and shell, adds public key.

Role uses variable list ```system_users``` that must be defined in ```host_vars``` or ```group_vars```.
```system_users``` should have information about users name, home directory, shell, public_keys for user and does user have sudo rights without password(admin rights)

Playbook should be run with admin rights.

# Example

*Variables*

```
system_users:
    - { name: 'rick_sanchez', sudo: yes, home: '/home/sanchez', key: 'ssh-rsa AAA456', shell: '/bin/bash' }
    - { name: 'morty_smith', sudo: no, home: '/var/tmp/morty', key: 'ssh-rsa AAA123', shell: '/bin/sh' }
```

*Playbook*

```
- hosts: all
  become: yes
  roles:
    - users
```

# Requirements

ansible 2.0.2.0 and higher

## Other

Tested on ansible 2.0.2.0, vagrant debian and ubuntu.