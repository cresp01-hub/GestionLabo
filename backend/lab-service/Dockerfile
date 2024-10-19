FROM openjdk:17-jdk-alpine
VOLUME /tmp
COPY target/lab-service-0.0.1-SNAPSHOT.jar lab-service.jar
ENTRYPOINT ["java","-jar","/lab-service.jar"]
