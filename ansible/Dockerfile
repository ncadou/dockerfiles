# Dockerfile to make an image that can run ansible playbooks.
#
# http://www.ansibleworks.com/

FROM ubuntu
MAINTAINER Nicolas Cadou <ncadou@cadou.ca>

RUN echo 'deb http://archive.ubuntu.com/ubuntu precise main universe' > /etc/apt/sources.list
RUN apt-get update && apt-get upgrade -y && apt-get clean

RUN apt-get install -y python-apt python-jinja2 python-paramiko python-pip python-yaml && apt-get clean
RUN pip install ansible
