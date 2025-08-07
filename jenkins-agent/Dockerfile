FROM ubuntu:22.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y \
    openjdk-17-jdk \
    git \
    curl \
    wget \
    unzip \
    sudo \
    openssh-client \
    && rm -rf /var/lib/apt/lists/*

RUN curl -fsSL https://get.docker.com | sh

RUN useradd -m -s /bin/bash jenkins

ENV JENKINS_AGENT_HOME=/home/jenkins
ENV AGENT_WORKDIR=/home/jenkins/agent
ENV JENKINS_URL=http://jenkins-master:8080

WORKDIR ${AGENT_WORKDIR}
RUN mkdir -p ${AGENT_WORKDIR}
RUN chown -R jenkins:jenkins ${JENKINS_AGENT_HOME}

COPY entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh

USER jenkins
ENTRYPOINT ["/entrypoint.sh"]
