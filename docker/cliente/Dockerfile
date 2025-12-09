FROM debian:13

RUN apt update  && apt install -y \
    procps \
    iproute2 \
    iputils-ping \
    bind9utils \
    dnsutils \
    tcpdump \
    ftp \
    ftp-ssl \
    && rm -rf /var/lib/apt/lists/*


CMD ["sleep", "infinity"]
