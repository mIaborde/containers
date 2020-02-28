# Containers

- [Containers](#containers)
  - [Get started with Docker](#get-started-with-docker)
    - [Install Docker & Docker-compose](#install-docker--docker-compose)
    - [Useful commands](#useful-commands)
    - [Visual Studio Code Extension](#visual-studio-code-extension)
  - [Gitea](#gitea)
  - [MariaDB](#mariadb)
  - [LEMP](#lemp)
  - [Postgres](#postgres)

## Get started with Docker

### Install Docker & Docker-compose

follow official method for your OS :

- **Docker**: https://docs.docker.com/install/linux/docker-ce/ubuntu/
- **Docker-compose**: https://docs.docker.com/compose/install/

### Useful commands

```bash
# list all running containers
docker ps -a
# list all docker images
docker images
# start shell in one container
docker exec -ti CONTAINER_ID /bin/sh
# remove the docker container with container id mentioned
docker rm CONTAINER_ID
# remove image with image id mentioned
docker rmi IMAGE_ID
```

> All commands in [official documentation](https://docs.docker.com/engine/reference/commandline/docker/)

### Visual Studio Code Extension

To integrate Docker into Visual Studio Code you can install [Docker extension](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker) from marketplace.

## Gitea

| services | db                    | app                   |
| -------- | --------------------- | --------------------- |
| image    | mariadb:latest        | gitea:latest          |
| port     | http://localhost:3306 | http://localhost:3000 |

```bash
# from the directory where you want to place the containerized gitea server
git clone https://github.com/miaborde/containers \
&& mv containers/gitea ./gitea \
&& rm -rf containers \
&& cd gitea
# edit the .env file according to your needs, then :
docker-compose up -d
```

## MariaDB

| services | db                    | admin                 |
| -------- | --------------------- | --------------------- |
| image    | mariadb:latest        | phpmyadmin/phpmyadmin |
| port     | http://localhost:3306 | http://localhost:3307 |

```bash
# from the root of your project
git clone https://github.com/miaborde/containers \
&& mv containers/mariadb/* . \
&& rm -rf containers
# edit the .env file according to your needs, then :
docker-compose up -d
```

## LEMP

| services | web                   | php              | db                    | admin                 |
| -------- | --------------------- | ---------------- | --------------------- | --------------------- |
| image    | nginx:stable-alpine   | php:7-fpm-alpine | mariadb:latest        | phpmyadmin/phpmyadmin |
| port     | http://localhost:8000 | x:8001           | http://localhost:3306 | http://localhost:3307 |

```bash
# from the directory where you want to place the containerized LEMP server
git clone https://github.com/miaborde/containers \
&& mv containers/lemp ./lemp \
&& rm -rf containers \
# edit the .env file according to your needs, then :
docker-compose up -d
```

> Just place your projects in the **web** folder so they are accessible on http://localhost:8000/yourProject.
> MariaDB is ready to go, just create a new database via PhpMyAdmin.

## Postgres

| services | api                   | pwa                   | db                    |
| -------- | --------------------- | --------------------- | --------------------- |
| image    | node:lts-alpine       | nginx:stable-alpine   | postgres:alpine       |
| port     | http://localhost:3001 | http://localhost:3000 | http://localhost:3002 |

```bash
# from the root of your project
git clone https://github.com/miaborde/containers \
&& mv containers/postgres/* . \
&& rm -rf containers
# edit the .env file according to your needs, then :
docker-compose up -d
```
