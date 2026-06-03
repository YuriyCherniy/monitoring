# Ansible Runner

Run Ansible in a Docker container to deploy project:

```bash
docker compose run --rm runner main.yml
```

Run Ansible in a Docker container with particular tags

```bash
docker compose run --rm runner main.yml --tags setup_hosts
```

Run Ansible in a Docker container standalone playbook:

```bash
docker compose run --rm runner ./playbooks/ping-hosts.yml
```

## Requirements

- SSH key: `~/.ssh/id_ed25519`
