Ansible Role Docker
========

This roles allow installation of the Docker engine

## OS Family

This role is available for CentOS and Debian (with systemd only !!)

## Features

At this day the role can be used to :

  * Install Docker engine
  * Configure Docker engine service (via systemd)
  * Install docker-compose (if arch is x86)

## Configuration

  * The role accept this list of parameters

| Name                   | Description                                                                                 |
| ---------------------- | ------------------------------------------------------------------------------------------- |
| docker__packages_name  | The list of packages to install                                                             |
| docker__service_name   | The name of the systemd service                                                             |
| docker__host           | The address on which dockerd will listen (default to "unix:///var/run/docker.sock")         |
| docker__storage_driver | The name of the storage driver to use                                                       |
| docker__storage_opt    | The dictionnary of storage options (each key value will be put into the configuration file  |
| docker__tlsverify      | If true, enable tls certificate verification                                                |
| docker__tlscacert      | The path to the certificate authority                                                       |
| docker__tlscert        | The path to the dockerd's certificate                                                       |
| docker__tlskey         | The path to the dockerd's private key                                                       |
