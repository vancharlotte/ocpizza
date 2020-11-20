# Build stage
FROM maven:3.5-jdk-8-alpine AS build
WORKDIR /api-gateway
COPY pom.xml /
COPY src /src
RUN mvn -f /pom.xml clean install

# Run stage
FROM openjdk:8-jdk-alpine
COPY --from=build /target/api-gateway.jar /api-gateway.jar
EXPOSE 9004
ENTRYPOINT ["java", "-jar", "/api-gateway.jar"]
