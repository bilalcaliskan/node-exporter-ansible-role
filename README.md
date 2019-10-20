## Role Name

Installs and configures Node Exporter daemon on RHEL/CentOS 7/8 servers.

## Requirements

No special requirements; note that this role requires root access, so either run it in a playbook with a global `become: yes`, or invoke the role in your playbook like:

      - hosts: all
        roles:
          - role: bilalcaliskan.node_exporter
            become: yes

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

        version: 0.18.1
        download_url: https://github.com/prometheus/node_exporter/releases/download/v{{ version }}/node_exporter-{{ version }}.linux-amd64.tar.gz
        base_dir_path: /opt
        file_path: "{{ base_dir_path }}/node_exporter-{{ version }}.linux-amd64.tar.gz"
        folder_path: "{{ base_dir_path }}/node_exporter-{{ version }}.linux-amd64"
        port: 9100
        enable_systemd_collector: true
        user: prometheus
        group: prometheus

## Dependencies

None

## Example Playbook

      - hosts: all
        become: yes
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

## License

MIT / BSD
