FROM resin/rpi-raspbian:jessie

RUN apt-get update && apt-get install -y libraspberrypi0 --no-install-recommends
RUN apt-get update && apt-get install -y vlc-nox --no-install-recommends

RUN useradd -ms /bin/bash -G video vlc

RUN rm -rf /var/lib/apt/lists/* && rm -rf /tmp/* && rm -rf /var/tmp/*

USER vlc
WORKDIR /home/vlc
