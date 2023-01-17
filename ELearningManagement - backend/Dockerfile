FROM maven:3-openjdk-11-slim AS build

WORKDIR /app

COPY ./ /app

RUN mvn clean install -DskipTests

FROM openjdk:11-jdk-slim

COPY --from=build /app/target/*.jar app.jar
 
ENV PORT 8080
EXPOSE $PORT
ENTRYPOINT ["java","-jar","-Xmx1024M","-Dserver.port=${PORT}","app.jar"]
