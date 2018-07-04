FROM resin/rpi-raspbian:jessie

ENV octoprint_version 1.3.8

RUN apt-get update && apt-get install -y python-pip python-dev python-setuptools virtualenv git libyaml-dev build-essential libav-tools --no-install-recommends

RUN rm -rf /var/lib/apt/lists/* && rm -rf /tmp/* && rm -rf /var/tmp/*

RUN useradd -ms /bin/bash -G tty,dialout octopi

USER octopi
WORKDIR /home/octopi
RUN virtualenv venv
RUN /home/octopi/venv/bin/pip install pip --upgrade

RUN mkdir ~/.octoprint
RUN git clone --depth 1 https://github.com/foosel/OctoPrint.git --branch ${octoprint_version}

WORKDIR /home/octopi/OctoPrint
RUN /home/octopi/venv/bin/python setup.py install

RUN rm -rf /tmp/* && rm -rf /var/tmp/*

EXPOSE 5000

ENTRYPOINT ["/home/octopi/venv/bin/octoprint"]
CMD ["serve"]
