FROM alpine:latest

LABEL maintainer="benko.richard86@gmail.com"

ENV VERSION="0.16.1"

WORKDIR /srv

RUN wget https://github.com/prometheus/snmp_exporter/releases/download/v${VERSION}/sha256sums.txt \
    https://github.com/prometheus/snmp_exporter/releases/download/v${VERSION}/snmp_exporter-${VERSION}.linux-amd64.tar.gz

RUN [ $(grep "snmp_exporter-${VERSION}.linux-amd64.tar.gz" sha256sums.txt | cut -f 1 -d " ") == $(sha256sum snmp_exporter-${VERSION}.linux-amd64.tar.gz | cut -f 1 -d " ") ] \
    && tar -xzf snmp_exporter-${VERSION}.linux-amd64.tar.gz \
    && rm -f snmp_exporter-${VERSION}.linux-amd64.tar.gz sha256sums.txt \
    && mv snmp_exporter-${VERSION}.linux-amd64 snmp_exporter \
    && chmod +x snmp_exporter/snmp_exporter

WORKDIR /srv/snmp_exporter

EXPOSE 9116

CMD [ "./snmp_exporter" ]