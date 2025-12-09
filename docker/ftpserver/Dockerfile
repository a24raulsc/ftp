FROM debian:13

RUN apt update  && apt install -y \
    procps \
    iproute2 \
    iputils-ping \
    vsftpd \
    dnsutils \
    rsyslog \
    passwd \
    ftp-ssl\
    && rm -rf /var/lib/apt/lists/*

# Crear usuarios con home e pass "a"
RUN for u in ana xan eva roi; do \
        useradd -m "$u" && \
        echo "$u:a" | chpasswd ; \
    done
RUN useradd -m -s /bin/bash gandalf  && echo "gandalf:abc123.." | chpasswd && \
    useradd -m -s /bin/bash saruman  && echo "saruman:abc123.." | chpasswd && \
    useradd -m -s /bin/bash aragorn  && echo "aragorn:abc123.." | chpasswd && \
    useradd -m -s /bin/bash frodo    && echo "frodo:abc123.."   | chpasswd

COPY entrypoint.sh /sbin
RUN chmod a+x /sbin/entrypoint.sh
RUN mkdir /etc/sauron
RUN chmod a+x /etc/sauron
RUN touch /var/log/ftp.log
RUN chmod 666 /var/log/ftp.log

RUN sed -i 's/^\s*module(load="imklog")/#module(load="imklog")/' /etc/rsyslog.conf

ENTRYPOINT ["/sbin/entrypoint.sh"]