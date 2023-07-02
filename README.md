# Prometheus-Stack Role

A role for installing and configuring Prometheus Stack.

## Requirements

- Docker installation is required.

## Role Variables

The following variables can be set for this role:

- `Prometheus_Docker_root`: The root folder required for Prometheus Stack Docker farm.
- `prometheus_package_version`: The version of Prometheus package.
- `node_exporter_targets`: A list of targets for the Node Exporter.
- `cadvisor_exporter_targets`: A list of targets for the cAdvisor Exporter.
- `nginx_exporter_targets`: A list of targets for the Nginx Exporter.
- `postgresql_exporter_targets`: A list of targets for the PostgreSQL Exporter.
- `Promtheus_archive_password`: Password for the Prometheus Stack archive.
- `admin_user`: Username for administrative purposes.
- `admin_password`: Password for the administrative user.
- `admin_password_hash`: Hashed password for the administrative user.
- `telegram_token`: Token for Telegram integration.
- `telegram_chatid`: Chat ID for Telegram integration.

## Dependencies

No external role dependencies.

## Example Playbook

Here's an example of how to use the Prometheus-Stack Role:

```yaml
- hosts: monitoring
  gather_facts: yes
  become: yes
  roles:
    - role: Prometheus-Stack
      vars:
        Prometheus_Docker_root: /opt/morsh_monit
        prometheus_package_version: "1.2.0"
        node_exporter_targets:
          - nodeexporter:9100
        cadvisor_exporter_targets:
          - cadvisor:8080
        nginx_exporter_targets:
          - nginx:10254
        postgresql_exporter_targets:
          - postgresql:12938
        Promtheus_archive_password: "your_prometheus_archive_password"
        admin_user: "admin"
        admin_password: "admin123"
        admin_password_hash: "$6$zqKl8Jzv7c6hMvZ7$AQTB1I1L1uBT8EG.Rc.c22P7Cr5CSoeRJTYhMK4UStZJit0Dvg.cHzLyA77zWtnyRZN2.KKX52xP4guy7.tNb."
        telegram_token: "your_telegram_token"
        telegram_chatid: "your_telegram_chatid"
```

# License

BSD