# AlmaLinux Container image for Ansible Testing

[![Build](https://github.com/bpadair32/docker-image-alma-systemd/actions/workflows/build.yml/badge.svg)](https://github.com/bpadair32/docker-image-alma-systemd/actions/workflows/build.yml)

Systemd AlmaLinux container images for testing roles and playbooks with molecule.

## Available images

Images are built weekly via Github Actions and can be downloaded from the Github Package Repository.

These tags are available. They are updated once a week or on merges to main.

| Tag | Base Image |
|-----|------------|
| `ghcr.io/bpadair32/docker-image-alma-systemd:alma9` | AlmaLinux 9 |
| `ghcr.io/bpadair32/docker-image-alma-systemd:alma10` | AlmaLinux 10 |

## Usage

- [Install Docker](https://docs.docker.com/engine/installation/).
- Pull the image from GitHub Container Repository:

```bash
# For AlmaLinux 9
docker pull ghcr.io/bpadair32/docker-image-alma-systemd:alma9

# For AlmaLinux 10
docker pull ghcr.io/bpadair32/docker-image-alma-systemd:alma10
```

- Run the container via Docker:

```bash
# AlmaLinux 9
docker run --detach --privileged --volume=/sys/fs/cgroup:/sys/fs/cgroup:rw --cgroupns=host --volume=$(pwd):/etc/ansible/roles/role_to_test:ro ghcr.io/bpadair32/docker-image-alma-systemd:alma9

# AlmaLinux 10
docker run --detach --privileged --volume=/sys/fs/cgroup:/sys/fs/cgroup:rw --cgroupns=host --volume=$(pwd):/etc/ansible/roles/role_to_test:ro ghcr.io/bpadair32/docker-image-alma-systemd:alma10
```

- Run ansible commands inside the container:

  a. `docker exec --tty [container_id] env TERM=xterm ansible --version`

  b. `docker exec --tty [container_id] env TERM=xterm ansible-playbook /path-to/playbook.yml --syntax-check` 

## Authors

Built and maintained by Brad Adair, brad@adair.tech.
Inspired by GeerlingGuy, https://github.com/geerlingguy.
