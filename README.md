# rustdesk-api

## docker-compose
```yaml
services:
  rustdesk-hbbs:
    container_name: rustdesk-hbbs
    image: rustdesk/rustdesk-server
    volumes:
      - ./root:/root
    network_mode: bridge
    ports:
      - 21115:21115
      - 21116:21116
      - 21116:21116/udp
    restart: always
    command: hbbs
  rustdesk-hbbr:
    container_name: rustdesk-hbbr
    image: rustdesk/rustdesk-server
    volumes:
      - ./root:/root
    network_mode: bridge
    ports:
      - 21117:21117
    restart: always
    command: hbbr
  rustdesk-api:
    container_name: rustdesk-api
    image: lechnolocy/rustdesk-api
    volumes:
      - ./data:/data
    network_mode: bridge
    ports:
      - 21114:80
    restart: always
```

## create account
```bash
curl -H 'Content-Type: application/json' -d '{"account":"xxx", "password": "xxxxx"}' http://<server>/admin/api/accounts
```

## update account
```bash
curl -H 'Content-Type: application/json' -X PUT -d '{"password": "xxxx", "nickname": "xxxx", "status": 0/1}' http://<server>/admin/api/accounts?account=xxx
```

## delete account
```bash
curl -H 'Content-Type: application/json' -X DELETE http://<server>/admin/api/accounts?account=xxx
```
