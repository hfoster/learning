FROM ubuntu:latest

MAINTAINER Hartnell Foster <hartnell.foster@googlemail.com>

RUN apt-get update
RUN apt-get -y upgrade

# Install basic system tools
RUN apt-get install -y openssh-server
# Install Java
RUN apt-get install -y openjdk
# Install build tools
RUN apt-get install -y maven3 git
