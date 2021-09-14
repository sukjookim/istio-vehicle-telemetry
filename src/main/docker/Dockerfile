FROM maven:3.5-jdk-8 as BUILD
COPY src /usr/src/myapp/src
COPY pom.xml /usr/src/myapp

RUN mvn -f /usr/src/myapp/pom.xml clean package -DskipTests

FROM openjdk:8u131-jre

COPY --from=BUILD /usr/src/myapp/target/telemetry-0.0.1-SNAPSHOT.jar webapp.jar

EXPOSE 8080

CMD ["java", "-Xmx50m", "-jar","webapp.jar"]
