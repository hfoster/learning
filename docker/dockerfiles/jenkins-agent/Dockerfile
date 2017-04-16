FROM ubuntu:latest

MAINTAINER Hartnell Foster <hartnell.foster@googlemail.com>

RUN apt-get update
RUN apt-get -y upgrade

# Install wget
RUN apt-get install -y wget
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
RUN mkdir -p /var/lib/jenkins/workspace

# Standard SSH port
EXPOSE 22

# Install and start the Jenkins swarm CLI tool
RUN wget -q https://repo.jenkins-ci.org/releases/org/jenkins-ci/plugins/swarm-client/3.4/swarm-client-3.4.jar -O /var/lib/swarm-client-3.4.jar
RUN java -jar /var/lib/swarm-client-3.4.jar -username jenkins -executors 10 -labels docker

CMD ["/usr/sbin/sshd", "-D"]
