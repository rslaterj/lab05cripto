FROM ubuntu:14.10

RUN sed -i 's|archive.ubuntu.com|old-releases.ubuntu.com|g' /etc/apt/sources.list
RUN sed -i 's|security.ubuntu.com|old-releases.ubuntu.com|g' /etc/apt/sources.list
RUN sed -i '/^# deb-src/s/^# //' /etc/apt/sources.list

RUN apt-get update
RUN apt-get install openssh-server openssh-client -y

RUN mkdir /var/run/sshd

RUN sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

RUN apt-get install dpkg-dev nano autoconf automake libtool zlib1g-dev libssl-dev --fix-missing -y
RUN apt-get source openssh-client


EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]