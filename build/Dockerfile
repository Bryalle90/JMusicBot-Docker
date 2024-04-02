# Use phusion/baseimage as base image. To make your builds reproducible, make
# sure you lock down to a specific version, not to `latest`!
# See https://github.com/phusion/baseimage-docker/blob/master/Changelog.md for
# a list of version numbers.
FROM phusion/baseimage:jammy-1.0.2

CMD ["./run"]

RUN groupadd -r musicbot && \
    useradd -g musicbot musicbot

RUN apt update &&\
    apt install -y wget apt-transport-https gpg &&\
    wget -qO - https://packages.adoptium.net/artifactory/api/gpg/key/public | gpg --dearmor | tee /etc/apt/trusted.gpg.d/adoptium.gpg > /dev/null &&\
    echo "deb https://packages.adoptium.net/artifactory/deb $(awk -F= '/^VERSION_CODENAME/{print$2}' /etc/os-release) main" | tee /etc/apt/sources.list.d/adoptium.list &&\
    apt update &&\
    apt install -y temurin-11-jdk jq &&\
    apt clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* &&\
    mkdir -p /jmusicbot

WORKDIR /jmusicbot

COPY scripts/run /jmusicbot/run

RUN chown -R musicbot:musicbot /jmusicbot && \
    chmod +x /jmusicbot/run

USER musicbot