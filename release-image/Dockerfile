# hyperframeoe-wildfly : version : lastest
FROM openjdk:8
# ref ) https://hub.docker.com/_/openjdk
MAINTAINER MW 1-4 <seungwook_hwang@tmax.co.kr, hyolim_shin@tmax.co.kr>

# 1) LATEST WildFly Binary - tmax build wildfly
ENV WILDFLY_BINARY_FILE  wildfly-latest.tar.gz


ENV WILDFLY_BINARY_URL  https://github.com/TmaxSoftOfficial/HyperFrameOE-Wildfly/raw/master
#ENV WILDFLY_BINARY_URL  http://192.168.13.200/install/hyperframeOE/wildfly/ 

ENV JBOSS_HOME      /opt/jboss/wildfly


# 2) copy source (jdk, wildfly) to image
RUN wget ${WILDFLY_BINARY_URL}/$WILDFLY_BINARY_FILE -P $JBOSS_HOME/


# 3) extract binary unzip files, set symbolic links
RUN set -eux; \
    #wildfly binary
    cd $JBOSS_HOME; \
    tar -zxvf $WILDFLY_BINARY_FILE --strip-components=1; \
    rm -rf $WILDFLY_BINARY_FILE; \
    chmod -R g+rw ${JBOSS_HOME};
 
# Ensure signals are forwarded to the JVM process correctly for graceful shutdown
ENV LAUNCH_JBOSS_IN_BACKGROUND true

# Expose the ports we're interested in
EXPOSE 8080

# Set the default command to run on boot
# This will boot WildFly in the standalone mode and bind to all interface
CMD ["/opt/jboss/wildfly/bin/standalone.sh", "-b", "0.0.0.0"]

