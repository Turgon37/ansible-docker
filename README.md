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

This role is available for

  * Debian/Raspbian 8/9
  * CentOS 7

### Dependencies

--


## Role Variables

The variables that can be passed to this role and a brief description about them are as follows:

| Name                                      | Types/Values   | Description                                                                                                                                                                                                                                   |
| ------------------------------------------| ---------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| docker_server__facts                      | Boolean        | Install the local fact script                                                                                                                                                                                                                 |
| docker_server__edition                    | String         | Install edition in 'ce' (Community Edition) or 'ee' (Enterprise Edition)                                                                                                                                                                      |
| docker_server__repository_release_channel | String         | The release channel to use in 'stable', 'edge', 'test'                                                                                                                                                                                        |
| docker_server__compose_version            | String         | The version of docker-compose to install                                                                                                                                                                                                      |
| docker_server__compose_state              | String         | The state of docker-compose tool in 'present', 'absent'                                                                                                                                                                                       |
| docker_server__service_enabled            | Boolean        | Enable or not the docker service on the host                                                                                                                                                                                                  |
| docker_server__service_restartable        | Boolean        | If the docker configuration change ansible will automatically restart the service unless this variable is set to False. In others words, set this to True if you want ansible automatically restart the docker daemon on configuration changes|
| docker_server__service_restart_stamp_file | String         | If service_restartable (above) is set to False, ansible will touch this path instead of restarting docker. This allow you to test the presence of this file with your monitoring tool                                                         |
| docker_server__socket_group               | String         | The name of the linux group the socket will belong to                                                                                                                                                                                         |
| docker_server__socket_group_users         | List of String | The list of linux local user name you want to add to socket group                                                                                                                                                                             |

:exclamation: In a production environment I recommend to set docker_server__service_restartable to False and to handle manually the docker service's restarts

## Facts

By default the local fact are installed and expose all variables available with the docker info command line.

You can use this command to get an idea of available keys

```
docker version --format '{{json .}}'
```

In addition, the following facts are available about docker-compose

* ```ansible_local.docker_compose.version_full```
* ```ansible_local.docker_compose.version_major```


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