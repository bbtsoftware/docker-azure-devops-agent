# Docker Azure DevOps agent

Docker image to run an Azure DevOps agent.

## Information

| Service | Stats                                                                                     |
|---------|-------------------------------------------------------------------------------------------|
| Docker  | [![Build](https://img.shields.io/docker/cloud/build/bbtsoftwareag/azure-devops-agent.svg?style=flat-square)](https://hub.docker.com/r/bbtsoftwareag/azure-devops-agent/builds) [![Pulls](https://img.shields.io/docker/pulls/bbtsoftwareag/azure-devops-agent.svg?style=flat-square)](https://hub.docker.com/r/bbtsoftwareag/azure-devops-agent) [![Stars](https://img.shields.io/docker/stars/bbtsoftwareag/azure-devops-agent.svg?style=flat-square)](https://hub.docker.com/r/bbtsoftwareag/azure-devops-agent) [![Automated](https://img.shields.io/docker/cloud/automated/bbtsoftwareag/azure-devops-agent.svg?style=flat-square)](https://hub.docker.com/r/bbtsoftwareag/azure-devops-agent/builds) |
| GitHub  | [![Last commit](https://img.shields.io/github/last-commit/bbtsoftware/docker-azure-devops-agent.svg?style=flat-square)](https://github.com/bbtsoftware/docker-azure-devops-agent/commits/master) [![Issues](https://img.shields.io/github/issues-raw/bbtsoftware/docker-azure-devops-agent.svg?style=flat-square)](https://github.com/bbtsoftware/docker-azure-devops-agent/issues) [![PR](https://img.shields.io/github/issues-pr-raw/bbtsoftware/docker-azure-devops-agent.svg?style=flat-square)](https://github.com/bbtsoftware/docker-azure-devops-agent/pulls) [![Size](https://img.shields.io/github/repo-size/bbtsoftware/docker-azure-devops-agent.svg?style=flat-square)](https://github.com/bbtsoftware/docker-azure-devops-agent/) [![License](https://img.shields.io/badge/license-MIT-blue.svg?style=flat-square)](https://github.com/bbtsoftware/docker-azure-devops-agent/blob/master/LICENSE) |

## General

| Topic  | Description                                                                  |
|--------|------------------------------------------------------------------------------|
| Image  | See [Docker Hub](https://hub.docker.com/r/bbtsoftwareag/azure-devops-agent). |
| Source | See [GitHub](https://github.com/bbtsoftware/docker-azure-devops-agent).      |

## Installation

```sh
docker pull bbtsoftwareag/azure-devops-agent
```

### Tags

| Tag                                   | Description                                                     | Size                                                                                                                                                       |
|---------------------------------------|-----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ubuntu-16.04-azure-devops-server-2019 | Azure DevOps agent on Ubuntu 16.04 for Azure DevOps Server 2019 | ![Size](https://shields.beevelop.com/docker/image/image-size/bbtsoftwareag/azure-devops-agent/ubuntu-16.04-azure-devops-server-2019.svg?style=flat-square) |

### Configuration

These environment variables are supported:

| ENV field      | Description                                                  |
|----------------|--------------------------------------------------------------|
| TZ             | Timezone to set, e.g. `Europe/Zurich`.                       |
| AZP_URL        | The URL of the Azure DevOps or Azure DevOps Server instance. |
| AZP_TOKEN      | Personal Access Token (PAT) granting access to `AZP_URL`.    |
| AZP_AGENT_NAME | Agent name (default value: the container hostname).          |
| AZP_POOL       | Agent pool name (default value: `Default`).                  |
| AZP_WORK       | Work directory (default value: `_work`).                     |

### Supported Azure Pipeline tasks

The following Azure Pipeline tasks are supported:

* Archive Files
* Extract Files

## Samples

### docker-compose

```yaml
version: '3.7'

services:
  app:
    image: bbtsoftwareag/azure-devops-agent:ubuntu-16.04-azure-devops-server-2019
    environment:
      - TZ=Europe/Zurich
      - AZP_URL=https://tfs.tempuri.org
      - AZP_TOKEN=tmk6je86ta8hvis7uk9csm9sncwrnuhjaxeqg5g6pe732cucby
      - AZP_AGENT_NAME=my-agent01
    networks:
      - default
```

### docker run

```sh
docker run -d \
  -e TZ=Europe/Zurich \
  -e AZP_URL=https://tfs.tempuri.org \
  -e AZP_TOKEN=tmk6je86ta8hvis7uk9csm9sncwrnuhjaxeqg5g6pe732cucby \
  -e AZP_AGENT_NAME=my-agent01 \
  bbtsoftwareag/azure-devops-agent:ubuntu-16.04-azure-devops-server-2019
```