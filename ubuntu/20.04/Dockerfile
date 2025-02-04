FROM  --platform=$TARGETOS/$TARGETARCH ubuntu:20.04

LABEL author="toster234" maintainer="contact@toster.dev"

ENV   DEBIAN_FRONTEND noninteractive

## add container user
RUN   useradd -m -d /home/container -s /bin/bash container

## update base packages
RUN   apt update \
        &&   apt upgrade -y

## install dependencies
RUN   apt install -y gcc g++ libgcc1 lib32gcc1 libc++-dev gdb libc6 git wget curl tar zip unzip binutils xz-utils liblzo2-2 cabextract iproute2 net-tools netcat telnet libatomic1 libsdl1.2debian libsdl2-2.0-0 \
        libfontconfig libicu66 icu-devtools libunwind8 libssl1.1 sqlite3 libsqlite3-dev libmariadb-dev libzip5 locales ffmpeg apt-transport-https init-system-helpers \
        libcurl3-gnutls libjsoncpp1 libleveldb1v5 liblua5.1-0 libluajit-5.1-2 libsqlite3-0 libfluidsynth2 bzip2 zlib1g


## configure locale
RUN   update-locale lang=en_US.UTF-8 \
        &&   dpkg-reconfigure --frontend noninteractive locales

WORKDIR /home/container

COPY  ./entrypoint.sh /entrypoint.sh
CMD   [ "/bin/bash", "/entrypoint.sh" ]
