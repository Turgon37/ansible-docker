Ansible Role Docker server
=========

[![Build Status](https://travis-ci.org/Turgon37/ansible-docker-server.svg?branch=master)](https://travis-ci.org/Turgon37/ansible-docker-server)

:warning: This role is under development, some important (and possibly breaking) changes may happend. Don't use it in production level environments but you can eventually base your own role on this one :hammer:

:grey_exclamation: Before using this role, please know that all my Ansible roles are fully written and accustomed to my IT infrastructure. So, even if they are as generic as possible they will not necessarily fill your needs, I advice you to carrefully analyse what they do and evaluate their capability to be installed securely on your servers.

**This roles configure the docker daemon.**

## Features

Currently this role provide the following features :

  * docker engine installation
  * docker engine configuration
  * docker engine systemd service file
  * install the docker-compose tool (if host architecture is x86)
  * [local facts](#facts)

## Requirements

### OS Family

This role is available for Debian 8/9 and CentOS

### Dependencies

--


## Role Variables

The variables that can be passed to this role and a brief description about them are as follows:

| Name                 | Types/Values   | Description                                                                                |
| ---------------------| ---------------|------------------------------------------------------------------------------------------- |
| docker_server__facts | Boolean        | Install the local fact script                                                              |


## Facts

By default the local fact are installed and expose all variables available with the docker info command line.

You can use this command to get an idea of available keys

```
docker version --format '{{json .}}'
```


## Examples Playbooks

To use this role create or update your playbook according the following examples :

  * Exemple of configuration with classical FILES backend

```
    - hosts: servers
      roles:
         - docker-server
      vars:
```


## License

MIT