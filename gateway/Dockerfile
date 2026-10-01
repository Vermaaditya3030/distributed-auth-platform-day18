FROM maven:3.9-eclipse-temurin-17 AS build
WORKDIR /app
COPY pom.xml .
COPY gateway/pom.xml gateway/pom.xml
RUN mvn -q -pl gateway -am dependency:go-offline
COPY gateway/src gateway/src
RUN mvn -q -pl gateway -am package -DskipTests
FROM eclipse-temurin:17-jre
COPY --from=build /app/gateway/target/gateway-1.0.0.jar /app.jar
ENTRYPOINT ["java","-jar","/app.jar"]
