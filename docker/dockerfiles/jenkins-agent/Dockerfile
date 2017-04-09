FROM ubuntu:latest

MAINTAINER Hartnell Foster <hartnell.foster@googlemail.com>

RUN apt-get update
RUN apt-get -y upgrade

# Install SSH server
RUN apt-get install -y openssh-server
RUN sed -i 's|session    required     pam_loginuid.so|session    optional     pam_loginuid.so|g' /etc/pam.d/sshd
RUN mkdir -p /var/run/sshd
# Install Java
RUN apt-get install -y openjdk-8-jdk
# Install build tools
RUN apt-get install -y maven git

# Create Jenkins user
RUN adduser --quiet jenkins
RUN echo "jenkins:jenkins" | chpasswd
RUN mkdir -p /home/jenkins/.m2
RUN chown -R jenkins:jenkins /home/jenkins/.m2

# Standard SSH port
EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]
