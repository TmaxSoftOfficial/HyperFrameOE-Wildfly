# hyperframeoe-wildfly : version : latest
FROM hyperframeoe-wildfly
MAINTAINER MW 1-4 <seungwook_hwang@tmax.co.kr, hyolim_shin@tmax.co.kr>

WORKDIR $JBOSS_HOME

# copy user's configuration/apps to image
COPY ./configuration $JBOSS_HOME/standalone/configuration
COPY ./deployments $JBOSS_HOME/standalone/deployments




