# Ansible Role Nexus

## Prerequisites

* Java 8

## Usage

    http://<server>:8081

## Example Playbook

    - hosts: servers
      roles:
      - ansible-role-nexus

## Main variables

## Default variables

    nexus_application_port: 8081
    nexus_application_host: '0.0.0.0'
    nexus_user: 'nexus'
    nexus_group: 'nexus'
    nexus_java_home: '/usr/lib/jvm/java-8-oracle'

## Advanced variables

**nexus_context_path:** '/' . The <context> is added almost like that: http://<server>:<port>/<context>

**nexus_java_home:** '/usr/lib/jvm/java-8-oracle'

**nexus_cleanup:** 'true' or 'false'. Enable to remove the downloaded tar.gz file.

**nexus_update:** 'true' or 'false'. Enable to update an installed nexus.

## License

MIT

## Author Information

This role was created in 2016 by Olivier Locard on the behalf of Deveryware.

