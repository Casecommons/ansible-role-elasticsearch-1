# Ansible Role: Elasticsearch

[![Build Status](https://travis-ci.org/geerlingguy/ansible-role-elasticsearch.svg?branch=master)](https://travis-ci.org/geerlingguy/ansible-role-elasticsearch)

An Ansible Role that installs Elasticsearch (2.x on Debian, see `tasks/setup-Debian.yml` ) on RedHat/CentOS or Debian/Ubuntu.

## Requirements

Requires at least Java 7 (Java 8+ preferred). See [`geerlingguy.java`](https://github.com/geerlingguy/ansible-role-java#example-playbook-install-openjdk-8) role instructions for installing OpenJDK 8.

## Role Variables
Available variables are listed below, along with default values (see `defaults/main.yml`):

    elasticsearch_package_name: 'elasticsearch=2.3.5'

The exact name of the package to be installed (Debian only). Useful for installing versions besides the latest 2.x (2.4). Defaults to `elasticsearch`.

    elasticsearch_network_host: localhost

Network host to listen for incoming connections on. By default we only listen on the localhost interface. Change this to the IP address to listen on a specific interface, or `0.0.0.0` to listen on all interfaces.

    elasticsearch_http_port: 9200

The port to listen for HTTP connections on.

    elasticsearch_script_inline: true
    elasticsearch_script_indexed: true

Whether to allow inline scripting against ElasticSearch. You should read the following link as there are possible security implications for enabling these options: [Enable Dynamic Scripting](https://www.elastic.co/guide/en/elasticsearch/reference/current/modules-scripting.html#enable-dynamic-scripting). Available options include: `true`, `false`, and `sandbox`.

    elasticsearch_plugins:
      - cloud-aws

List of plugins to install. Defaults to an empty list.



## Dependencies

  - geerlingguy.java

## Example Playbook

    - hosts: search
      roles:
        - geerlingguy.java
        - geerlingguy.elasticsearch

## License

MIT / BSD

## Author Information

This role was created in 2014 by [Jeff Geerling](https://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).
