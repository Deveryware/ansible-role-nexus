# Ansible Role Nexus

## Prerequisites

* Java 8

## Usage

    http://<server>:8081

The default login credentials are : `admin / admin123`

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

## Advanced variables

**nexus_context_path:** '/' . The <context> is added almost like that: http://<server>:<port>/<context>

**nexus_java_home:** '/usr/lib/jvm/java-8-oracle'

**nexus_cleanup:** 'true' or 'false'. Enable to remove the downloaded tar.gz file.

**nexus_update:** 'true' or 'false'. Enable to update an installed nexus.

## VM options

You can override some parameters in `bin/nexus.vmoptions`, the default values are below:

    nexus_vmoptions:
    - key: '-Xms'
      value: '1200M'
    - key: '-Xmx'
      value: '1200M'
    - key: '-XX:MaxDirectMemorySize='
      value: '2G'
    - key: '-XX:LogFile='
      value: '../sonatype-work/nexus3/log/jvm.log'
    - key: '-Dkaraf.data='
      value: '../sonatype-work/nexus3'
    - key: '-Djava.io.tmpdir='
      value: '../sonatype-work/nexus3/tmp'

## Elasticsearch customization

You can override the cluster routing allocation parameters with this kind of arborescence :

    cluster_routing_allocation:
      disk:
        watermark:
          low: 5gb

## License

MIT

## Author Information

This role was created in 2016 by Olivier Locard on the behalf of Deveryware.

