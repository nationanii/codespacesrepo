FROM ubuntu:20.04

ENV DEBIAN_FRONTEND noninteractive
RUN echo 'root:root' | chpasswd
RUN printf '#!/bin/sh\nexit 0' > /usr/sbin/policy-rc.d
RUN apt update \
    && apt install -y rsyslog systemd init dbus-user-session systemd-cron dbus sudo wget curl nano software-properties-common net-tools apt-utils language-pack-vi language-pack-vi-base locales locales-all \
    # Fix a bug with common-debian script
    && rm -f /usr/local/bin/systemctl \
    #  Clean up
    && apt clean && rm -rf /var/lib/apt/lists/* 
RUN yes | unminimize
RUN locale-gen "vi_VN.UTF-8"
ENV LANG=vi_VN.UTF-8 \
    LANGUAGE=vi_VN:vi \
    LC_ALL=vi_VN.UTF-8
RUN printf "systemctl start systemd-logind" >> /etc/profile 

ENTRYPOINT ["/sbin/init"]
