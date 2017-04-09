FROM ubuntu:latest

MAINTAINER Hartnell Foster <hartnell.foster@googlemail.com>

# Grab the Jenkins repository and key
RUN wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
RUN deb https://pkg.jenkins.io/debian-stable binary/

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

# Install Jenkins
RUN apt-get install -y jenkins
# Enable and start Jenkins service
RUN systemctl enable jenkins
RUN systemctl start jenkins
# Webapp port
EXPOSE 8080
# Agent port
EXPOSE 5000
# SSH port
EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]
