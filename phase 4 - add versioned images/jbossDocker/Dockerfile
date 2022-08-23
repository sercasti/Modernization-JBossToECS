FROM jboss/wildfly:latest





# Instead of adding the war files via file system with no versioning
# ADD numberguessDocker/target/numberguess.war /opt/jboss/wildfly/standalone/deployments/
# ADD helloworld-html5/target/helloworld-html5.war /opt/jboss/wildfly/standalone/deployments/


# We can copy files within versioned docker images from docker repo, 
# by doing this, we can deploy different versions of each artifact in the same jboss
COPY --from=numberguess:latest /opt/jboss/wildfly/standalone/deployments/numberguess.war /opt/jboss/wildfly/standalone/deployments/
#                   Notice version here
COPY --from=helloworld-html:develop /opt/jboss/wildfly/standalone/deployments/helloworld-html5.war /opt/jboss/wildfly/standalone/deployments/





COPY standalone.xml /opt/jboss/wildfly/standalone/configuration/

CMD ["/opt/jboss/wildfly/bin/standalone.sh", "-b", "0.0.0.0", "-bmanagement", "0.0.0.0"]

EXPOSE 8080 9990 8009
