FROM debian:latest

ENV TINI_VERSION="v0.10.0"

RUN apt update && apt install -y freeradius-ldap curl \
        && apt-get autoremove -y \
        && apt-get autoclean -y \
        && curl -L https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini > /usr/bin/tini \
        && chmod +x /usr/bin/tini

COPY ldap /etc/freeradius/3.0/mods-available/
COPY init /

RUN chmod +x /init
EXPOSE 1812/udp 1813/udp

ENTRYPOINT [ "/init" ]
