FROM nautsch/oracle-jdk:8
MAINTAINER Oliver Nautsch <oliver.nautsch@nautsch.com>

RUN apt-get update
RUN apt-get -y upgrade

RUN apt-get install -y openssh-server
RUN sed -i 's|session    required     pam_loginuid.so|session    optional     pam_loginuid.so|g' /etc/pam.d/sshd
RUN mkdir -p /var/run/sshd

RUN adduser --quiet jenkins
RUN echo "jenkins:jenkins" | chpasswd

# Standard SSH port
EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]