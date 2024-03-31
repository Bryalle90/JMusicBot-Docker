# Use phusion/baseimage as base image. To make your builds reproducible, make
# sure you lock down to a specific version, not to `latest`!
# See https://github.com/phusion/baseimage-docker/blob/master/Changelog.md for
# a list of version numbers.
FROM phusion/baseimage:jammy-1.0.2

RUN apt-get update &&\
    apt-get install -y openjdk-11-jdk &&\
    apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* &&\
    mkdir -p /etc/service/jmusicbot

COPY scripts/run /etc/service/jmusicbot/run