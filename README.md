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


| Variable                | Description                                               | Default / Choices                               |
| ----------------------- | ------------------------------------------------------    | ----------------------------------------------- |
| `golang_version`        | Go version                                                | (string) `1.14`                                 |
| `golang_gopath`         | Directory path Used to set GOPATH env var                 | (string) `/opt/gopath`                          |
| `golang_install_dir`    | Directory path of software installation                   | (string) `/usr/local/share`                     |
| `golang_tarball_repo`   | Remote Repository from where to download software         | (string) `https://golang.org/dl`                |
| `golang_packages`       | List of Go packages to be installed (check example below) | (array) i.e ["github.com/gorilla/mux"]          |
| `golang_users`          | List of users to be appended to Go group (example below)  | (array) i.e ["ec2-user"]                        |
| `golang_group`          | System group which owns Golang files                      | (string) `go`                                    |


Role Facts
----------

This role publish the variable `golang_fact_env` that can be used with the play which import the role.

`golang_fact_env` is a good workaround if your hosts does not recognize `go` command after installation.

If so, you just need to attach this variable as environment for the specific task

```yaml
# You import role 
# then,
- name: use go command
  command: go get github.com/go-redis/redis
  environment: "{{ golang_fact_env }}"
``` 


Dependencies
------------
N/A

Example Playbook
----------------

This is how you can use it:

```yaml
- hosts: all
  tasks:
  - import_role:
      name: abdennour.golang
    vars:
      golang_version: "1.14"
      golang_packages:
      - github.com/gorilla/mux
      - go.mongodb.org/mongo-driver/mongo
      golang_users:
      - "{{ ansible_ssh_user }}"
    become: yes
  
```

License
-------

BSD


[1]: https://docs.ansible.com/ansible/latest/modules/openssh_keypair_module.html#parameter-path
[2]: https://docs.ansible.com/ansible/latest/modules/openssh_keypair_module.html#parameter-type
[3]: https://docs.ansible.com/ansible/latest/modules/openssh_keypair_module.html#parameter-size