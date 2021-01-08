## Node Exporter Ansible Role

[![Build Status](https://travis-ci.org/bilalcaliskan/node_exporter-ansible-role.svg?branch=master)](https://travis-ci.org/bilalcaliskan/node_exporter-ansible-role)

Installs and configures node-exporter to expose node metrics to Prometheus on RHEL/CentOS 7/8 instances.

## Requirements

No special requirements; note that this role requires root access, so either run it in a playbook with a global `become: true`, or invoke the role in your playbook like:

```yaml
- hosts: all
  become: true
  roles:
    - role: bilalcaliskan.node_exporter
```

### Role Variables
See the default values in [defaults/main.yml](defaults/main.yml). You can overwrite them in [vars/main.yml](vars/main.yml) if neccessary or you can set them while running playbook.

> Please note that this role will ensure that `firewalld` systemd service on your servers are started and enabled by default. If you want to stop and disable `firewalld` service, please modify below variable as false when running playbook:  
> ```yaml  
> firewalld_enabled: false

## Dependencies

None

### Example Playbook File For Installation

```yaml
- hosts: all
  become: true
  roles:
    - role: bilalcaliskan.node_exporter
      vars:
        exporter_port: 9092
        install_node_exporter: true
        version: 1.0.1
```

You can also override default variables inside [vars/main.yml](vars/main.yml)*:
```yaml
version: 1.0.1
```

### Example Playbook File For `Ununinstallation`

```yaml
- hosts: all
  become: true
  roles:
    - role: bilalcaliskan.node_exporter
      vars:
        install_node_exporter: false
```

### License

MIT / BSD
