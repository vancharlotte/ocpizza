# Build stage
FROM maven:3.5-jdk-8-alpine AS build
WORKDIR /ui-client
COPY pom.xml /
COPY src /src
RUN mvn -f /pom.xml clean install

# Run stage
FROM openjdk:8-jdk-alpine
COPY --from=build /target/ui-client.jar /ui-client.jar
EXPOSE 8000
ENTRYPOINT ["java", "-jar", "/ui-client.jar"]
