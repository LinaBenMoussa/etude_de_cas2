# Étape 1 : Construire l'application Java
FROM maven:3.8.5-openjdk-11 AS build
# Répertoire de travail dans l'image
WORKDIR /app

COPY pom.xml .

RUN mvn dependency:go-offline -Dmaven.wagon.http.ssl.insecure=true -Dmaven.wagon.http.ssl.allowall=true

COPY src ./src

RUN mvn clean package -DskipTests

#stage2

FROM openjdk:11-jre-slim

WORKDIR /app

COPY --from=build /app/target/spring-boot-data-jpa-0.0.1-SNAPSHOT.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "app.jar"]

