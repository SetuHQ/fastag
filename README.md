# Gondolin

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
# Table of Contents

- [Table of Contents](#table-of-contents)
- [Getting started](#getting-started)
- [Developer Setup](#developer-setup)
  - [1. Fill in configuration in `docker-compose.yml`](#1-fill-in-configuration-in-docker-composeyml)
  - [2. Bring up the setup](#3-bring-up-the-setup)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Getting started

To get started with gondolin, you'd need to install the following tools:

1. [Docker](https://docs.docker.com/get-docker/)
2. [Docker compose](https://docs.docker.com/compose/install/)

The setup consists of a postgresql database and a docker containerized service delivered by Setu.

# Developer Setup

To bring up a local developer setup,

## 1. Fill in configuration in `docker-compose.yml`

- Fill in the switch server credentials:

```bash
      # Switch server credentials
      - HTTP_PROXY=http://<user>:<password>@<switch-server>.setu.co:<port>
      - ALL_PROXY=http://<user>:<password>@<switch-server>.setu.co:<port>
      - END_POINT=<Fastag endpoint>
```

- Fill other credentials as communicated.

## 2. Bring up the setup

```bash
docker-compose up
```

# Docker Best practices

1. Resource constraints: Configure memory and cpu resources when being run along with other docker containers.
2. PID limits: Tune container pids limit. Ex: `--pid="100"`
3. IPC Mode: Inter process communication mode. Set it to `private` when possible. Ex: `--ipc="private"` 
4. Use `127.0.0.1` if possible for the docker host name instead of `0.0.0.0`.
5. Disable container processes from gaining more privileges. Ex: `--security-opt="no-new-privileges"` 

## References
```buildoutcfg
https://docs.docker.com/compose/compose-file/compose-file-v2/
https://docs.docker.com/engine/reference/run/  
https://dev-sec.io/baselines/docker/
```
