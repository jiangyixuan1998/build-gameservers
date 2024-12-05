# build-palworldserver
## Quick start

```bash
cd palworld && docker-compose up -d 
```
## how to update game server version ?
### make a dockerfile
```dockerfile
#use this Docker file rebuild this container
FROM jiangyixuan/palworldserver:latest
# RUN apt-get update  
# RUN apt-get install -y lib32gcc1 sudo wget ca-certificates curl software-properties-common dirmngr apt-transport-https lsb-release  net-tools xdg-user-dirs
# RUN mkdir -p /home/steam && useradd -d "/home/steam" steam && usermod  -s "/bin/bash" steam && usermod -aG sudo steam && chown -R steam:steam /home/steam
# USER steam
# WORKDIR /home/steam
# RUN cd /home/steam && pwd && wget https://steamcdn-a.akamaihd.net/client/installer/steamcmd_linux.tar.gz &&  tar -xvzf steamcmd_linux.tar.gz 
RUN /home/steam/steamcmd.sh +login anonymous +app_update 2394010 validate +quit
```

### then run docker build

```bash
docker build -t <registry>/<image_name>:<tag> .
```

### update palworld image version

```
#stop palworld game setting
cd palworld && docker-compose down
#change settings
vim $palworld/Config/LinuxServer/PalWorldSettings.ini
#start palworld game server
docker-compose up -d
```