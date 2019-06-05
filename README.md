# An ansible role for ssh and related things.   [![Build Status](https://www.travis-ci.com/mafalb/ansible-ssh.svg?branch=master)](https://www.travis-ci.com/mafalb/ansible-ssh)

## Basic Usage

```
- hosts: localhost
  roles:
    - role: ssh/server
    - role: ssh/sftp_user
      user: mafalb_test2
```
```
```
- hosts: localhost
  roles:
    - role: ssh/server
    - role: ssh/sftp_user
      user: mafalb_test2
      uid: 8001
      group: blablubb
      gid: 8001
```


## Variables

```
ssh_server_config_file: path/to/configtemplate/relative/to/playbook
```
.This is optional. A default template comes with this role.

```
ssh_server_config:
    PasswordAuthentication: 'yes'|'no'   
    PermitRootLogin: 'yes'|'no'|without-password
    ...
```
specify configuration directives, see sshd_config(5). The template you use must implement it of course. The example template that comes with this role implements only some of them.

If you specify yes or no values be sure to write it as string

not
```
PasswordAuthentication: yes
```
but
```
PasswordAuthentication: 'yes'
```
```
ssh_sftp_chroot_group: sftp_chroot
```
The name of a group whose members are forced into a chroot by sftp

```
transfer_dirs:
  - me2client
  - client2me
```
if specified 2 subdirectories are created to split incoming from outgoing data.

```
transfer_dirs_mode: 00750
```
the permissions the transfer_dirs should have.

