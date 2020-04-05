# docker-minecraft-server

## Install

1. Build image

```
docker image build -t minecraft_server:1.15.2 .
```

2. Create and run container

```
docker run --publish 25565:25565 --detach --name minecraft_server minecraft_server:1.15.2
```
