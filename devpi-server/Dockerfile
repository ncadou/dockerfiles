# Dockerfile for installing devpi-server.
#
# https://pypi.python.org/pypi/devpi-server

FROM ubuntu
MAINTAINER Nicolas Cadou <ncadou@cadou.ca>

ENV PYTHONPATH .

RUN echo 'deb http://archive.ubuntu.com/ubuntu precise main universe' > /etc/apt/sources.list
RUN apt-get update
RUN apt-get upgrade -y

RUN apt-get install -y python-virtualenv
RUN adduser --gecos 'devpi user' --disabled-password devpi
RUN su - devpi -c 'virtualenv venv'
RUN su - devpi -c 'venv/bin/pip install devpi'
ADD start /usr/local/bin/

EXPOSE 3141

ENTRYPOINT ["/usr/local/bin/start"]
CMD [""]
