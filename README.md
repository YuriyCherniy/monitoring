# Monitoring Stack with Ansible

To start this project, you need two hosts with Ubuntu. The first one must have 1 GB RAM (app server), and the second one must have 2 GB RAM (monitoring server). On both hosts, an ansible user must be configured. If the hosts are created by a cloud provider, you can configure the ansible user with the example file .vm-config.yml.example.

Before deployment, update the inventory `ansible/inventory.yml` with your real host IP addresses.

All commands below should be run from the `ansible/` directory.

## In this project, Ansible runs inside a Docker container. You can run it using Docker Compose.

Examples:

Build the Ansible Docker image:
```bash
docker compose build
```

Run the ping playbook to check connectivity to hosts:
```bash
docker compose run --rm runner ansible-playbook ./playbooks/ping-hosts.yml --ask-vault-pass
```

Deploy the project by running the main playbook:
```bash
docker compose run --rm runner ansible-playbook main.yml --ask-vault-pass
```

Run a playbook with specific tags:
```bash
docker compose run --rm runner ansible-playbook main.yml --tags setup_hosts --ask-vault-pass
```

## Before deploying the project, you must create a `vault.yml` file with secrets. Run the following command (it will prompt for a password and open the Vim editor):

```bash
docker compose run --rm runner ansible-vault create 
```

**Example of `vault.yml` content:**
```yaml
vault_grafana_admin_user: <login>
vault_grafana_admin_password: "<password>"

vault_prometheus_admin_user: <login>
vault_prometheus_admin_password: "<password>"

vault_node_exporter_admin_user: <login>
vault_node_exporter_admin_password: "<password>"
```
Or you can use the existing ./group_vars/all/vault.yml file with login: admin and password: 0000 for all services.
