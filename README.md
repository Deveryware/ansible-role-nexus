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

    nexus_download_url: 'https://download.sonatype.com/nexus/3/latest-unix.tar.gz' (Should be overwritten by 'https://download.sonatype.com/nexus/3/nexus-VERSION-linux-x86_64.tar.gz')
    nexus_checksum_format: 'sha512' (md5, sha1, sha256, sha512 available)
    nexus_checksum_url: "{{ nexus_checksum_format }}:{{ nexus_download_url }}.{{ nexus_checksum_format }}" (can be emptied to avoid checksum: '')
    nexus_application_port: 8081
    nexus_application_host: '0.0.0.0'
    nexus_user: 'nexus'
    nexus_group: 'nexus'
    nexus_scripts_allowCreation: false

## Advanced variables

**nexus_context_path:** '/' . The <context> is added almost like that: http://<server>:<port>/<context>

**nexus_java_home:** '/usr/lib/jvm/java-8-oracle'

**nexus_cleanup:** 'true' or 'false'. Enable to remove the downloaded tar.gz file.

**nexus_update:** 'true' or 'false'. Enable to update an installed nexus.

**nexus_service_restart:** 'always'. Enable de configure the _systemd.service_ `Restart` (no, on-success, on-failure, on-abnormal, on-watchdog, on-abort).

**nexus_scripts_allowCreation:** 'true' or 'false'. Default is false. Enable the creation of file on Nexus server via Nexus API (/service/rest/v1/script).

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

