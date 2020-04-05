## Node Exporter Ansible Role

[![Build Status](https://travis-ci.org/bilalcaliskan/node_exporter-ansible-role.svg?branch=master)](https://travis-ci.org/bilalcaliskan/node_exporter-ansible-role)

Installs and configures node-exporter daemon on RHEL/CentOS 7/8 instances.

## Requirements

No special requirements; note that this role requires root access, so either run it in a playbook with a global `become: yes`, or invoke the role in your playbook like:

      - hosts: all
        become: true
        roles:
          - role: bilalcaliskan.node_exporter

## Role Variables

See the default values in 'defaults/main.yml'. You can overwrite them in 'vars/main.yml' if neccessary.

## Dependencies

None

## Example Playbook

      - hosts: all
        become: true
        vars_files:
          - vars/main.yml
        roles:
          - { role: bilalcaliskan.node_exporter }

*Inside `vars/main.yml`*:

        version: 0.18.1
        download_url: https://github.com/prometheus/node_exporter/releases/download/v{{ version }}/node_exporter-{{ version }}.linux-amd64.tar.gz
        base_dir_path: /opt
        file_path: "{{ base_dir_path }}/node_exporter-{{ version }}.linux-amd64.tar.gz"
        folder_path: "{{ base_dir_path }}/node_exporter-{{ version }}.linux-amd64"
        port: 9100
        enable_systemd_collector: true
        user: prometheus
        group: prometheus

## Playbook for uninstall

      - hosts: all
        become: true
        vars_files:
          - vars/main.yml
        roles:
          - { role: bilalcaliskan.node_exporter }

*Inside `vars/main.yml`*:

        install_node_exporter: false

## License

MIT / BSD
