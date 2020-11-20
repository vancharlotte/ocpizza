# Build stage
FROM maven:3.5-jdk-8-alpine AS build
WORKDIR /gestion-administrative
COPY pom.xml /
COPY src /src
RUN mvn -f /pom.xml clean install

# Run stage
FROM openjdk:8-jdk-alpine
COPY --from=build /target/gestion-administrative.jar /gestion-administrative.jar
EXPOSE 9003
ENTRYPOINT ["java", "-jar", "/gestion-administrative.jar"]
