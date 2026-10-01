FROM maven:3.9-eclipse-temurin-17 AS build
WORKDIR /app
COPY pom.xml .
COPY auth-service/pom.xml auth-service/pom.xml
RUN mvn -q -pl auth-service -am dependency:go-offline
COPY auth-service/src auth-service/src
RUN mvn -q -pl auth-service -am package -DskipTests
FROM eclipse-temurin:17-jre
COPY --from=build /app/auth-service/target/auth-service-1.0.0.jar /app.jar
ENTRYPOINT ["java","-jar","/app.jar"]
