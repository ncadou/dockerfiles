# Dockerfile for installing pypicache.

# Adapted from https://github.com/fujin/dockerfiles/blob/master/pypicache

FROM ubuntu
MAINTAINER Nicolas Cadou <ncadou@cadou.ca>

ENV DEBIAN_FRONTEND noninteractive
ENV PYTHONPATH .

RUN echo 'deb http://archive.ubuntu.com/ubuntu precise main universe multiverse' > /etc/apt/sources.list
RUN apt-get update
RUN apt-get upgrade -y

RUN apt-get install -y git make python-all python-pip
RUN git clone https://github.com/micktwomey/pypicache.git /srv/pypicache
RUN cd /srv/pypicache && make init

EXPOSE 8080

CMD cd /srv/pypicache && make runserver
