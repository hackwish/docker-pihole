# Docker PI Hole

This repo contains base files to depoy PI Hole Server.

## How-to

- Clone the repo

### Gluetun

Configure Gluetun in a local `.env` file (it is ignored by Git) before starting the Compose services. Set `VPN_SERVICE_PROVIDER`, the provider-specific VPN credentials (`OPENVPN_USER` and `OPENVPN_PASSWORD` or the corresponding WireGuard variables), `HTTPPROXY_USER`, `HTTPPROXY_PASSWORD`, `SOCKS5_USER`, `SOCKS5_PASSWORD`, and `GLUETUN_API_KEY`. The API key is used by both Gluetun and its WebUI. Use strong, distinct proxy credentials and a protected API key; do not commit real credentials.

The WebUI is available at `http://localhost:3000`; the HTTP and SOCKS5 proxies are bound to `127.0.0.1` on ports `8888` and `1080`. DNS on port `53` and the control API on port `8000` are available only to other containers on the Compose network; port `53` is already published by Pi-hole. Do not bind the WebUI to a public interface without adding an authentication and TLS layer.

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
nameserver 208.67.222.222
nameserver 208.67.220.220
```

### 2. Run

```sh
docker compose pull && docker compose down && docker compose up -d --remove-orphans
```
