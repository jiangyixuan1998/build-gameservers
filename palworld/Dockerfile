FROM ubuntu:20.04
RUN apt-get update  
RUN apt-get install -y lib32gcc1 sudo wget ca-certificates curl software-properties-common dirmngr apt-transport-https lsb-release  net-tools xdg-user-dirs
RUN mkdir -p /home/steam && useradd -d "/home/steam" steam && usermod  -s "/bin/bash" steam && usermod -aG sudo steam && chown -R steam:steam /home/steam
USER steam
WORKDIR /home/steam
RUN cd /home/steam && pwd && wget https://steamcdn-a.akamaihd.net/client/installer/steamcmd_linux.tar.gz &&  tar -xvzf steamcmd_linux.tar.gz 
RUN /home/steam/steamcmd.sh +login anonymous +app_update 2394010 validate +quit
