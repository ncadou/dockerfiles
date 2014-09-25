# Base OpenVPN client image.

FROM debian:jessie
MAINTAINER Nicolas Cadou <ncadou@cadou.ca>

RUN apt-get update && \
    apt-get install -y dnsutils iputils-ping openvpn traceroute unzip && \
    apt-get clean

# Private Internet Access client.
RUN mkdir -p /usr/local/share/openvpn/providers/pia
ADD https://www.privateinternetaccess.com/openvpn/openvpn.zip \
    /usr/local/share/openvpn/providers/pia/
RUN cd /usr/local/share/openvpn/providers/pia && \
    unzip -q openvpn.zip && \
    sed -ri 's/.*(auth-user-pass).*/\1 auth/' *.ovpn

ADD init /usr/local/sbin/

ENTRYPOINT ["/usr/local/sbin/init"]
