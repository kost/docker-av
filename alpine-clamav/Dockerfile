FROM gliderlabs/alpine
MAINTAINER Vlatko Kosturjak kost@kost.im

RUN apk add --update clamav clamav-libunrar && \
cp /etc/clamav/freshclam.conf.sample /etc/clamav/freshclam.conf && \
freshclam -v && \
mkdir /work

VOLUME ["/work"]
WORKDIR /work

ENTRYPOINT ["clamscan"]
CMD ["-h"]

