# Build stage
FROM maven:3.5-jdk-8-alpine AS build
WORKDIR /gestion-commande
COPY pom.xml /
COPY src /src
RUN mvn -f /pom.xml clean install

# Run stage
FROM openjdk:8-jdk-alpine
COPY --from=build /target/gestion-commande.jar /gestion-commande.jar
EXPOSE 9002
ENTRYPOINT ["java", "-jar", "/gestion-commande.jar"]
