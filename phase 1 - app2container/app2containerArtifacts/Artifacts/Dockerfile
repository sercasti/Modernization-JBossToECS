FROM registry.access.redhat.com/ubi8/ubi
MAINTAINER AWS
WORKDIR /
# Copying Entryfile
COPY entryfile /entryfile
# Adding and unpacking Tar file
COPY ContainerFiles.tar /
RUN tar xvfP /ContainerFiles.tar --directory / --skip-old-files --same-owner --ignore-failed-read && rm -rf /ContainerFiles.tar 
# Follow the below example to update files# COPY ["generic_config_file", "/root/app2container/java-jboss-56611d5f/Artifacts/generic_config_file"]# Adding advanced app mode installs
RUN yum install -y java-1.8.0-openjdk-devel 
# Environment Variables
ENV HOME /opt/wildfly
ENV JBOSS_HOME /opt/wildfly
ENV PATH /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin
ENV WILDFLY_BIND 0.0.0.0
ENV LANG en_US.UTF-8
ENV MALLOC_ARENA_MAX 1
ENV PWD /
ENV USER wildfly
ENV WILDFLY_MODE standalone
ENV _ /usr/bin/java
ENV INVOCATION_ID d3d77a2e24bb48fa8de6aa7547f3a67e
ENV LOGNAME wildfly
ENV SHLVL 2
ENV LAUNCH_JBOSS_IN_BACKGROUND 1
ENV WILDFLY_CONFIG standalone.xml
# Exposing ports
EXPOSE 8443
EXPOSE 8080
EXPOSE 9990
# User and user group 
RUN groupadd -f -r -g 990 wildfly
RUN id -u wildfly > /dev/null 2>&1 || useradd -r -g 990 -u 993 wildfly
USER wildfly:wildfly
WORKDIR /
# Image Entrypoint
CMD /entryfile
