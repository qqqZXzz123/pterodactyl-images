FROM        python:3.11-slim

LABEL       author="Software-noob" maintainer="admin@softwarenoob.com"
LABEL       org.opencontainers.image.source="https://github.com/Software-Noob/pterodactyl-images"
LABEL       org.opencontainers.image.licenses="MIT"

RUN         apt-get update \
            && apt-get -y install --no-install-recommends git gcc g++ ca-certificates dnsutils curl iproute2 ffmpeg procps locales proxychains4 \
            && apt-get clean \
            && rm -rf /var/lib/apt/lists/* \
            && locale-gen en_US.UTF-8

COPY ./requirements3_11.txt .

RUN pip install -r requirements3_11.txt \
&& pip install uvicorn \
&& pip install fastapi \
&& pip install schedule \
&& pip install requests \
&& pip install pydantic

ENV         LC_ALL=en_US.UTF-8
ENV         LANG=en_US.UTF-8
ENV         LANGUAGE=en_US.UTF-8

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

COPY        ./entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]
