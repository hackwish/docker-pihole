# Docker PI Hole

This repo contains base files to depoy PI Hole Server.

## How-to

- Clone the repo

## Previous steps

### 0. On Ubuntu

```sh
sudo systemctl stop systemd-resolved.service

sudo systemctl disable systemd-resolved.service
```

### 1. Change the DNS

- Edit /etc/resolv.conf

```sh
nameserver 1.1.1.1
nameserver 1.0.0.1
nameserver 8.8.8.8
nameserver 8.8.4.4
nameserver 9.9.9.9
nameserver 208.67.222.222
nameserver 208.67.220.220
```

### 2. Run

```sh
docker-compose up -d
```
