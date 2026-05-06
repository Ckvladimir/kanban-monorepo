FROM maven:3.9.6-eclipse-temurin-8 AS build

WORKDIR /app

COPY pom.xml .
RUN mvn -B -q dependency:go-offline

COPY src ./src
RUN mvn -B -q package -DskipTests

FROM eclipse-temurin:8-jre

WORKDIR /app

ENV SERVER_PORT=8080

COPY --from=build /app/target/kanban-app-0.0.1-SNAPSHOT.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "app.jar"]
