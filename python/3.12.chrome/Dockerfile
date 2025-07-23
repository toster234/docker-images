FROM        --platform=$TARGETOS/$TARGETARCH python:3.12-slim-bookworm

LABEL       author="toster.dev" maintainer="contact@toster.dev"

RUN         apt update \
            && apt -y install git gcc g++ ca-certificates dnsutils curl iproute2 ffmpeg procps tini \
               chromium chromium-driver \
            && ln -s /usr/bin/chromium /usr/bin/google-chrome \
            && useradd -m -d /home/container container \
            && apt clean \
            && rm -rf /var/lib/apt/lists/*

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

STOPSIGNAL SIGINT

COPY        --chown=container:container ./../entrypoint.sh /entrypoint.sh
RUN         chmod +x /entrypoint.sh
ENTRYPOINT  ["/usr/bin/tini", "-g", "--"]
CMD         ["/entrypoint.sh"]
