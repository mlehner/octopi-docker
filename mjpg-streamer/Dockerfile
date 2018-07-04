FROM resin/rpi-raspbian:jessie

RUN apt-get update && apt-get install -y cmake libjpeg8-dev git build-essential libraspberrypi0 libraspberrypi-dev --no-install-recommends

RUN rm -rf /var/lib/apt/lists/* && rm -rf /tmp/* && rm -rf /var/tmp/*

RUN useradd -ms /bin/bash -G video mjpg

USER mjpg
WORKDIR /home/mjpg

RUN git clone https://github.com/jacksonliam/mjpg-streamer.git
WORKDIR /home/mjpg/mjpg-streamer/mjpg-streamer-experimental

RUN make

RUN rm -rf /tmp/* && rm -rf /var/tmp/*

EXPOSE 8080

ENV LD_LIBRARY_PATH .
ENTRYPOINT ["/home/mjpg/mjpg-streamer/mjpg-streamer-experimental/mjpg_streamer"]
CMD []
