FROM alpine:3.8
LABEL maintainer "Steven Leong <steven@aisstech.com>"
LABEL branch "master"

COPY Dockerfile /Dockerfile
COPY .bashrc /root/.bashrc

RUN apk --update -t add keepalived iproute2 grep bash tcpdump sed && \
    rm -f /var/cache/apk/* /tmp/* && \
    rm -f /sbin/halt /sbin/poweroff /sbin/reboot

COPY keepalived.sh /usr/bin/keepalived.sh
COPY keepalived.conf /etc/keepalived/keepalived.conf

RUN chmod +x /usr/bin/keepalived.sh; chown root:root /usr/bin/keepalived.sh

ENTRYPOINT ["/usr/bin/keepalived.sh"]