FROM jenkins/jenkins:2.385-jdk11

LABEL org.opencontainers.image.source=https://github.com/acschm1d/cloud-collections

ENV JAVA_OPTS -Djenkins.install.runSetupWizard=false
ENV CASC_JENKINS_CONFIG /var/jenkins_home/casc.yaml

COPY plugins.txt /usr/share/jenkins/ref/plugins.txt
COPY casc.yaml /var/jenkins_home/casc.yaml

RUN jenkins-plugin-cli -f /usr/share/jenkins/ref/plugins.txt
