# Dockerfile for installing OpenVPN.

FROM base
MAINTAINER Nicolas Cadou <ncadou@cadou.ca>

# It's not possible to use mknod inside a container with the default LXC
# template, so we untar it from this archive.
ADD dev-tun.tgz /dev/

RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get install -y openvpn
RUN apt-get clean
