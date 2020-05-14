[![Build Status](https://travis-ci.org/abdennour/ansible-role-golang.svg?branch=master)](https://travis-ci.org/abdennour/ansible-role-golang)

abdennnour.golang
=========

Go lang installation with GOPATH & GOROOT

```sh
ansible-galaxy install abdennour.golang
```

Requirements
------------

N/A


Role Variables
--------------


| Variable                | Description                                        | Default / Choices                               |
| ----------------------- | -----------------------------------------------    | ----------------------------------------------- |
| `golang_version`        | Go version                                         | (string) `1.14`                                 |
| `golang_gopath`         | Directory path Used to set GOPATH env var          | (string) `/opt/gopath`                          |
| `golang_install_dir`    | Directory path of software installation            | (string) `/usr/local/share`                     |



Dependencies
------------
N/A

Example Playbook
----------------

This is how you can use it:

    - hosts: all
      tasks:
      - name: Go lang is installed
        import_role:
          name: abdennour.golang
        vars:
          go_version: "1.14"
          

License
-------

BSD


[1]: https://docs.ansible.com/ansible/latest/modules/openssh_keypair_module.html#parameter-path
[2]: https://docs.ansible.com/ansible/latest/modules/openssh_keypair_module.html#parameter-type
[3]: https://docs.ansible.com/ansible/latest/modules/openssh_keypair_module.html#parameter-size