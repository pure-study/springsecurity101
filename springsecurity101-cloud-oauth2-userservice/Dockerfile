FROM openjdk:8-jre-alpine3.9
LABEL authors="Will"

ENTRYPOINT ["/usr/bin/java", "-jar", "/app/app.jar"]

EXPOSE 8080

ARG JAR_FILE=springsecurity101-cloud-oauth2-userservice-1.0.0.jar
COPY target/${JAR_FILE} /app/app.jar