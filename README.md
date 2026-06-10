## In this project, Ansible is run within a Docker container. You can run it using Docker Compose.

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
docker compose run --rm runner ansible-vault create ./group_vars/all/vault.yml
```

**Example of `vault.yml` content:**
```yaml
vault_grafana_admin_user: <login>
vault_grafana_admin_password: "<password>"
```

## Requirements

- SSH key: `~/.ssh/id_ed25519`
