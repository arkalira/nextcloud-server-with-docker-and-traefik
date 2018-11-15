# Nextcloud with docker compose and Traefik
## Prerequisites

- In order to use this compose file (docker-compose.yml) you must have:

- docker: https://docs.docker.com/install/
- docker-compose: https://docs.docker.com/compose/install/

## How to use this contents
### Clone this repository

```
git clone https://github.com/arkalira/Nextcloud_with_docker_compose
```

- Create 3 folders:

```
 mkdir -p /opt/nextcloud /opt/mysql /opt/traefik
```

- Make a copy of traefik folders content of this repo to /opt/traefik.

```
cp ./traefik/* /opt/traefik
```

- Change mask for "acme.json" file: 600

```
chmod 600 /opt/traefik/acme.json
```

### Configuration for Nextcloud using Traefik WebProxy

### Network name

- NETWORK=proxy

```
docker network create proxy
```

## Start your containers

```
docker-compose up --build -d
```

## Systemd Units

- Copy the content of Systemd units folder to /etc/systemd/system/

```
cp -r systemd units/* /etc/systemd/system/ 
systemctl enable proxy.service nextcloud.service mysql-docker.service adminer.service
systemctl status proxy.service nextcloud.service mysql-docker.service adminer.service
```
