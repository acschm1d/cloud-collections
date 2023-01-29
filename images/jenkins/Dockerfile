FROM --platform=linux/amd64 jenkins/jenkins:2.385-jdk11

LABEL org.opencontainers.image.source=https://github.com/acschm1d/cloud-collections

ENV JAVA_OPTS -Djenkins.install.runSetupWizard=false
ENV CASC_JENKINS_CONFIG /var/data/casc.yaml

COPY plugins.txt /usr/share/jenkins/ref/plugins.txt
COPY casc.yaml /var/data/casc.yaml

RUN jenkins-plugin-cli -f /usr/share/jenkins/ref/plugins.txt
