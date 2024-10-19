FROM openjdk:17-jdk-alpine
VOLUME /tmp
COPY target/analysis-service-0.0.1-SNAPSHOT.jar analysis-service.jar
ENTRYPOINT ["java","-jar","/analysis-service.jar"]
