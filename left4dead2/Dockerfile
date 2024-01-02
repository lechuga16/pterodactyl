#
# Copyright (c) 2021 Matthew Penner
#
# Permission is hereby granted, free of charge, to any person obtaining a copy
# of this software and associated documentation files (the "Software"), to deal
# in the Software without restriction, including without limitation the rights
# to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
# copies of the Software, and to permit persons to whom the Software is
# furnished to do so, subject to the following conditions:
#
# The above copyright notice and this permission notice shall be included in all
# copies or substantial portions of the Software.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.
#

FROM        --platform=$TARGETOS/$TARGETARCH debian:bookworm-slim

LABEL       author="lechuga" maintainer="https://github.com/lechuga16/pterodactyl/left4dead2"

LABEL       org.opencontainers.image.source="https://github.com/lechuga16/pterodactyl/left4dead2"
LABEL       org.opencontainers.image.licenses=MIT

ENV         DEBIAN_FRONTEND=noninteractive

# Agrega la arquitectura i386
RUN dpkg --add-architecture i386

# Actualiza las listas de paquetes y realiza la actualización del sistema
RUN apt update
RUN apt upgrade -y

# Instala el paquete libc6:i386
RUN apt install -y libc6:i386

# Instala el paquete tar
RUN apt install -y tar

# Instala el paquete curl
RUN apt install -y curl

# Instala el paquete gcc
RUN apt install -y gcc

# Instala el paquete g++
RUN apt install -y g++

# Instala el paquete lib32gcc-s1
RUN apt install -y lib32gcc-s1

# Instala el paquete libgcc1
RUN apt install -y libgcc1

# Instala el paquete libcurl4-gnutls-dev:i386
RUN apt install -y libcurl4-gnutls-dev:i386

# Instala el paquete libssl3:i386 en reemplazo de libssl1.1:i386
RUN apt install -y libssl3:i386

# Instala el paquete libcurl4:i386
RUN apt install -y libcurl4:i386

# Instala el paquete lib32tinfo6
RUN apt install -y lib32tinfo6

# Instala el paquete libtinfo6:i386
RUN apt install -y libtinfo6:i386

# Instala el paquete lib32z1
RUN apt install -y lib32z1

# Instala el paquete lib32stdc++6
RUN apt install -y lib32stdc++6

# Instala el paquete libncurses5:i386
RUN apt install -y libncurses5:i386

# Instala el paquete libcurl3-gnutls:i386
RUN apt install -y libcurl3-gnutls:i386

# Instala el paquete libsdl2-2.0-0:i386
RUN apt install -y libsdl2-2.0-0:i386

# Instala el paquete iproute2
RUN apt install -y iproute2

# Instala el paquete gdb
RUN apt install -y gdb

# Instala el paquete libsdl1.2debian
RUN apt install -y libsdl1.2debian

# Instala el paquete libfontconfig1
RUN apt install -y libfontconfig1

# Instala el paquete telnet
RUN apt install -y telnet

# Instala el paquete net-tools
RUN apt install -y net-tools

# Instala el paquete netcat-openbsd en reemplazo de netcat
RUN apt install -y netcat-openbsd

# Instala el paquete tzdata
RUN apt install -y tzdata

# Instala el paquete numactl
RUN apt install -y numactl

# Instala el paquete tini
RUN apt install -y tini

# Crea el usuario "container"
RUN useradd -m -d /home/container container

## instala rcon
RUN cd /tmp/ \
RUN curl -sSL https://github.com/gorcon/rcon-cli/releases/download/v0.10.3/rcon-0.10.3-amd64_linux.tar.gz > rcon.tar.gz \
RUN tar xvf rcon.tar.gz \
RUN mv rcon-0.10.3-amd64_linux/rcon /usr/local/bin/

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

STOPSIGNAL SIGINT

COPY        --chown=container:container ./entrypoint.sh /entrypoint.sh
RUN         chmod +x /entrypoint.sh
ENTRYPOINT    ["/usr/bin/tini", "-g", "--"]
CMD         ["/entrypoint.sh"]