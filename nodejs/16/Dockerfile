FROM        --platform=$TARGETOS/$TARGETARCH node:16-bookworm-slim

LABEL       author="Michael Parker" maintainer="parker@pterodactyl.io"

RUN         apt update \
            && apt -y install curl ffmpeg iproute2 git sqlite3 python3 tzdata ca-certificates dnsutils build-essential locales git sqlite3 libsqlite3-dev python3-dev zip tar libtool iputils-ping libnss3 tini proxychains* \
            && useradd -m -d /home/container container

RUN         npm install npm@9.8.1 typescript ts-node @types/node --location=global

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

STOPSIGNAL SIGINT

COPY        --chown=container:container ./../entrypoint.sh /entrypoint.sh
RUN         chmod +x /entrypoint.sh
ENTRYPOINT    ["/usr/bin/tini", "-g", "--"]
CMD         ["/entrypoint.sh"]
