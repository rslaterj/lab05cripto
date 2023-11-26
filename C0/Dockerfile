FROM ubuntu:12.10

RUN sed -i 's|archive.ubuntu.com|old-releases.ubuntu.com|g' /etc/apt/sources.list

RUN apt-get update
RUN apt-get install openssh-server openssh-client -y

RUN mkdir /var/run/sshd

RUN echo 'root:password' | chpasswd

RUN sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]