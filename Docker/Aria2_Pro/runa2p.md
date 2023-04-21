# Run Aria 2 Pro on Docker

## Aria2-Pro by P3TERX

- Change <TOKEN> to your own for RPC

```dockerfile
docker run -d \
    --name aria2-pro \
    --restart unless-stopped \
    --log-opt max-size=1m \
    -e PUID=$UID \
    -e PGID=$GID \
    -e UMASK_SET=022 \
    -e RPC_SECRET＝<TOKEN> \
    -e RPC_PORT=6800 \
    -p 6800:6800 \
    -e LISTEN_PORT=6888 \
    -p 6888:6888 \
    -p 6888:6888/udp \
    -v $PWD/aria2-config:/config \
    -v $PWD/aria2-downloads:/downloads \
    p3terx/aria2-pro
```

## AriaNg by P3TERX

- A WebUI for Settings

```dockerfile
docker run -d \
    --name ariang \
    --log-opt max-size=1m \
    --restart unless-stopped \
    -p 6880:6880 \
    p3terx/ariang
```