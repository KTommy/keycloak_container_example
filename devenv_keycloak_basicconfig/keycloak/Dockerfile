FROM jboss/keycloak:latest

RUN echo "now building keycloak ..."

ENV KEYCLOAK_USER=admin
ENV KEYCLOAK_PASSWORD=admin

ENTRYPOINT [ "/opt/jboss/tools/docker-entrypoint.sh" ]

COPY ./import/*.json /opt/jboss/import/

#############################################
# import setting

# when you want to import demo-realms/demousers
CMD ["-b", "0.0.0.0", "-Dkeycloak.migration.action=import", "-Dkeycloak.migration.provider=singleFile", "-Dkeycloak.migration.file=/opt/jboss/import/demorealm.json", "-Dkeycloak.migration.strategy=OVERWRITE_EXISTING" ]

# when you don't want to import demo-realms/demousers
# CMD ["-b", "0.0.0.0"]

#############################################
