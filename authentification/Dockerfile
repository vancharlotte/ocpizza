# Build stage
FROM maven:3.5-jdk-8-alpine AS build
WORKDIR /authentification
COPY pom.xml /
COPY src /src
RUN mvn -f /pom.xml clean install

# Run stage
FROM openjdk:8-jdk-alpine
COPY --from=build /target/authentification.jar /authentification.jar
EXPOSE 9001
ENTRYPOINT ["java", "-jar", "/authentification.jar"]
