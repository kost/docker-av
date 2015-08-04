FROM debian:latest
MAINTAINER kost, https://github.com/kost

# Install Requirements
RUN apt-get update && apt-get install -yq libc6-i386 wget && \
  wget -O- -q http://download.bitdefender.com/repos/deb/bd.key.asc | apt-key add - && \
  sh -c 'echo "deb http://download.bitdefender.com/repos/deb/ bitdefender non-free" >> /etc/apt/sources.list' && \
  apt-get update -qq &&  apt-get install -yq bitdefender-scanner && apt-get clean && rm -rf /var/lib/apt/lists/*

# Install Bitdefender
RUN cat /opt/BitDefender-scanner/etc/bdscan.conf > /opt/BitDefender-scanner/etc/bdscan.conf.bak && \
echo "LicenseAccepted = True" >> /opt/BitDefender-scanner/etc/bdscan.conf && \
bdscan --update && \
rm -rf /tmp/* /var/tmp/* && \
mkdir /work

VOLUME ["/work"]
WORKDIR /work

ENTRYPOINT ["bdscan"]

CMD ["--help"]
