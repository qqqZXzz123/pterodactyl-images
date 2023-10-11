FROM        python:3.8-slim

LABEL       author="Software-noob" maintainer="admin@softwarenoob.com"
LABEL       org.opencontainers.image.source="https://github.com/Software-Noob/pterodactyl-images"
LABEL       org.opencontainers.image.licenses="MIT"

RUN         apt-get update \
            && apt-get -y install --no-install-recommends unzip wget git gcc g++ ca-certificates dnsutils curl iproute2 ffmpeg procps locales \
            && apt-get clean \
            && rm -rf /var/lib/apt/lists/* \
            && locale-gen en_US.UTF-8

COPY ./requirements.txt .

RUN pip install -r requirements.txt

RUN wget https://github.com/kiki7000/discord.py-components/archive/refs/tags/2.1.2.zip -O discord.py-components-2.1.2.zip \
&& unzip discord.py-components-2.1.2.zip -d .. \
&& cd discord.py-components-2.1.2 \
&& pip install .

ENV         LC_ALL=en_US.UTF-8
ENV         LANG=en_US.UTF-8
ENV         LANGUAGE=en_US.UTF-8

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

COPY        ./entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]
