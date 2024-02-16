# VPN

This repository contains WireGuard – a fast, modern and secure VPN tunnel.

## Requirements

Make sure that the [Base](https://gitlab.com/hueske-digital/services/base) is already set up and started.

## Setup instructions

Clone the code to your server:<br>
```
git clone git@gitlab.com:hueske-digital/services/vpn.git ~/services/vpn
```

Create environment file and fill up with your values:<br>
```
cd ~/services/vpn && cp .env.example .env && vim .env
```

Pull images and start the compose file:<br>
```
docker compose up -d
```

Set up port forwarding on your router for port `51820/udp` (configured in .env file).

Show your vpn client configuration:<br>

_QR-Code_
```
docker compose exec app /app/show-peer <Name or ID of Peer>
```

_File_
```
docker compose exec app cat /config/peer_MacBook/peer_<Name or ID of Peer>.conf
```

Use the qr-code or config file with [WireGuard clients](https://www.wireguard.com/install/).

## Other information

Update all container images and recreate them if new images are available:<br>
```
docker compose pull && docker compose up -d
```

Restart a single container:<br>
```
docker compose restart app
```

Shutdown all container of this compose file:<br>
```
docker compose down
```

Show and follow logs:<br>
```
docker compose logs -ft
```

Additional configuration:<br>
You can include any other docker config by using an additional [compose file](https://docs.docker.com/compose/extends/).
