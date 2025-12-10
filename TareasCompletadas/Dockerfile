FROM maven:3.8.4-eclipse-temurin-17 AS build
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn clean package -DskipTests

FROM eclipse-temurin:17-jdk-jammy
WORKDIR /app
COPY --from=build /app/target/TareasCompletadas-1.0.0.jar app.jar
COPY tareas_completas.json ./
EXPOSE 8081
ENTRYPOINT ["java", "-jar", "app.jar"]
